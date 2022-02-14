---
title: Hugoの設定
weight: 1
---

# 設定


## 基本設定
### KaTexなどのマークアップを有効にする

    [markup.goldmark.renderer]
      unsafe = true

## GitHub Actions を使って GitHub Pages に公開する設定
### キーの作成
deploy key(秘密鍵) と secret(公開鍵)を登録する。

https://www.morling.dev/blog/automatically-deploying-hugo-website-via-github-actions/


### 空の .nojekyll を作成する
git push してgithub側で build される際、「Deploy to GitHub Pages」の段階で次のエラーが出るため、空の .nojekyll を作成しておく。

```
Error: Error: No uploaded artifact was found! Please check if there are any errors at build step.
```

    touch .nojekyll

https://stackoverflow.com/questions/70830152/page-on-github-wont-publish-error-404-not-found


### gh-pages-deployment.yml  
ここを参考にGitHub Actionの設定ファイル gh-pages-deployment.yml を作成する。
https://gohugo.io/hosting-and-deployment/hosting-on-github/#build-hugo-with-github-action

以下の例では、

```# extended: true```

のコメントアウトをはずし、
```if: github.ref == 'refs/heads/main'```
を削除し、branch を masterにしてある。

.github/workflows/gh-pages-deployment.yml

    name: github pages

    on:
    push:
        branches:
        - master  # Set a branch to deploy
    pull_request:

    jobs:
    deploy:
        runs-on: ubuntu-20.04
        steps:
        - uses: actions/checkout@v2
            with:
            submodules: true  # Fetch Hugo themes (true OR recursive)
            fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod

        - name: Setup Hugo
            uses: peaceiris/actions-hugo@v2
            with:
            hugo-version: 'latest'
            extended: true

        - name: Build
            run: hugo --minify

        - name: Deploy
            uses: peaceiris/actions-gh-pages@v3
            with:
            github_token: ${{ secrets.GITHUB_TOKEN }}
            publish_dir: ./public

