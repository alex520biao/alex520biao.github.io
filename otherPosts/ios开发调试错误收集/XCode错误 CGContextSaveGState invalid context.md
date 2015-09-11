
###CGContextSaveGState: invalid context 0x0 
----
错误信息如下:
<Error>: CGContextSaveGState: invalid context 0x0. This is a serious error. This application, or a library it uses, is using an invalid context  and is thereby contributing to an overall degradation of system stability and reliability. This notice is a courtesy: please fix this problem. It will become a fatal error in an upcoming update.

###解决方法:
---
将原先的 CGContextSaveGState(context)与CGContextRestoreGState(context) 换成 UIGraphicsPushContext(context); 和 UIGraphicsPopContext();
 
###引用参考
1. [http://www.cocoachina.com/ask/questions/show/52532](http://www.cocoachina.com/ask/questions/show/52532)


