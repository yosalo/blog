---
layout: post
title: macOS brew install consul
tag: macos
comments: true
keywords: macOS, brew, consul
description: brew install consul on macOS
---


## 安装Consul

  ```bash
  brew install consul
  ```

## 配置Consul启动项

  ```bash
  vim /usr/local/opt/consul/homebrew.mxcl.consul.plist
  ```

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
        <key>KeepAlive</key>
        <dict>
        <key>SuccessfulExit</key>
        <false/>
        </dict>
        <key>Label</key>
        <string>homebrew.mxcl.consul</string>
        <key>ProgramArguments</key>
        <array>
        <string>/usr/local/opt/consul/bin/consul</string>
        <string>agent</string>
        <string>-server</string>
        <string>-bind</string>
        <string>127.0.0.1</string>
        <string>-data-dir</string>
        <string>./data</string>
        <string>-ui</string>
        </array>
        <key>RunAtLoad</key>
        <true/>
        <key>WorkingDirectory</key>
        <string>/usr/local/var</string>
        <key>StandardErrorPath</key>
        <string>/usr/local/var/log/consul.log</string>
        <key>StandardOutPath</key>
        <string>/usr/local/var/log/consul.log</string>
    </dict>
    </plist>
  ```

## 重启Consul

  ```bash
  brew services restart consul
  ```