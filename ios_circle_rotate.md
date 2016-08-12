#make circle view,initAnimat,playAnimat,pauseAnimat
```
  circleView = UIImageView.init()
        circleView.frame = CGRectMake(50, 50, 200, 200)
        circleView.image = UIImage.init(named: "te") //
        circleView.layer.cornerRadius = CGRectGetHeight((circleView.bounds))/2
        circleView.layer.masksToBounds = true
        circleView.layer.borderColor = UIColor.lightGrayColor().CGColor
        circleView.layer.borderWidth = 8
        self.view.addSubview(circleView)
```

```

  var circleView : UIImageView!
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
        
        circleView = UIImageView.init()
        circleView.frame = CGRectMake(50, 50, 200, 200)
        circleView.image = UIImage.init(named: "te") //
        circleView.layer.cornerRadius = CGRectGetHeight((circleView.bounds))/2
        circleView.layer.masksToBounds = true
        circleView.layer.borderColor = UIColor.lightGrayColor().CGColor
        circleView.layer.borderWidth = 8
        self.view.addSubview(circleView)
       // initRotationAnimation(circleView)

        let  initbtn = UIButton.init()
        initbtn.frame = CGRectMake(50, 300, 80, 40)
        initbtn.backgroundColor = UIColor.lightGrayColor()
        initbtn.setTitle("initbtn", forState: .Normal)
        self.view.addSubview(initbtn)
        initbtn.addTarget(self, action: #selector(initClick(_:)), forControlEvents: .TouchUpInside)
        
        let  pausebtn = UIButton.init()
        pausebtn.frame = CGRectMake(50, 350, 80, 40)
        pausebtn.backgroundColor = UIColor.lightGrayColor()
        pausebtn.setTitle("pausebtn", forState: .Normal)
        self.view.addSubview(pausebtn)
        pausebtn.addTarget(self, action: #selector(pauseClick(_:)), forControlEvents: .TouchUpInside)
        
        let  playBtn = UIButton.init()
        playBtn.frame = CGRectMake(50, 400, 80, 40)
        playBtn.backgroundColor = UIColor.lightGrayColor()
        playBtn.setTitle("playBtn", forState: .Normal)
        self.view.addSubview(playBtn)
        playBtn.addTarget(self, action: #selector(playClick(_:)), forControlEvents: .TouchUpInside)
        
        let  resetbtn = UIButton.init()
        resetbtn.frame = CGRectMake(50, 450, 80, 40)
        resetbtn.backgroundColor = UIColor.lightGrayColor()
        resetbtn.setTitle("resetbtn", forState: .Normal)
        self.view.addSubview(resetbtn)
        resetbtn.addTarget(self, action: #selector(resetClick(_:)), forControlEvents: .TouchUpInside)
    }
    
    func initClick(sender : UIButton){
    
         initRotationAnimation(circleView)
        
    }
    
    
    func resetClick(sender : UIButton){
   
       playRotationAnimation(circleView)
       initRotationAnimation(circleView)
        
    }
    
   
    func pauseClick(sender : UIButton){
        
       pauseRoationAnimation(circleView)
        
    }
    
    func playClick(sender : UIButton){
         playRotationAnimation(circleView)
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }
    
    
    //circle init rotate 图片旋转动画
    internal func initRotationAnimation(someView : UIView){
         circleView.layer.removeAllAnimations()
        let rotation=CABasicAnimation(keyPath: "transform.rotation.z")
        rotation.timingFunction=CAMediaTimingFunction(name: kCAMediaTimingFunctionLinear)
        rotation.toValue=2*M_PI
        rotation.duration=10
        rotation.repeatCount=FLT_MAX
        rotation.cumulative=true
//        rotation.autoreverses=false
        someView.layer.addAnimation(rotation, forKey: "rotationAnimation")
    }
    
    func resetRotationAnimation(someView : UIView){
        let pausedTime = someView.layer.timeOffset
        let sumTime = someView.layer.convertTime(CACurrentMediaTime(), fromLayer: nil)
        someView.layer.speed = 0
        
        let timeSinceZero = pausedTime
        someView.layer.beginTime = timeSinceZero
    }
   

    func pauseRoationAnimation(someView : UIView){
        let pausedTime = someView.layer.convertTime(CACurrentMediaTime(), fromLayer: nil)
        someView.layer.speed = 0
        someView.layer.timeOffset = pausedTime
    }
    
    
    
    //circle play rotate
    func playRotationAnimation(someView : UIView){
      
        let pausedTime = someView.layer.timeOffset
        someView.layer.speed = 1
        someView.layer.beginTime = 0
        let timeSincePause = someView.layer.convertTime(CACurrentMediaTime(), fromLayer: nil)-pausedTime
        someView.layer.beginTime = timeSincePause
    }
    



```
