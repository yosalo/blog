---
layout: post
title: Jekyll build error
tag: jekyll
comments: true
---

# About error on jekyll build
<br>
```bash
/usr/local/lib/ruby/gems/2.3.0/gems/bundler-1.13.6/lib/bundler/definition.rb:179:in `rescue in specs': Your bundle is locked to minitest (5.8.3), but that version could not be found in any of the sources listed in your Gemfile. If you haven't changed sources, that means the author of minitest (5.8.3) has removed it. You'll need to update your bundle to a different version of minitest (5.8.3) that hasn't been removed in order to install. (Bundler::GemNotFound)
	from /usr/local/lib/ruby/gems/2.3.0/gems/bundler-1.13.6/lib/bundler/definition.rb:173:in `specs'
	from /usr/local/lib/ruby/gems/2.3.0/gems/bundler-1.13.6/lib/bundler/definition.rb:233:in `specs_for'
	from /usr/local/lib/ruby/gems/2.3.0/gems/bundler-1.13.6/lib/bundler/definition.rb:222:in `requested_specs'
	from /usr/local/lib/ruby/gems/2.3.0/gems/bundler-1.13.6/lib/bundler/runtime.rb:118:in `block in definition_method'
	from /usr/local/lib/ruby/gems/2.3.0/gems/bundler-1.13.6/lib/bundler/runtime.rb:19:in `setup'
	from /usr/local/lib/ruby/gems/2.3.0/gems/bundler-1.13.6/lib/bundler.rb:99:in `setup'
	from /usr/local/lib/ruby/gems/2.3.0/gems/jekyll-3.3.1/lib/jekyll/plugin_manager.rb:36:in `require_from_bundler'
	from /usr/local/lib/ruby/gems/2.3.0/gems/jekyll-3.3.1/exe/jekyll:9:in `<top (required)>'
	from /usr/local/bin/jekyll:19:in `load'
	from /usr/local/bin/jekyll:19:in `<main>'
	from /usr/local/bin/ruby_executable_hooks:15:in `eval'
	from /usr/local/bin/ruby_executable_hooks:15:in `<main>'
```
<br>
这个问题是因为bundle版本过低的问题,在终端直接运行以下命令即可
```bash
bundle update
```