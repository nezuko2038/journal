---
layout: post
category: Jekyll 
tags:  [jekyll, asciidoc ]
revdate:  2019-04-27  14:33 +0900
---


## jekyll-asciidocとは

* 静的サイトジェネレータ jekyll のプラグイン
* asciidocファイルをhtml変換します。
* https://github.com/asciidoctor/jekyll-asciidoc
* https://www.rubydoc.info/gems/jekyll-asciidoc/


## インストール


```Gemfile
group :jekyll_plugins do
  gem 'jekyll-asciidoc'
end
```

その後 `bundle` コマンドを実行します。

## 設定方法

### ascciidocプラグインの有効化

[source,yml]
```config.yml
plugins:
- jekyll-asciidoc
```

### その他の設定
```yml
asciidoc: {}
asciidoctor:
  base_dir: :docdir
  safe: unsafe
  attributes:
    - sectnumlevels=5
    - idseparator=_
    - source-highlighter=coderay
    - coderay-linenums-mode=table
    - source-linenums-option
    - icons=font
    - imagesdir=/journal/images

```

