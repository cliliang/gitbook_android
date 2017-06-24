##安全漏洞
在Android level 16及以前版本存在远程代码执行安全漏洞，该漏洞源于程序没有正确限制使用Webview.addJavascriptInterface方法，远程攻击者可以使用java的反射机制利用该漏洞执行任意Java对象方法。
##在布局中的使用
在布局文件中一般放入LinearLayout等容器中，但是要在代码中动态加入，在onDestroy中，先remove webview，然后，webview.removeAllViews()， Webview.destroy()。
##Jsbridge
在Web端和Native端建立一座桥，让Native端可以调用Web端的方法，Web端也可以调用Native的方法。
##WebviewClient.onPageFinish()方法
当前正在加载的网页产生跳转的时候，这个方法会被很多次调用，建议不用此方法，而是用WebChromeClient.onProgressChanged()方法。
##webview性能优化
因为在使用webview的时候，它用自己在后台创建很多线程，如果没有完全销毁，会很耗电。可以在退出程序的时候，调用System.exit()，完全销毁Java虚拟机。
##Webview硬件加速导致的页面渲染问题
容易产生页面加载的块和界面闪烁的现象，可以设置Webview界面暂时关闭硬件加速。
##内存泄漏
1.将webview放入单独线程中处理，简单粗暴，但是可能涉及线程间通信。
2.将webview动态的加入到viewGroup中