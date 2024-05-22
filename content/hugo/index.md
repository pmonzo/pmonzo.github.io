---
title: 'Hugo'
date: 2024-05-19T21:43:39+02:00
draft: false
featured_image: ''
tags: [hugo, go, blog]
menu:
  main: 
    weight: 1
---

Hugo is a static site generator written in Go, optimized for speed and designed for flexibility. With its advanced templating system and fast asset pipelines, Hugo renders a complete site in seconds, often less.

Due to its flexible framework, multilingual support, and powerful taxonomy system, Hugo is widely used to create:

- Corporate, government, nonprofit, education, news, event, and project sites
- Documentation sites
- Image portfolios
- Landing pages
- Business, professional, and personal blogs
- Resumes and CVs

Use Hugo's embedded web server during development to instantly see changes to content, structure, behavior, and presentation. Then deploy the site to your host, or push changes to your Git provider for automated builds and deployment.

Hugo's fast asset pipelines include:

- CSS bundling – transpilation (Sass), tree shaking, minification, source maps, SRI hashing, and PostCSS integration
- JavaScript bundling – transpilation (TypeScript, JSX), tree shaking, minification, source maps, and SRI hashing
- Image processing – convert, resize, crop, rotate, adjust colors, apply filters, overlay text and images, and extract EXIF data

And with Hugo Modules, you can share content, assets, data, translations, themes, templates, and configuration with other projects via public or private Git repositories.

[Hugo website](https://github.com/gohugoio/hugo)

# Installation

## Install go

Remove any previous Go installation by deleting the /usr/local/go folder (if it exists), then extract the archive you just downloaded into /usr/local, creating a fresh Go tree in /usr/local/go: 

```
sudo rm -rf /usr/local/go && sudo tar -C /usr/local -xzf go1.22.3.linux-amd64.tar.gz
```

We must add golang path before using go command.

```
echo "export PATH=\$PATH:/usr/local/go/bin" | sudo tee /etc/profile.d/golang.sh
```

## Install hugo

In order to use the transpiler for sass to css we need to install the extended version of hugo.

```
CGO_ENABLED=1 go install -tags extended github.com/gohugoio/hugo@latest
```

Before using Hugo we must add local go binaries to PATH.

```
echo -e "export GOPATH=\$HOME/go\nexport PATH=\$PATH:\$GOPATH/bin" >> ~/.bashr
```

To compile themes we must install dart-sass. On linux it can be installed with snap.

```
sudo snap install dart-sass
```

## Create a new site

```
hugo new site pmonzo.github.io
cd pmonzo.github.io
```

Initialize git repository and add a new theme

```
git init
git add remote origin git@github.com:pmonzo/pmonzo.github.io.git
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
echo "theme = 'ananke'" >> hugo.toml
```

Finally we can start our server with -D option for development purposes

```
hugo server -D
```
