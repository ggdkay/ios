#Link(Carlos Butron,Gesture.swift)
>* change with gesture and click

```
  
    @IBOutlet weak var testButton: UIButton!
    @IBOutlet weak var image: UIImageView!
    
    @IBOutlet weak var test2Button: UIButton!
    var timer: NSTimer!
    
    override func viewDidLoad() {
        
        //ROTATION
        let rotateGesture = UIRotationGestureRecognizer(target: self, action: "rotateGesture:")
        image.addGestureRecognizer(rotateGesture)
        
        //SWIPE
        let swipeGestureRight = UISwipeGestureRecognizer(target: self, action: "respondToSwipeGesture:")
        swipeGestureRight.direction = UISwipeGestureRecognizerDirection.Right
        image.addGestureRecognizer(swipeGestureRight)
        
        let swipeGestureDown = UISwipeGestureRecognizer(target: self, action: "respondToSwipeGesture:")
        swipeGestureDown.direction = UISwipeGestureRecognizerDirection.Down
        image.addGestureRecognizer(swipeGestureDown)
        
        let swipeGestureLeft = UISwipeGestureRecognizer(target: self, action: "respondToSwipeGesture:")
        swipeGestureLeft.direction = UISwipeGestureRecognizerDirection.Left
        image.addGestureRecognizer(swipeGestureLeft)
        
        let swipeGestureUp = UISwipeGestureRecognizer(target: self, action: "respondToSwipeGesture:")
        swipeGestureUp.direction = UISwipeGestureRecognizerDirection.Up
        image.addGestureRecognizer(swipeGestureUp)
        
        //LONG PRESS
        let longPressGesture = UILongPressGestureRecognizer(target: self, action: #selector(longPress(_:)))
        longPressGesture.minimumPressDuration = 2.0;
        image.addGestureRecognizer(longPressGesture)
        
        image.image = UIImage(named: "image1.png")
        

        testButton.addTarget(self, action: #selector(click), forControlEvents: .TouchUpInside)
        testButton.addGestureRecognizer(longPressGesture)
        
        
        let longLeftGesture = UILongPressGestureRecognizer.init(target: self, action: #selector(longPress(_:)))
        longLeftGesture.minimumPressDuration = 2.0
        test2Button.addTarget(self, action: #selector(click), forControlEvents: .TouchUpInside)
        test2Button.addGestureRecognizer(longLeftGesture)
        
        
        timer = NSTimer.scheduledTimerWithTimeInterval(1.0, target: self, selector: #selector(startCalcu), userInfo: nil, repeats: true)
        //pause timer
        timer.fireDate = NSDate.distantFuture()
        super.viewDidLoad()
    }
    
    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
    }
    
    var isBackwardFlag: Bool = false
    func click() {
        print("click--------")
    }
    
    func startCalcu() {
     
        
        if isBackwardFlag {
               print("  isBackwardFlag timerThread.start()===========")
        }else{
               print("  isForwardFlag timerThread.start()===========")
        }
       
    }
    
    func longPress(gestureRecognizer: UIGestureRecognizer) {
       
        if gestureRecognizer.view == testButton {
            isBackwardFlag = true
        }else if gestureRecognizer.view == test2Button {
            isBackwardFlag = false
        }
        
        if (gestureRecognizer.state == UIGestureRecognizerState.Began){
       
            print("long press---longPress-------",isBackwardFlag)
           //start timer
            timer.fireDate = NSDate.distantPast()
            
        }
        
        
        if gestureRecognizer.state == UIGestureRecognizerState.Ended {
            print("Ended----")
            //pause timer
            timer.fireDate = NSDate.distantFuture()
        }
    }
    
    //ROTATION
    @IBAction func rotateGesture(sender : UIRotationGestureRecognizer) {
        let rotation:CGFloat = sender.rotation
        let transform:CGAffineTransform  =
        CGAffineTransformMakeRotation(rotation + netRotation)
        sender.view?.transform = transform
        if (sender.state == UIGestureRecognizerState.Ended){
            netRotation += rotation;
        }
    }
    
    //SWIPE
    @IBAction func respondToSwipeGesture(send: UIGestureRecognizer) {
        
        if let swipeGesture = send as? UISwipeGestureRecognizer {
            switch swipeGesture.direction {
            case UISwipeGestureRecognizerDirection.Right:
                changeImage()
                print("Swiped right")
            case UISwipeGestureRecognizerDirection.Down:
                changeImage()
                print("Swiped down")
            case UISwipeGestureRecognizerDirection.Left:
                changeImage()
                print("Swiped left")
            case UISwipeGestureRecognizerDirection.Up:
                changeImage()
                print("Swiped up")
            default:
                break
            }
        }
    }
    
    //LONG PRESS
    @IBAction func action(gestureRecognizer:UIGestureRecognizer) {
        
        if (gestureRecognizer.state == UIGestureRecognizerState.Began){
//            let alertController = UIAlertController(title: "Alert", message: "Long Press gesture", preferredStyle: .Alert)
//            let OKAction = UIAlertAction(title: "OK", style: .Default) { (action) in }
//            alertController.addAction(OKAction)
//            self.presentViewController(alertController, animated: true) { }
            
            print("long press----------")
          //start timer
            timer.fireDate = NSDate.distantPast()
            
            
            
        }
        
     
        if gestureRecognizer.state == UIGestureRecognizerState.Ended {
            print("Ended----")
            //pause timer
            timer.fireDate = NSDate.distantFuture()
        }
      
    }
    
    
    
    
    func changeImage(){
        if (image.image == UIImage(named: "image1.png")){
            image.image = UIImage(named: "image2.png")}
        else{
            image.image = UIImage(named: "image1.png")
        }
    }


```
