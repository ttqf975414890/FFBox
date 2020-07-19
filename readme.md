# FFBox

多媒体转码百宝箱  

![软件截图](http://ffbox.ttqf.tech/img/%E8%BD%AF%E4%BB%B6%E6%88%AA%E5%9B%BE.png)

*可能是地球上最漂亮的多媒体转码软件*  
*本软件是 FFmpeg 的一个 GUI，使用 FFmpeg 进行多媒体转码并提供动感的进度显示*  
*支持添加滤镜、调节速度等多种功能（通过后期更新增加）*  
*转码，本应如此有意思*  

## 更新说明

**2020-07-09 更新：** FFBox 1.x 使用了传统的原生 web 技术进行开发，开发速度快，但结构性差。考虑到未来的开发需求，将使用 vue-cli 重构工程。因此 FFBox 2.x 的项目结构将与 FFBox 1.x 的项目结构差异较大，请知悉。  

## 安装说明

### Windows

在 Releases 中下载并运行 FFBox_Installation_v1.1.msi，按照指示操作即可完成。  
您可在安装完成后将程序所在文件夹的内容复制出来，作为便携版使用。安装包的意义仅仅是压缩而已，相信您也知道国内访问 Github 的速度 ^_^  
当然建议您在安装后对程序所在文件夹添加“压缩”属性（NTFS 分区可用此功能），这能省下三分之一的磁盘空间，代价仅仅是额外的 <500ms 启动耗时而已 :)  

### Linux

暂未制作安装包。如需自行制作，您可参考下方的“构建说明”

### macOS

暂未制作安装包。

### Android/iOS

想想就好~

## 构建说明

### 版本 1.x

1. 下载本工程。  
2. 安装 Node.js。详情可见 [Node.js 官网](https://nodejs.org/en/)。安装完毕后，执行 `node --version`，可显示 Node.js 版本。安装过程中，应当自动安装 npm。检验方法：`npm --version`。
3. 安装依赖库。进入工程文件夹，您可使用 `npm install`、`cnpm install`、`yarn` （等方法）进行依赖库的安装。经试验，推荐使用 yarn 作为依赖库管理器，速度最快。如没有 yarn，需执行 `npm install yarn -g`  
4. 依赖库安装完成后，执行 `electron .`，即可运行 FFBox。  
5. 如需输出二进制包，您可使用 electron-packager 或 electron-builder。版本 1.x 使用的是 electron-packager。  

#### Windows 打包

使用 electron-packager：`electron-packager . FFBox --platform=win32 --arch=[x64] --icon=256.ico --out=./app --asar --app-version=[1.x]`，其中 `[x64]` 为处理器平台，可选 ia32、x64、armv7l、arm64、mips64el；`[1.x]` 为程序版本号。  
使用 electron-builder：`electron-builder build --win [target]`，其中 `[target]` 为输出类型，经测试可用的项有 nsis（msi 安装包）、nsis-web（msi 安装外壳 + 程序压缩文件）、portable（单文件便携式）、msi（msi 安装包）、dir（程序文件夹）。  

#### Linux 打包

使用 electron-packager：`electron-packager . FFBox --platform=linux --arch=[x64] --icon=256.ico --out=./app --asar --app-version=[1.x]`，其中 `[x64]` 为处理器平台，可选 ia32、x64、armv7l、arm64、mips64el；`[1.x]` 为程序版本号。  
使用 electron-builder：`electron-builder build --linux [target]`，其中 `[target]` 为输出类型，经测试可用的项有 AppImage（单文件便携式）、deb（Debian 系操作系统安装包）、dir（程序文件夹）。  

- 测试**通过**的系统：Deepin 15.11 桌面版  
- 测试**未通过**的系统：UOS 20 个人版。UOS 用户暂无法通过打安装包的方式运行 FFBox，只能以在程序文件夹中执行 `electron . --no-sandbox` 执行。  

#### macOS 打包

这就得请您自行尝试了 ^_^  

### 版本 2.x

正在做了，别急 ^_^  

## FFmpeg 安装

如果您没有 FFmpeg，那么 FFBox 只能为您输出命令行，不能进行转码工作。您需要在 [FFmpeg 下载页面](http://ffmpeg.org/download.html) 下载 FFmpeg 后，放到程序文件夹中，或者将其放到一个位置并添加环境变量，FFBox 即可进行转码工作。  

### Windows

从 [此处](https://ffmpeg.zeranoe.com/builds/) 下载 FFmpeg。Version 可以选择最新，但如果使用硬件加速时遇到需要更新显卡驱动的问题，则需要使用旧一点的版本。Linking 请选择 static。  

### Linux

从 [此处](https://johnvansickle.com/ffmpeg/) 下载 FFmpeg。请选择 static 的包。  