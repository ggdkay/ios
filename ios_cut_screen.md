## screenShot

>1 ImageHelper help with many function  

https://github.com/melvitax/ImageHelper

>2 how to use ? goto hangg.com 

http://www.hangge.com/blog/cache/detail_757.html

 --- 
 
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
    
---

--- swift file data 

      let filePath: String = NSBundle.mainBundle().pathForResource("res5", ofType: "jpg")!
       fileData = NSData.init(contentsOfFile: filePath)
       
---
