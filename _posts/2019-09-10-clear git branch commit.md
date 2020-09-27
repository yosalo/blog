---
layout: post
title: clear git branch commit
tag: git
comments: true
description: clear git branch commit
---

{% highlight shell %}
git checkout --orphan latest_branch

git add -A

git commit -am "commit message"

git branch -D master

git branch -m master

git push -f origin master
{% endhighlight %}