
####XCode6编译工程，程序XXXX主target编译没有错误，但是XXXXTests测试target出现编译错误。
	CodeSign error: code signing is required for product type 'Unit Test Bundle' in SDK 'iOS 8.0' 
	
####错误原因
XCTest.framework只有在基于iOS8的工程下才能使用，当前工程并不支持XCTest但是却运行了XXXXTest的target。

####解决方法:
	XCode6 --> Edit Scheme --> Build --> Targets --> XXXXTests --> 确认Run选项没有被选中。

如果此选项被选中，则每次编译的时不仅会编辑XXXX程序主target而且会编译XXXXTests,由于当前程序并不支持XCTest,因此XXXXTests会报错。因此，我们要确保编译时只编译XXXX主target，不要编译XXXXTests的测试target。    
Scheme中的设置是每个开发者独立存储的，此问题并不会影响其他开发者调试程序。

更为直接的方法就是直接删除XXXXTests测试target，然后再编译运行就可以了。

####参考链接
* [http://www.cocoachina.com/ask/questions/show/120680/CodeSignerror](http://www.cocoachina.com/ask/questions/show/120680/CodeSignerror)
* [Code signing is required for product type Unit Test Bundle in SDK iOS 8.0](http://stackoverflow.com/questions/26109851/code-signing-is-required-for-product-type-unit-test-bundle-in-sdk-ios-8-0)
* [Code signing is required for product type 'Unit Test Bundle' in SDK 'iOS 8.0'](http://stackoverflow.com/questions/26057455/code-signing-is-required-for-product-type-unit-test-bundle-in-sdk-ios-8-0)