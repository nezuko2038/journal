---
layout: post
category: Markup
tags: [asciidoc]
description: AsciidocFXをご紹介します。
revdate:  2019-04-12  01:52 +0900
---
# AsciidocFX



## AsciidocFXとは
- Java製のasciidocエディタ
- https://asciidocfx.com/

## 設定
色々と既知の問題があるので、まずはこちらを確認しましょう。
https://github.com/asciidocfx/AsciidocFX/blob/master/index.adoc#known-issues

### 文字のにじみをなくす

AsciidocFXはJavaFXを用いて開発されたもので、JavaFXはデフォルトでLCD用にアンチエイリアスをかけるため、
文字が滲んだように感じることがあります。
滲みをなくすためには、AsciidocFX起動時に
 `-Dprism.lcdtext=false` オプションを追加します。



```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
  <plist version="1.0">
  <dict>
  <key>Label</key>
  <string>setenv.JAVA_TOOL_OPTIONS</string>
  <key>ProgramArguments</key>
  <array>
    <string>/bin/launchctl</string>
    <string>setenv</string>
    <string>JAVA_TOOL_OPTIONS</string>
    <string>-Dprism.lcdtext=false </string>
  </array>
  <key>RunAtLoad</key>
  <true/>
  <key>ServiceIPC</key>
  <false/>
</dict>
</plist>
```

### 文字が\#### で表示される場合

Known IssueにはMicrosoft Core Fontが必要と書かれていますが、
FOPは中国語の斜体太字はサポートしていないらしいです。
https://github.com/asciidocfx/AsciidocFX/issues/287



 
./Applications/AsciidocFX/conf\/ocbook-config/fo-pdf.xsl
```xml
<xsl:attribute-set name="section.title.level6.properties">
    <xsl:attribute name="font-size">12pt</xsl:attribute>
    <!-- <xsl:attribute name="font-style">italic</xsl:attribute> -->
    <xsl:attribute name="font-weight">bold</xsl:attribute>
</xsl:attribute-set>
```

### ページサイズの変更


https://github.com/asciidocfx/AsciidocFX/issues/291



./Applications/AsciidocFX/conf\/ocbook-config/fo-pdf.xsl
```xml
<xsl:param name="page.height.portrait">29.7cm</xsl:param>
<xsl:param name="page.width.portrait">21.0cm</xsl:param>
```
