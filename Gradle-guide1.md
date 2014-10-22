为什么要用Gradle？

Gradle是比较先进的构建系统，也是一个很好的构建工具，允许通过插件自定义构建逻辑

以下是为什么Android Studio选择Gradle的主要原因：

        使用领域专用语言（Domain Specific Language）来描述和处理构建逻辑。（以下简称DSL）
        基于Groovy。DSL可以混合各种声明元素，用代码操控这些DSL元素达到逻辑自定义。
        支持已有的Maven或者Ivy仓库基础建设
        非常灵活，允许使用best practices，并不强制让你遵照它的原则来。
        其它插件时可以暴露自己的DSL和API来让Gradle构建文件使用。
        允许IDE集成，是很好的API工具

需要准备：

       Gradle 1.6 or 1.7
       SDK with Build Tools 17.0.0 (released 5/16/2013)
Basic Project

      在Gradle项目的根目录下，有个叫build.gradle的文件，它描述了这个项目的整体构建基础。

build文件 

      最基本的java程序，它的build.gradle文件就一句话：

apply plugin: 'java'
 

最基本的Android项目，它的build.gradle如下：

buildscript {
    repositories {
          mavenCentral()
     }

    dependencies {
          classpath 'com.android.tools.build:gradle:0.5.6'
     }
}

apply plugin: 'android'
android {
       compileSdkVersion 17
}

 
我们一步步来分析一下上面三部分的内容。

buildscript{...} 配置了驱动build的代码，它声明将在Maven中央仓库，取一个classpath dependency，也就是Android plugin for Gradle v0.5.6
apply plugin     指明了用到的plugin是android，就像前面java程序中，用的plugin是java一样
android{...}     中配置了所有android构建的参数，这里也就是Android DSL的入口点。
 

默认的，只有目标编译环境是必要的，也就是compileSdkVersion这个属性。这和以前在project.properties中的target属性类似。

值得注意的是，如果你在Android项目中写 apply plugin:java 而不是apply plugin:android的话，将会build失败。
