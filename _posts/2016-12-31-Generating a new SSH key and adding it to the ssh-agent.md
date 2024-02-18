---
layout: post
title: Generating a new SSH key and adding it to the ssh-agent
tag: git
comments: true
---

# add to ssh-agent
```bash
#打开终端
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

Generating public/private rsa key pair.

Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [这里填入你生成rsa的路径]

Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]

#Adding your SSH key to the ssh-agent
eval "$(ssh-agent -s)"

#这里的id_rsa是你生成
ssh-add ~/.ssh/id_rsa

#因为这个是往session里面添加key,所以当机器重启的的时候，需要重新再次往ssh-agent里面添加key
```