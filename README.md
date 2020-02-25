## intellij IDEA优化配置最佳实践



 本项目对如下可提升开发效率和视觉舒适度的配置进行了优化，并集成了若干插件。

### 一、 用法

- 使用时直接把仓库中的 `settings.zip`  导入IDEA即可同步本仓库的优化配置，再也无需手动的一个个配置。尤其是在重装系统或者更换电脑的情况下。
- 在IDEA里面按照`plugin export import` 插件，重启后，点击`import plugin` ，选择仓库中的`plugins.json`  文件即可自动安装本配置里面的插件



 ### 二、  编辑器优化说明

-  IDEA的编辑器背景调整为豆沙绿的护眼色，看起来更加舒适

 - 字体大小调整为`14 px`，再也不用带着放大镜去敲代码
 - 行注释空格开始，而非从行第一列开始,更符合中文排版习惯
 - 自动编译，方便热部署
 - 键盘映射为Eclipse模式，并新增了若干快捷键
    - git push     → ctrl+f8
    - git history   →  ctrl+8
    - git pull       →  ctrl +p 
 - 自动导包
 - inspection 校验进行了优化，减少了不必要的校验，从而优化加载性能
 - 代码提示的大小写模糊



### 三、 方法注释和类注释模板说明

- 自定义了method template ，通过**方法体内**的键入 **comm** 字符来呼出(记住，一定要在方法体内。IDEA自身的bug，方法体生成的注释会没有参数)
- 对类注释进行了优化



### 四、 插件集成说明



#### lombok

配合lombok的maven依赖，可以替你省去一大堆编写getter  setter 方法的时间


 - Maven Helper
 - MyBatis Log Plugin
 - Free MyBatis plugin
 - Codota
 - alibaba code guideline
 - Emoji Support Plugin
 - ESLint
 - Git Commit Template
 - .ignore
 - Spring Assistant
 ####  

 ###  

 

### 后续待完善 