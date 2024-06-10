+++
title = 'Hugo Quick Start'
date = 2024-06-10T18:00:32+07:00
+++


# Quickstart

Generating new site use `hugo` command
```shell
hugo new site <nama situs atau folder>
```
Nanti akan generate folder dengan nama situs serta file yang dibutuhkan

Open your website folder that have created
```shell
cd <folder nama situs>
```
Masuk ke folder yang sudah dibuat

Git command for initiate
```shell
git init
```
Inisialisasi git

Install hugo theme using `git submodule add` space `themes/folder_name`
```shell
git submodule add <hugo theme link dari github> themes/<nama folder tema>
```
Install tema hugo

```shell
echo "theme = '<nama tema hugo>'"  >> hugo.toml
```
Menambah text ke theme = 'x' ke /hugo.toml

```
hugo server
```
Menyalakan server 


lanjutan versi youtube
```shell
hugo new content posts/hello-world.md
```

kemudian edit .md dengan gaya markdown

Run hugo server. Then copy link or IP address into browser
```shell
hugo server --buildDrafts
```

# Change themes

```shell
git submodule --depth=1 <link github> themes/<nama folder>
git submodule update --init --recursive
```

then
```shell
git submodule update --remote --merge 
```
this will measure everything is oke

then edit hugo.yoml theme again
```shell
theme = '<nama theme>'
```

Save and happy



# Deploy at github.io

Create Repository Public that have end line xxxx.github.io
Push an existing repo from command line
```shell
git remote add origin <github link>

# membuat branch main
git branch -M main 

# upload existing repo ke branch main
git push -u origin main
```

Your site will 404, we need ->
repo setting -> pages -> source -> github action
create folder .github on my repo
create file hugo.yaml

```shell
# Sample workflow for building and deploying a Hugo site to GitHub Pages
name: Deploy Hugo site to Pages
on:
  # Runs on pushes targeting the default branch
  push:
    branches:
      - main

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# Sets permissions of the GITHUB_TOKEN to allow deployment to GitHub Pages
permissions:
  contents: read
  pages: write
  id-token: write

# Allow only one concurrent deployment, skipping runs queued between the run in-progress and latest queued.

# However, do NOT cancel in-progress runs as we want to allow these production deployments to complete.
concurrency:
  group: "pages"
  cancel-in-progress: false

# Default to bash
defaults:
  run:
    shell: bash

jobs:
  # Build job
  build:
    runs-on: ubuntu-latest
    env:
      HUGO_VERSION: 0.123.0
    steps:
      - name: Install Hugo CLI
        run: |
          wget -O ${{ runner.temp }}/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb \
          && sudo dpkg -i ${{ runner.temp }}/hugo.deb          
      - name: Install Dart Sass
        run: sudo snap install dart-sass
      - name: Checkout
        uses: actions/checkout@v4
        with:
          submodules: recursive
          fetch-depth: 0
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v4
      - name: Install Node.js dependencies
        run: "[[ -f package-lock.json || -f npm-shrinkwrap.json ]] && npm ci || true"
      - name: Build with Hugo
        env:
          # For maximum backward compatibility with Hugo modules
          HUGO_ENVIRONMENT: production
          HUGO_ENV: production
        run: |
          hugo \
            --gc \
            --minify \
            --baseURL "${{ steps.pages.outputs.base_url }}/"          
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v2
        with:
          path: ./public

  # Deployment job
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v3
```

then push
```shell
git add .
git commit -m "github action"
git push
```

if content / posts doesnt showing, delete draft in xxxx.md header
then 
```shell
git add .
git commit -m "publishing posts"
git push
```