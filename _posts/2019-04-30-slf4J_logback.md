---
layout: post
category: Java
tags:  [ slf4j, logback ]
revdate:  2019-05-01  00:28 +0900
---


## SLF4Jとは

* The Simple Logging Facade for Java
* https://www.slf4j.org/

Facadeとは、GoFのデザインパターンに出てくるFacadeパターンのことで、
ユーザにインターフェースを提供しつつ実装の詳細を隠すパターンのことです。
SLF4Jは、ログの実装(Log4Jであったり、logbackであったり)を隠すためのライブラリになります。

## logbackとは
- log4j の創始者であるCekiGülcü によって設計されたLog4Jの後継プロジェクト
- http://logback.qos.ch/


## ビルドパスの設定
###  Mavenプロジェクトの場合

https://mvnrepository.com を参照して、
[slf4j-api](https://mvnrepository.com/artifact/org.slf4j/slf4j-api)と 
[logback-classic](https://mvnrepository.com/artifact/ch.qos.logback/logback-classic)をビルドパスへ追加します。

2019-04-30時点のバージョンを使用すると下記のようになります。

```pom.xml 
	<dependencies>
		<dependency>
			<groupId>org.slf4j</groupId>
			<artifactId>slf4j-api</artifactId>
			<version>1.7.26</version>
		</dependency>
		<dependency>
			<groupId>ch.qos.logback</groupId>
			<artifactId>logback-classic</artifactId>
			<version>1.2.3</version>
			<scope>test</scope>
		</dependency>

	</dependencies>
```





### code


```java 
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class Slf4jSample {

	public static void main(String[] args) {

		Logger logger = LoggerFactory.getLogger(Slf4jSample.class);
		logger.trace("trace");
		logger.debug("debug");
		logger.info("info");
		logger.warn("warn");
		logger.error("error");
	}

}
```