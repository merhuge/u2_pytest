运行环境 Python 3.7.7, pytest-6.2.3, allure-pytest-2.8.13, reportlog-0.1.2, pytest-rerunfailures-9.1.1, uiautomator2


#1、识别机器
 adb devices
List of devices attached
HLRDU19815003620	device


#2、设备安装 atx-agent （android手机的驱动软件）
 python3 -m uiautomator2 init

[I 210420 11:29:36 init:155] uiautomator2 version: 2.9.0
[D 210420 11:29:39 init:390] atx-agent version 0.9.4
Successfully init AdbDevice

#3、识别元素 （weditor）
执行pip3 install weditor命令
在命令行中 输出 python -m weditor ( or weditor )
即可在浏览器中打开课元素识别的 界面。

#4业务相关
功能：
   目的：获取回放 进入，退出，心跳保持的埋点
   过程：进入指定回放，保持一段时间 app会定时埋点上报，再汇总埋点数据
   说明：回放进入 退出的点 是实时上报，心跳保持的点是非实时上报，且为一分钟一次。

执行case：
   进入到 pytest_case 文件夹
   执行命令：pytest test_Into_playback.py --reruns 3 --alluredir allure_report
查看测试报告：
   执行完case后 生成报告：allure serve allure_report
