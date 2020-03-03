## Intellij IDEA配置优化最佳实践



* [Intellij IDEA配置优化最佳实践](#intellij-idea%E9%85%8D%E7%BD%AE%E4%BC%98%E5%8C%96%E6%9C%80%E4%BD%B3%E5%AE%9E%E8%B7%B5)
  * [一、 介绍](#%E4%B8%80-%E4%BB%8B%E7%BB%8D)
  * [二、 用法](#%E4%BA%8C-%E7%94%A8%E6%B3%95)
  * [三、  编辑器优化说明](#%E4%B8%89--%E7%BC%96%E8%BE%91%E5%99%A8%E4%BC%98%E5%8C%96%E8%AF%B4%E6%98%8E)
    * [背景色和字体](#%E8%83%8C%E6%99%AF%E8%89%B2%E5%92%8C%E5%AD%97%E4%BD%93)
    * [行注释](#%E8%A1%8C%E6%B3%A8%E9%87%8A)
    * [热部署](#%E7%83%AD%E9%83%A8%E7%BD%B2)
    * [键盘映射](#%E9%94%AE%E7%9B%98%E6%98%A0%E5%B0%84)
    * [自动导包](#%E8%87%AA%E5%8A%A8%E5%AF%BC%E5%8C%85)
    * [性能优化](#%E6%80%A7%E8%83%BD%E4%BC%98%E5%8C%96)
    * [代码提示](#%E4%BB%A3%E7%A0%81%E6%8F%90%E7%A4%BA)
    * [字符编码](#%E5%AD%97%E7%AC%A6%E7%BC%96%E7%A0%81)
  * [四、 方法注释和类注释模板说明](#%E5%9B%9B-%E6%96%B9%E6%B3%95%E6%B3%A8%E9%87%8A%E5%92%8C%E7%B1%BB%E6%B3%A8%E9%87%8A%E6%A8%A1%E6%9D%BF%E8%AF%B4%E6%98%8E)
    * [自定义了方法注释模板 ：](#%E8%87%AA%E5%AE%9A%E4%B9%89%E4%BA%86%E6%96%B9%E6%B3%95%E6%B3%A8%E9%87%8A%E6%A8%A1%E6%9D%BF-)
    * [对类注释进行了优化](#%E5%AF%B9%E7%B1%BB%E6%B3%A8%E9%87%8A%E8%BF%9B%E8%A1%8C%E4%BA%86%E4%BC%98%E5%8C%96)
    * [修改注释模板：](#%E4%BF%AE%E6%94%B9%E6%B3%A8%E9%87%8A%E6%A8%A1%E6%9D%BF)
  * [五、 插件集成说明](#%E4%BA%94-%E6%8F%92%E4%BB%B6%E9%9B%86%E6%88%90%E8%AF%B4%E6%98%8E)
    * [Lombok](#lombok)
    * [Maven Helper](#maven-helper)
    * [MyBatis Log Plugin](#mybatis-log-plugin)
    * [Free MyBatis plugin](#free-mybatis-plugin)
    * [Codota](#codota)
    * [EclipseCodeFormatter](#eclipsecodeformatter)
    * [Alibaba Code Guideline](#alibaba-code-guideline)
    * [Emoji Support Plugin](#emoji-support-plugin)
    * [Git Commit Template](#git-commit-template)
    * [\.ignore](#ignore)
    * [Spring Assistant](#spring-assistant)
    * [CamelCase](#camelcase)
  * [六、 推荐阅读](#%E5%85%AD-%E6%8E%A8%E8%8D%90%E9%98%85%E8%AF%BB)
  * [七 、本仓库持续更新中，敬请期待](#%E4%B8%83-%E6%9C%AC%E4%BB%93%E5%BA%93%E6%8C%81%E7%BB%AD%E6%9B%B4%E6%96%B0%E4%B8%AD%E6%95%AC%E8%AF%B7%E6%9C%9F%E5%BE%85)

### 一、 介绍

IDEA默认的一些配置并不符合我们的使用习惯，安装IDEA后，为了提升**开发效率**和**视觉舒适度**，往往需要花费很多精力去优化那些默认配置。

 本项目对 可提升**开发效率**和**视觉舒适度**的配置进行了优化，并集成了若干插件，**使用时直接引入本项目的配置文件即可**。视觉效果如图（默认是亮色的Intelij主题，当然你也可以切换酷炫的Darcula 主题）

![](https://raw.githubusercontent.com/msh01/PicGo/master/20200302135522.png)

### 二、 用法

- **引入编辑器和注释模板配置：** 打开你的IDEA，点击`file`→`import settings`，选中仓库中的 `settings.zip`  导入IDEA即可同步本仓库的优化配置
- **引入插件：** 在IDEA的插件市场里面搜索 `plugin-importer-exporter` 插件，安装后重启，点击`file`→`import plugin` ，选择本仓库中的`plugins.json`  文件即可自动安装本配置里面包含的插件
- **设置创建新项目时的默认maven路径：** 因为每个人的本地的maven路径不同，所以需要设置你的IDEA默认配置的的maven路径（如果不在这里不设置的话，每次创建新项目时则不得不都手动设置一遍）。 找到`file` →`other settings`   →`settings for new projects` , 搜索`maven`，在里面设置你自己的创建新项目时默认的maven路径

![](https://raw.githubusercontent.com/msh01/PicGo/master/20200303001944.png)

 ### 三、  编辑器优化说明

#### 背景色和字体

-  IDEA的编辑器背景调整为`豆沙绿`的护眼色而不是亮瞎狗眼的白色，看起来更加舒适和护眼
 - 字体大小调整为`16 px`，再也不用带着放大镜去敲代码

#### 行注释

 - 行注释从注释内容往前推一个空格开始，而非从每行的第一列开始,更符合中文排版习惯

#### 热部署

 - 开启自动编译配置+勾选registry中的`compiler. automake.allow.when.app.running` ，方便热部署（spring boot应用需要引入spring-boot-devtools 依赖 配合使用）

#### 键盘映射

 -  键盘映射为`Eclipse模式`，减少了由`Eclipse`转移过来的用户的学习成本。
 - 新增了若干快捷键
    - git push     → ctrl + f8
    - git history   →  ctrl + 8
    - git pull       →  ctrl + p
    - f3 → 打开文件所在位置

#### 自动导包

 - 开启自动导包和智能移除，,再也不用手动一个个 import了。ctrl+shift+o 可以移除掉无用的import

#### 性能优化

 - 编辑器的inspection 校验进行了优化，减少了不必要的校验，从而优化加载性能，去除一大片毫无意义且醒目的黄色警告
 - 将某些红色警告改为黄色警告，避免编译错误和警告提示混在一起

#### 代码提示

 - 代码提示取消大小写敏感

#### 字符编码

- 项目的默认的字符编码全部设为`utf-8`
- `.properties` 文件防止乱码，开启 `native-to-ascii  conversion`

### 四、 方法注释和类注释模板说明



#### 自定义了方法注释模板 ：

通过**方法体内**的键入 **comm** 字符唤出方法注释模板，然后回车(**注意，一定要在方法体内。由于IDEA自身的bug，方法体外生成的注释会没有参数**)。

最后把再把方法注释拷贝到方法外部，补充上方法的说明即可。

![](https://raw.githubusercontent.com/msh01/PicGo/master/20200226000344.png)



#### 对类注释进行了优化

在类上面通过键入`cc` 字符来唤出类注释模板，然后回车，即可自动生产类注释。最后补充上类的说明即可。

![](https://raw.githubusercontent.com/msh01/PicGo/master/20200226001020.png)

#### 修改注释模板：

本注释模板可能会不满足你的需要，则可在如下图所示的位置，修改方法注释模板和类注释模板

![](https://raw.githubusercontent.com/msh01/PicGo/master/20200302235035.png)

### 五、 插件集成说明



#### Lombok

配合在项目中引入lombok的maven依赖，再也无需手写或者借助编辑器生成满屏的getter  setter 方法。

原理是在编译成字节的时候lombok会自动帮你生成getter  setter 方法。

**问题：**

我觉得借助IDEA自动生成的getter setter 方法也不错啊，为啥多此一举使用lombok？

**回答：** 

第一，getter setter 方法生成后并不是一成不变的，属性名变更或者属性删除的时候，getter setter 方法你是不是也要跟着去修改或者删除？而使用lombok的话则不必这样做

第二，少了一大堆getter setter 方法后，有没有发现代码看起来清晰了许多？毕竟代码不是要能运行，还要保证可读性

当然lombok不只是这一点功能，其它功能读者自己挖掘即可。另外lombok生成的建造者方法慎用，可能会出现json反序列化的问题。

#### Maven Helper

Maven Helper 可以帮你一目了然的查看项目的依赖树，以及依赖的路径。尤其是在maven多模块的项目中，很容易出现依赖冲突和依赖重复引入的问题（最严重的情况是同样的依赖下的类被spring 加载两次，从而导致应用启动失败）。这款插件就是解决此类场景下的问题的杀手锏

 

#### MyBatis Log Plugin

在控制台帮你生成含参数的SQL日志，方便你直接拷贝到Navicat里面定位错误。而不是带有一个个`？`的SQL，让你自己去填充。

使用这块插件时，需要手动唤起。唤起的快捷键为`ctrl+shift+alt+o`,或者点击`tools` 下面的`MyBatis Log Plugin`子菜单开启



#### Free MyBatis plugin

方便你在mybatis的dao 方法和其对应的xml 中的sql标签来回跳转，体验升天般的快感



#### Codota

一个基于机器学习的代码提示插件。相对于IDEA原有的代码提示做了增强

#### EclipseCodeFormatter

此插件需配合本仓库的阿里巴巴代码格式化模板使用，可以让你的代码排版更符合国人习惯。

请按照下图配置代码格式化模板的路径

![](https://raw.githubusercontent.com/msh01/PicGo/master/20200303001105.png)





#### Alibaba Code Guideline

代码规范扫描插件，同时可以很方便扫描出不符合阿里巴巴编程规范的代码，给以警告提示，并可一键重构

#### Emoji Support Plugin

在你提交git仓库时，可以加上表情符号，可以让你的提交记录变更丰富多彩，经实测，这些表情github和gitlab都支持

#### Git Commit Template

可以自定义IDEA里面的git commit的提交信息模板

![](https://raw.githubusercontent.com/msh01/PicGo/master/20200303002451.png)

附录git commit template 常见的五种改动类型（type of change）

```shell
- feat (新特性)
- fix (bug修复)
- docs (文档改动)
- style (格式化, 缺失分号等; 不包括生产代码变动)
- refactor (重构代码)
- test (添加缺失的测试, 重构测试, 不包括生产代码变动)
- chore (更新grunt任务等; 不包括生产代码变动)
```



#### .ignore

支持你能想象到的所有ignore文件生成。最常用的有.gitignore (Git), .hgignore (Mercurial), .npmignore (NPM), .dockerignore (Docker)等

#### Spring Assistant

在你编辑spring boot 应用的配置文件（`application.yml`,`appliction.properties`）时，给予强大的代码提示以及配置去重和配置纠错

 ####  CamelCase

通过`ctrl+alt+u` 快捷键，可以让选中的字符串在驼峰命名法和下划线命名法之间切换







### 六、 推荐阅读

[IntelliJ IDEA 2019.3利用补丁永久破解激活教程](https://www.jiweichengzhu.com/article/2940ed65c94f4671ae3f3aa72e168673)

[IntelliJ IDEA 2019.3.3 便携增强版](https://www.ghpym.com/idea.html)

[IntelliJ IDEA 简体中文专题教程](https://github.com/judasn/IntelliJ-IDEA-Tutorial)

[java代码格式化模板（阿里代码规范）](https://www.jianshu.com/p/9befe7710176)

### 七 、本仓库持续更新中，敬请期待

