## Intellij IDEA配置优化最佳实践



### 一、 介绍

IDEA默认的一些配置并不符合我们的使用习惯，安装IDEA后，为了提升**开发效率**和**视觉舒适度**，往往需要花费很多精力去优化那些默认配置。

 本项目对 可提升**开发效率**和**视觉舒适度**的配置进行了优化，并集成了若干插件，使用时直接引入本项目的配置文件即可。视觉效果如图



![](https://raw.githubusercontent.com/msh01/PicGo/master/20200302135522.png)

### 二、 用法

- **引入编辑器和注释模板配置：** 使用时点击`file`→`import settings`，选中仓库中的 `settings.zip`  导入IDEA即可同步本仓库的优化配置，再也无需手动的一个个配置。尤其是在重装系统或者更换电脑的情况下。
- **引入插件：** 在IDEA的插件市场里面搜索 `plugin-importer-exporter` 插件，安装重启后，点击`file`→`import plugin` ，选择仓库中的`plugins.json`  文件即可自动安装本配置里面所有的插件
- **设置创建新项目时的默认maven路径：** 因为每个人的本地的maven路径不同，所以需要设置你本地的maven路径。 找到`file` →`other settings`   →`settings for new projects` , 搜索`maven`，在里面设置你自己的创建新项目时默认的maven路径

![](https://raw.githubusercontent.com/msh01/PicGo/master/20200302114940.png)

 ### 三、  编辑器优化说明

#### 背景色和字体

-  IDEA的编辑器背景调整为`豆沙绿`的护眼色而不是默认的白色，看起来更加舒适和护眼
 - 字体大小调整为`16 px`，再也不用带着放大镜去敲代码

#### 行注释

 - 行注释从注释的首个字符的往前一个空格开始，而非从每行的第一列开始,更符合中文排版习惯

#### 热部署

 - 修改了自动编译的配置+registry ，方便热部署（spring boot应用需要引入spring-boot-devtools）

#### 键盘映射

 -  键盘映射为`Eclipse模式`，减少了由`Eclipse`转移过来的用户的学习成本。
 - 新增了若干快捷键
    - git push     → ctrl + f8
    - git history   →  ctrl + 8
    - git pull       →  ctrl + p
    - f3 → 打开文件所在位置

#### 自动导包

 - 自动导包和智能移除，,再也不用手动一个个 import了。ctrl+shift+o 可以移除掉无用的import

#### 性能优化

 - 编辑器的inspection 校验进行了优化，减少了不必要的校验，从而优化加载性能，去除一大片毫无意义且醒目的黄色警告

#### 代码提示

 - 代码提示取消大小写敏感

#### 字符编码

- 项目的默认的字符编码全部设为`utf-8`
- `.properties` 文件防止乱码，开启 `native-to-ascii  conversion`

### 四、 方法注释和类注释模板说明



#### 自定义了方法注释模板 ：

通过**方法体内**的键入 **comm** 字符唤出注释模板，然后回车(**注意，一定要在方法体内。由于IDEA自身的bug，方法体外生成的注释会没有参数**)。

最后把再方法注释拷贝到方法外部，补充上方法的说明即可

![](https://raw.githubusercontent.com/msh01/PicGo/master/20200226000344.png)



#### 对类注释进行了优化

在类上面通过键入`cc` 字符来唤出类注释模板，然后回车，即可自动生产类注释。最后补充上类的说明即可。

![](https://raw.githubusercontent.com/msh01/PicGo/master/20200226001020.png)

### 五、 插件集成说明



#### Lombok

在项目中引入lombok的maven依赖后，配合此插件，再也无需手动写或者借助编辑器自动生成满屏的getter  setter 方法。不仅节省时间，同时还使得代码看起来更加清晰。

原理是在编译成字节的时候lombok会自动帮你生成getter  setter 方法。

当然lombok不只是这一点功能，其它功能读者自己挖掘即可。另外lombok生成的建造者方法慎用，可能会出现参数注入失败的问题。

#### Maven Helper

Maven Helper 可以帮你一目了然的查看项目的依赖树，以及依赖的路径。尤其是在maven多模块的项目中，很容易出现依赖冲突和依赖重复引入的问题（最严重的情况是同样的依赖下的类被spring 加载两次，从而导致应用启动失败）。这款插件就是解决此类场景下的问题的杀手锏

 

#### MyBatis Log Plugin

在控制台帮你生成含参数的SQL日志，方便你直接拷贝到Navicat里面定位错误。而不是带有一个个？的SQL，让你自己去填充。

使用这块插件时，需要手动唤起。唤起的快捷键为`ctrl+shift+alt+o`,或者点击tools 下面的`MyBatis Log Plugin`子菜单开启



#### Free MyBatis plugin

方便你在mybatis的dao的xmlSQL子句和它对应的dao 方法中来回跳转，体验升天般的快感



#### Codota

一个基于机器学习的代码提示插件。相当于对IDEA原有的代码提示做了增强

#### Alibaba Code Guideline

代码规范扫描插件，同时可以很方便帮你重构代码。此插件需配合本仓库的代码模板使用

#### Emoji Support Plugin

在你提交git仓库时，可以加上表情符号，可以让你的提交记录变更丰富多彩，经实测，这些表情github和gitlab都支持

#### Git Commit Template

可以自定义IDEA里面的git commit的提交信息模板

<img src="https://raw.githubusercontent.com/msh01/PicGo/master/20200229204334.png" align="center"/>

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

支持你能想象到的所有ignore文件生成。最常用的有`.gitignore`

#### Spring Assistant

在你编辑spring boot配置文件（`application.yml`,`appliction.properties`）时，给予强大的代码提示以及配置去重和配置纠错

 ####  





### 六、 推荐阅读

[IntelliJ IDEA 2019.3利用补丁永久破解激活教程](https://www.jiweichengzhu.com/article/2940ed65c94f4671ae3f3aa72e168673)

[IntelliJ IDEA 2019.3.3 便携增强版](https://www.ghpym.com/idea.html)

[IntelliJ IDEA 简体中文专题教程](https://github.com/judasn/IntelliJ-IDEA-Tutorial)

[java代码格式化模板（阿里代码规范）](https://www.jianshu.com/p/9befe7710176)

### 七 、本仓库持续更新中，敬请期待