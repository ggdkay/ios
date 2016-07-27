## volume


**Get Volume**
###class AppDelegate
```

  func application(application: UIApplication, didFinishLaunchingWithOptions launchOptions: [NSObject: AnyObject]?) -> Bool {
 
         NSNotificationCenter.defaultCenter().addObserver(self, selector: #selector(volumeChanged(_ :)), name:"AVSystemController_SystemVolumeDidChangeNotification", object: nil)
    }    



    //MARK: - change system volume set app volume in music after 2nd version
    func volumeChanged(noti : NSNotification){
        let volume  = noti.userInfo?["AVSystemController_AudioVolumeNotificationParameter"] as! Float
        print("vol sys : \(volume)")
 
    }
```
###print 0~1(per 0.0625)
>*vol sys : 0.0625

**Set Volume**

###MPVolumeView
```
 _volumeView = [[MPVolumeView alloc]init];

 _volumeView.showsRouteButton = NO;
 //默认YES，这里为了突出，故意设置一遍
 _volumeView.showsVolumeSlider = YES;

 [_volumeView sizeToFit];
 [_volumeView setFrame:CGRectMake(-1000, -1000, 10, 10)];

 [self addSubview:_volumeView];
 [_volumeView userActivity];

 for (UIView *view in [_volumeView subviews]){
     if ([[view.class description] isEqualToString:@"MPVolumeSlider"]){
         _volumeSlider = (UISlider*)view;
         break;
     }
 }
 //设置默认打开视频时声音为0.3，如果不设置的话，获取的当前声音始终是0
 [_volumeSlider setValue:0.2];

 //获取最是刚打开时的音量值
 _volumeValue = _volumeSlider.value;

 //设置展示音量条的值
 _showVolueSlider.value = _volumeValue;
```
[MPVolumeView from : ](http://www.jianshu.com/p/683f3f312a79)
[Camera volume control From](https://www.quora.com/How-can-I-detect-volume-up-down-button-press-in-Swift)
[From Tips](http://www.cnblogs.com/KiVen2015/p/5670288.html)
