---
layout: post
title: Jekyll On Windows 从本地搭建到github部署
category: jekyll
description: 
---

【持续更新中...】记一次搭建属于自己博客的步骤(本地os为win7 64bits)，仅供参考。


## 要求
1. Open Git Bash

2. Check whether you have Ruby installed

	```
	$ ruby --version
	ruby 2.6.3p62 (2019-04-16 revision 67580) [x64-mingw32]
	```

3. If you don't have Ruby installed, [install Ruby](https://rubyinstaller.org/downloads/)

4. Install Bundler

	```
	$ gem install bundler
	```

## 最简易的本地Jekyll site搭建
### Step 1: Create a local repository for your Jekyll site

1. Open Git Bash

2. On your local computer, initialize a new Git repository for your Jekyll site

	``` 
	$ git init JEKYLL-SITE-REPOSITORY-NAME
	```

3. Change directories to the new repository you created

	``` 
	$ cd JEKYLL-SITE-REPOSITORY-NAME
	```


### Step 2: Install Ruby Dependencies 

1. Create the file Gemfile under the root directory of your local Jekyll site repository， save it 

	```
	source 'https://rubygems.org'
	if RUBY_PLATFORM=~ /win32|mingw|mswin|x64_mingw/ 
		gem 'tzinfo-data'
		gem 'wdm'
	end
	gem 'github-pages', group: :jekyll_plugins
	```

2. Install Jekyll and other dependencies from the GitHub Pages gem

	```
	$ bundle install
	```


### Step 3: Build your local Jekyll site
1. Navigate into the root directory of your local Jekyll site repository

2. Run your Jekyll site locally

	```
	$ bundle exec jekyll serve
	```

3. Preview your local Jekyll site in your web browser at http://localhost:4000

## 添加主题模板

在以上简易站点基础下，添加已有博客模板中相应的文件(夹)即可。自己结合了以下两个进行添加

- [https://github.com/comsince/comsince.github.io](https://github.com/comsince/comsince.github.io)
- [https://github.com/mzlogin/mzlogin.github.io](https://github.com/mzlogin/mzlogin.github.io)

 其他模板也可参考
- [https://github.com/qiubaiying/qiubaiying.github.io](https://github.com/qiubaiying/qiubaiying.github.io)
- [https://dongchuan.github.io/](https://dongchuan.github.io/)
- [http://ywtail.github.io](http://ywtail.github.io) 
- [https://github.com/EdisonXu/EdisonXu.github.io](https://github.com/EdisonXu/EdisonXu.github.io)

[目录结构说明](https://www.jianshu.com/p/50d97f32e558)
```
_config.yml  保存配置数据
_drafts      未发布的文章
assets       辅助资源，css布局/js脚本/图片等
_pages       其他需要生成的网页，如About页	
_includes    包含部分文章的布局，通过include标签将其中文件包含进来
_layouts     包裹在文章外部的模板，可以在YAML头信息中根据不同文章进行选择，标签{{  content  }}可以将content插入页面中
_posts       发布的文章，文件标题必须符合：`YEAR-MONTH-DAY-TITLE.MARKUP`
_data        站点数据，可用过`site.data.members`访问其中的数据 (the jekyll engine will autoload all yaml file`members.yml`under the directory)
_site        jekyll引擎转换生成的页面，最好将这个目录放进`.gitignore`文件中
```


## 评论插件

* [为博客添加 Gitalk 评论插件](https://www.jianshu.com/p/78c64d07124d)
* [解决配置gitalk插件后初始化登录时跳转回首页](https://blog.csdn.net/w47_csdn/article/details/88858343)

## 待完善

- [ ] 自动初始化gitalk评论 


## 参考资料

* [Setting up your GitHub Pages site locally with Jekyll](https://help.github.com/en/articles/setting-up-your-github-pages-site-locally-with-jekyll)
* [Jekyll中国](http://jekyllcn.com/)
* [Jekyll目录结构和运行机理	](https://blog.csdn.net/HopefulLight/article/details/78366374)