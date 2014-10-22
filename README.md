Android-Studio-Guide
====================
方便他人，方便自己，省的到处搜索；
现在将android studio使用手册，收录集成，可能会在使用中，逐步更新；
翻译：Android Studio 中文组（大锤译）


[Gradle使用手册（一）：为什么要用Gradle？](#gradle1)

[Gradle使用手册（二）：项目结构](#gradle2)

[Gradle使用手册（三）：构建任务](#gradle3)

<a name="gradle1"/>

##Gradle使用手册（一）：为什么要用Gradle?

为什么要用Gradle？

Gradle是比较先进的构建系统，也是一个很好的构建工具，允许通过插件自定义构建逻辑

以下是为什么Android Studio选择Gradle的主要原因：

        使用领域专用语言（Domain Specific Language）来描述和处理构建逻辑。（以下简称DSL）
        基于Groovy。DSL可以混合各种声明元素，用代码操控这些DSL元素达到逻辑自定义。
        支持已有的Maven或者Ivy仓库基础建设
        非常灵活，允许使用best practices，并不强制让你遵照它的原则来。
        其它插件时可以暴露自己的DSL和API来让Gradle构建文件使用。
        允许IDE集成，是很好的API工具

<a name="gradle2"/>

##Gradle使用手册（二）：项目结构

<a name="gradle3"/>

##Gradle使用手册（三）：构建任务
