# first_react_native_app （抓包说明：https://juejin.im/post/5ae73a4ff265da0b71560e7a）
  第一个React-native项目,[官网学习说明](https://reactnative.cn/docs/getting-started/)
# 搭建步骤
## 环境要求 Node, Python2, JDK（好像没有装Python2也能初步启动成功）注意 Node 的版本必须高于 8.3，Python 的版本必须为 2.x（不支持 3.x），而 JDK 的版本必须是 1.8（目前不支持 1.9 及更高版本
  1. 安装脚手命令 npm install -g yarn react-native-cli；删除npm remove -g react-native-cli
  2. 设置node国内的源： npm config set registry https://registry.npm.taobao.org --global 和 npm config set disturl https://npm.taobao.org/dist --global
  3. 安装完 yarn 后同理也要设置镜像源：yarn config set registry https://registry.npm.taobao.org --global和yarn config set disturl https://npm.taobao.org/dist --global；注意：安装完 yarn 之后就可以用 yarn 代替 npm 了，例如用yarn代替npm install命令，用yarn add 某第三方库名代替npm install 某第三方库名。
  4. 在存放工作目录执行react-native init first_react_native_app
## 搭建安卓的虚拟设备环境
  1. 进入之前下载好的安卓tools的bin目录cd D:\soft\android\tools\bin，查看命令使用帮助.\sdkmanager.bat  --help
  2. .\sdkmanager.bat  --list 查看镜像列表，安装模拟器镜像.\avdmanager.bat create avd -n test -k "system-images;android-28;default;x86_64"，可以通过命令卸载，也可以安装谷歌定制的.\sdkmanager.bat "system-images;android-28;google_apis;x86_64"，安装底层虚拟机支持.\sdkmanager.bat "emulator"；具体参考说明https://developer.android.com/studio/command-line/sdkmanager?hl=zh-cn
  3. 创建虚拟机.\avdmanager.bat create avd -n test -k "system-images;android-28;google_apis;x86_64"；删除虚拟机.\avdmanager.bat delete avd -n test
  4. 返回上级目录 D:\soft\android\tools>执行 .\android.bat list avd 查看安装虚拟机列表
  5. 需要安装HAXM，下载地址https://software.intel.com/en-us/articles/intel-hardware-accelerated-execution-manager-intel-haxm；执行虚拟机 D:\soft\android\tools> .\emulator.exe -avd test -skindir ../platforms/android-28/skins -skin WVGA854，关于emulator使用说明http://www.android-doc.com/tools/help/emulator.html；最后可以 adb devices  //cmd 运行查看设备列表
  6. windows安装iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex；安装说明：https://chocolatey.org/install；删除操作https://chocolatey.org/docs/uninstallation
## vscode 安装环境 安装说明：https://code.visualstudio.com/docs/azure/deployment
  1. 上面的导入完，打开文件夹，加载该项目，在该项目下，通过终端执行react-native run-android就会执行安卓来调试（前提真机或者虚拟设备已经连接到该开发的电脑上adb devices  //cmd 运行查看）
  2. 通过vscode 的dubug启动；安装插件React Native Tools，（Debugger For Chrome我测试没装）,然后点击vscode的调式-->添加配置；然后会在项目根目录的.vscode下新增一个launch.json 文件，里面默认生成很多类型debug："configurations"就是配置列表，在该文件的右下角还有个【添加配置】按钮。最后可以ctrl+shift+d，选择运行的配置。 进行调试输出