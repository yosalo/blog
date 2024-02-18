---
layout: post
title: rvm install ruby on macOS
tag: macos
comments: true
keywords: macOS, rvm, ruby
description: rvm install ruby on macOS
---

## Install rvm

```bash
brew install rvm
```

## Install ruby

```bash
rvm install ruby-3.3.0 --with-openssl-dir='brew --prefix openssl'
```

```bash
rvm reinstall 3.3.0 --with-openssl-dir=`brew --prefix openssl`
```

```bash
sudo gem install rails
gem update --system
```
