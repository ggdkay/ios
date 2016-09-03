## screenShot

 >
 func screenShot() -> UIImage {
         //UIGraphicsBeginImageContext(self.view.bounds.size)
        UIGraphicsBeginImageContextWithOptions(self.view.bounds.size, true, UIScreen.mainScreen().scale)
        self.view.layer.renderInContext(UIGraphicsGetCurrentContext()!)
        let screenShotImage = UIGraphicsGetImageFromCurrentImageContext()
        UIGraphicsEndImageContext()
        
        print("screenShotImage :\(screenShotImage)")
        
        //show image
        let imageView = UIImageView.init(image: screenShotImage)
        imageView.frame = CGRectMake(0, 350, SCREEN_WIDTH, SCREEN_HEIGHT)
        self.view.addSubview(imageView)
        
        //save image at photo store
        UIImageWriteToSavedPhotosAlbum(screenShotImage, self, nil, nil)
  
        return screenShotImage
    }


> file data 
      let filePath: String = NSBundle.mainBundle().pathForResource("res5", ofType: "jpg")!
       fileData = NSData.init(contentsOfFile: filePath)
