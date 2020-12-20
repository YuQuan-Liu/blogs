---
title: "利用Jekyll & Github pages搭建自己的博客"
tags:
  - Jekyll
toc: true
---

## 一、安装Jekyll (Mac)

参考：
- [jekyll官网](https://jekyllrb.com/)
- [Jekyll on macOS](https://jekyllrb.com/docs/installation/macos/)
- [Github+Jekyll 搭建个人网站详细教程](https://www.jianshu.com/p/9f71e260925d)

目的很简单，就是搭一个可以写blog的地方，按照文档的步骤做。

### 1. 安装xcode

```
xcode-select --install 
```

> Note：在自己的机器上安装之后还是会报错，在app store中安装了xcode后OK了。
>
> 自己的mac版本是 Big Sur 11.1

### 2. Install Ruby

```
ruby -v

ruby 2.6.3p62 (2019-04-16 revision 67580) [universal.x86_64-darwin20]
```

### 3. Install Jekyll

```
gem install --user-install bundler jekyll

# If you're using Zsh
echo 'export PATH="$HOME/.gem/ruby/2.6.0/bin:$PATH"' >> ~/.zshrc

gem env
```

### 4. 创建一个简单的Jekyll site 测试一下

参考：
- [Jekyll Quickstart](https://jekyllrb.com/docs/#instructions)

```
## 在./myblog中创建新的jekyll site。
jekyll new myblog

## 进入myblog
cd myblog

## 构建 并在本地启动
bundle exec jekyll serve

## 在浏览器中访问 http://localhost:4000 验证。

```

### 5. 选择一个自己喜欢的Jekyll Themes

参考：
- [Free Jekyll Themes](https://jekyllthemes.io/free)
- [https://github.com/mmistakes/minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)

> 我自己选择的是 [Minimal Mistakes Jekyll theme](https://jekyllthemes.io/theme/minimal-mistakes)

5.1 将minimal-mistakes fork到自己的账号下

5.2 将自己账号下的minimal-mistakes clone到本地，创建一个分支进行修改。

## 二、修改Minimal Mistakes Jekyll theme


### 1. 参考Minimal Mistakes Quick-Start Guide 自己本地仓库的新分支

参考：
- [Remote theme method](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#remote-theme-method)

### 2 修改 Gemfile

```
source "https://rubygems.org"

gem "github-pages", group: :jekyll_plugins
gem "jekyll-include-cache", group: :jekyll_plugins

group :jekyll_plugins do
  gem "jekyll-archives"
end

```

### 3 修改 _config.yml

```
# theme                  : "minimal-mistakes-jekyll"
# remote_theme           : "mmistakes/minimal-mistakes"
remote_theme: "mmistakes/minimal-mistakes@4.21.0" 
```

> 参考 [Minimal Mistakes Configuration](https://mmistakes.github.io/minimal-mistakes/docs/configuration/) 修改自己相关的配置信息【主题、皮肤、描述、作者】。

### 4 使用bundle 拉去更新bundled gems

```
bundle
```

### 5 删除不必要的文件

- .editorconfig
- .gitattributes
- .github
- /docs
- /test
- CHANGELOG.md
- minimal-mistakes-jekyll.gemspec
- README.md
- screenshot-layouts.png
- screenshot.png

> 注意：将your-site/docs/_pages 复制到 your-site/_pages一份。

### 6 修改导航链接。

_data/navigation.yml
```
# main links
main:
  #- title: "Quick-Start Guide"
  #  url: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/
  # - title: "About"
  #   url: /about/
  - title: "标签"
    url: /tags/
  - title: "归档"
    url: /year-archive/
  # - title: "分类"
  #   url: /categories/
  # - title: "Sitemap"
  #   url: /sitemap/

```

### 7 写个Post测试一下。
参考:
- [Working with Posts](https://mmistakes.github.io/minimal-mistakes/docs/posts/)

在your-site/_posts 目录中新建一个2020-12-19-test.md 的文件

```

---
title: "利用Jekyll & Github pages搭建自己的博客"
categories:
  - test
tags:
  - test
toc: true
---

### Test

#### 测试测试一下。
```

> 如果帖子开头有说明categories，本地生成的site中会在post前面添加一个categories对应的目录。本地启动后可以在_site目录下查看。
>
> 如果自己的帖子有照片，将存放照片的目录img存放到your-site/img下，post中使用相对路径引用，如果post指定了categories，会报找不到图片。

### 8 本地启动，验证一下。[http://127.0.0.1:4000/](http://127.0.0.1:4000/)

```
bundle exec jekyll serve
```


## 三、书写Posts，提交，推送到自己的Github仓库中。


Enjoy. 

坚持！
