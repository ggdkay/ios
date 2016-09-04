http://lecason.com/2015/11/23/iOS-NSData-UInt-Array-UInt-exchance/

---
// [UInt] 数组转化成 NSDate
>extension Array {
    func toData() -> NSData {
        let commandData: NSMutableData = NSMutableData()
        for var subCommand in self {
            commandData.appendBytes(&subCommand, length: 1)
        }
        return commandData
    }
}

// 大端模式的[UInt]数组转换成UInt
// 大端模式 [0x01,0x02] 转化成 Binary = [0b00000001, 0b00000010] 转化成 Hex 应该是 0x0102
>extension NSData {
    func toBigendInt() -> UInt {
        
        if self.length > 8 { print("\n【toBigendInt overflow max big-end 8 byte maybe get the wrong value】\n") }
        
        let intMutableArray = NSMutableData()
        var subData = NSData()
        for var i = self.length - 1; i >= 0;  --i {
            subData = self.subdataWithRange(NSMakeRange(i, 1))
            intMutableArray.appendData(subData)
        }
        var commandInt:UInt = 0
        intMutableArray.getBytes(&commandInt, length: sizeof(self.dynamicType))
        return commandInt
    }
}
// 小端模式的[UInt]数组转换成UInt
// 小端模式 [0x01,0x02] 会转成 Binary = [0b00000010, 0b00000001] 转化成 Hex 应该是 0x0201
>extension NSData {
    func toSmallendInt() -> UInt {
        
        if self.length > 8 { print("\n【toSmallendInt overflow max big-end 8 byte maybe get the wrong value】\n") }
        
        var commandInt:UInt = 0
        self.getBytes(&commandInt, length: sizeof(self.dynamicType))
        return commandInt
    }
}

// NSData 转化成UInt 数组
>extension NSData {
    func toUIntArray() -> [UInt8] {
        var uintArray = [UInt8]()
        var subData: NSData!
        for i in 0..<self.length {
            subData = self.subdataWithRange(NSMakeRange(i, 1))
            uintArray.append(UInt8(subData.toSmallendInt()))
        }
        return uintArray
    }
}

---

>
override func viewDidLoad() {
super.viewDidLoad()
    let intArray = [0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08]
    let intData = intArray.toData()
    let small = intData.toSmallendInt()
    let big = intData.toBigendInt()
    let uintArray = intData.toUIntArray()
    print("intArray: \(intArray)\nintData: \(intData)\nsmall: \(small)\nbig: \(big)\nuintArray: \(uintArray)\n")
}


>
intArray: [1, 2, 3, 4, 5, 6, 7, 8]
intData: <01020304 05060708>
small: 578437695752307201
big: 72623859790382856
uintArray: [1, 2, 3, 4, 5, 6, 7, 8]
