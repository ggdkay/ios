#UIButton

###情景：
>* 1 滚动的UILabel
>* 2 透明的UIButton view 显示 图标/文字（靠左）
>* 3 注意：更新颜色或者背景，需要使用set方法，状态：normal,highlight,selected,focus


```
example :
//MARK:- showAllPathLabel
        showAllPathLabel = MarqueeLabel.init(frame: CGRectMake(TILTE_BTN_LENGTH, TITLE_MENU_HEIGHT, SCREEN_WIDTH, TITLE_MENU_HEIGHT))
        self.view.addSubview(showAllPathLabel)

        showAllPathLabel.textColor = UIColor.orangeColor()
        showAllPathLabel.font = UIFont.boldSystemFontOfSize(16.0)
        showAllPathLabel.backgroundColor = UIColor.lightGrayColor()
        
        let showAllPathButton = UIButton.init(frame: CGRectMake(0, TITLE_MENU_HEIGHT, SCREEN_WIDTH, TITLE_MENU_HEIGHT))
        showAllPathButton.setImage(UIImage.init(named: "back"), forState: .Normal)
        showAllPathButton.contentHorizontalAlignment = UIControlContentHorizontalAlignment.Left
        //showAllPathButton.contentEdgeInsets = UIEdgeInsetsMake(0, 0, 0, 0)
        self.view.addSubview(showAllPathButton)


```
