##ios setting 

[ios app to setting](http://blog.csdn.net/github_34613936/article/details/51506959)
```
ex :
> * 1 //蓝牙设置界面
    NSURL *url = [NSURL URLWithString:@"prefs:root=Bluetooth"];
    if ([[UIApplication sharedApplication] canOpenURL:url])
    {
        [[UIApplication sharedApplication] openURL:url];
    }
    
>* 2 <code>[[UIApplication sharedApplication] openURL:[NSURL URLWithString:UIApplicationOpenSettingsURLString]];</code>

>* 3 [[UIApplicationsharedApplication] openURL:[NSURLURLWithString:@"prefs:root=Bluetooth"]];
  info -> 在URL Types中添加一个新项。我没有深入研究，只填写prefs就可以了
```



```
1.参数配置

我在网上找到一个列表，可以跳到这些界面的参数配置：
About — prefs:root=General&path=About

Accessibility — prefs:root=General&path=ACCESSIBILITY

Airplane Mode On — prefs:root=AIRPLANE_MODE

Auto-Lock — prefs:root=General&path=AUTOLOCK

Brightness — prefs:root=Brightness

Bluetooth — prefs:root=General&path=Bluetooth

Date & Time — prefs:root=General&path=DATE_AND_TIME

FaceTime — prefs:root=FACETIME

General — prefs:root=General

Keyboard — prefs:root=General&path=Keyboard

iCloud — prefs:root=CASTLE

iCloud Storage & Backup — prefs:root=CASTLE&path=STORAGE_AND_BACKUP

International — prefs:root=General&path=INTERNATIONAL

Location Services — prefs:root=LOCATION_SERVICES

Music — prefs:root=MUSIC

Music Equalizer — prefs:root=MUSIC&path=EQ

Music Volume Limit — prefs:root=MUSIC&path=VolumeLimit

Network — prefs:root=General&path=Network

Nike + iPod — prefs:root=NIKE_PLUS_IPOD

Notes — prefs:root=NOTES

Notification — prefs:root=NOTIFICATIONS_ID

Phone — prefs:root=Phone

Photos — prefs:root=Photos

Profile — prefs:root=General&path=ManagedConfigurationList

Reset — prefs:root=General&path=Reset

Safari — prefs:root=Safari

Siri — prefs:root=General&path=Assistant

Sounds — prefs:root=Sounds

Software Update — prefs:root=General&path=SOFTWARE_UPDATE_LINK

Store — prefs:root=STORE

Twitter — prefs:root=TWITTER

Usage — prefs:root=General&path=USAGE

VPN — prefs:root=General&path=Network/VPN

Wallpaper — prefs:root=Wallpaper

Wi-Fi — prefs:root=WIFI
```
