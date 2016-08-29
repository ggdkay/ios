

真机调试xcode，The entitlements specified in your application’s Code Signing Entitlements file do not match those specified in your provisioning profile
code4上下载一个Demo，在点击Build And Run后，提示 The entitlements specified in your application’s Code Signing Entitlements file do not match those specified in your provisioning profile.(0xE8008016). 错误，致使无法将应用程序装到手机上。

解决方法：
找到Targets中的Build Settings选项卡中的Code Signing Entitlements，删除该项的值，重新Build即可解决。

