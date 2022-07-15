# Install from Website
# 从网页安装
1. Open your Jmix project in IntelliJ IDEA with the Jmix Studio plugin.
   使用安装了 [Jmix Studio](https://www.jmix.cn/tools/) 插件的 IntelliJ IDEA 打开 Jmix 项目。
   
2. Click the button:
   点击按钮：
Install to Jmix project
安装至 Jmix 项目

3. Switch back to IntelliJ IDEA to proceed to installation.
   切换至 IntelliJ IDEA 继续安装。

4. If the add-on installation does not start, check out this instruction or install the add-on from Studio as explained in the documentation.
   如果没有自动开始安装扩展组件，请查看[安装说明](https://www.jmix.cn/marketplace/addon-installation-troubleshooting/)或根据[文档](https://docs.jmix.cn/jmix/add-ons.html#installation)从 Studio 中安装。

Alternatively, you can install any add-on from Studio according to the instruction.
或者，您可以根据[说明文档](https://docs.jmix.cn/jmix/add-ons.html#installation)从 Studio 安装任何扩展组件。

**Add-on Installation Troubleshooting**
**扩展组件安装疑难解答**

The trial add-on is available for 28 days, then becomes unavailable. Please note that only the latest add-on version is available for trial usage, so it can be used only with the latest Jmix release version. By activating a trial subscription, you accept the [Software License Agreement](jmix.cn/commercial-software-license).
扩展组件的试用期为 28 天，过期后不可使用。请注意，仅扩展组件的最新版本具有试用功能，也就是说只能在最新的 Jmix 发布版中进行试用。激活试用订阅即表示您接受[软件许可协议](jmix.cn/commercial-software-license)

# Add-on Installation Troubleshooting
# 扩展组件安装疑难解答
## If the add-on installation does not start, make sure that the following things are done:
## 如果没有自动开始安装扩展组件，请检查以下配置：
- IntelliJ IDEA instance with the installed Jmix plugin is running on your computer.
- 您电脑中正在运行安装了 Jmix 插件的 IntelliJ IDEA。

- Your IDEA debug port is **63343**
- 您 IDEA 的调试端口为 **63343**
  
To set-up the IDEA debug port go to
如需设置 IDEA 的调试端口，在 IDEA 中打开

**Execution, Deployment | Debugger settings**
**Build, Execution, Deployment | Debugger** 设置

**(File | Settings | Build, Execution, Deployment | Debugger** for Windows and Linux
Windows 和 Linux 为：**(File | Settings | Build, Execution, Deployment | Debugger**

or **IntelliJ IDEA | Preferences | Build, Execution, Deployment | Debugger** for macOS)
macOS 为：**IntelliJ IDEA | Preferences | Build, Execution, Deployment | Debugger**

and find the Port settings:
然后修改端口设置：

- You are using one of the supported browsers: Chrome, Firefox, Opera. Installation is not supported on Safari.
- 请使用支持的浏览器安装：Chrome，Firefox，Opera。目前不支持通过 Safari 安装。
