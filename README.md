## Intellij IDEA优化配置最佳实践



 本项目对 可提升**开发效率**和**视觉舒适度**的配置进行了优化，并集成了若干插件。视觉效果如图



![](https://raw.githubusercontent.com/msh01/PicGo/master/20200225235330.png)

### 一、 用法

- **引入编辑器配置：**使用时点击`file`→`import settings`，选中仓库中的 `settings.zip`  导入IDEA即可同步本仓库的优化配置，再也无需手动的一个个配置。尤其是在重装系统或者更换电脑的情况下。
- **引入插件：**在IDEA的插件市场里面搜索 `plugin-importer-exporter` 插件，安装重启后，点击`file`→`import plugin` ，选择仓库中的`plugins.json`  文件即可自动安装本配置里面的插件



 ### 二、  编辑器优化说明

-  IDEA的编辑器背景调整为豆沙绿的护眼色，看起来更加舒适

 - 字体大小调整为`14 px`，再也不用带着放大镜去敲代码
 - 行注释空格开始，而非从行第一列开始,更符合中文排版习惯
 - 自动编译，方便热部署（需配合spring-boot-devptools）
 - 键盘映射为Eclipse模式，并新增了若干快捷键
    - git push     → ctrl+f8
    - git history   →  ctrl+8
    - git pull       →  ctrl +p 
 - 自动导包,再也不用手动一个个 import了
 - 编辑器的inspection 校验进行了优化，减少了不必要的校验，从而优化加载性能
 - 代码提示的大小写模糊



### 三、 方法注释和类注释模板说明



#### 自定义了方法注释模板 ：

通过**方法体内**的键入 **comm** 字符呼出注释模板，然后回车(注意，**一定要在方法体内。由于IDEA自身的bug，方法体外生成的注释会没有参数**)。

最后把再方法注释拷贝到方法外部，补充上方法的说明即可

![](https://raw.githubusercontent.com/msh01/PicGo/master/20200226000344.png)



#### 对类注释进行了优化

在类上面通过键入`cc` 字符来唤出类注释模板，然后回车，即可自动生产类注释。最后补充上类的说明即可。

![](https://raw.githubusercontent.com/msh01/PicGo/master/20200226001020.png)

### 四、 插件集成说明



#### Lombok

在项目中引入lombok的maven依赖后，配合此插件，可以替你省去一大堆编写getter  setter 方法的时间。原理是在编译成字节的时候lombok会自动帮你生成getter  setter 方法。

当然lombok不只是这一点功能，其它功能读者自己挖掘即可

#### Maven Helper

Maven Helper 属于那种你平常很少用到，但却是必备的一款插件。尤其是在maven多模块的项目中，很容易出现依赖冲突和依赖重复引入的问题（最严重的情况是同样的类被spring 加载两次，从而向应用启动失败）。这款插件就是解决此类场景下的问题的杀手锏



#### MyBatis Log Plugin

在控制台帮你生成含参数的SQL日志，方便你直接拷贝到Navicat里面定位错误。而不是带有一个个？的SQL，让你自己去填充



#### Free MyBatis plugin

方便你在mybatis的xml的SQL子句和它对应的dao 方法中来回跳转，体验升天般的舒爽



#### Codota

一个基于机器学习的代码提示插件。相当于对idea原有的代码提示做了增强

#### alibaba code guideline

代码规范扫描插件，同时可以很方便帮你重构代码。此插件需配合本仓库的代码模板使用

#### Emoji Support Plugin

在你提交git仓库时，可以加上表情符号，可以让你的提交记录变更丰富多彩，经实测，这些表情github和gitlab都支持

#### Git Commit Template

git commit的提交信息模板



#### .ignore

支持你能想象到的所有ignore文件生成。例如`.gitignore`

#### Spring Assistant

在你编辑spring boot配置文件时，给予强大的代码提示以及去重和纠错

 ####  

 ###  

 

### 后续待完善 