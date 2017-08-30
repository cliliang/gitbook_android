1、将dialog显示有屏幕底部
```java
Window window = dialog.getWindow();
WindowManager.LayoutParams params = window.getAttributes();
Display display = window.getWindowManager().getDefaultDisplay();
params.width = display.getWidth();
params.height = WindowManager.LayoutParams.WRAP_CONTENT;
dialog.getWindow().setGravity(Gravity.BOTTOM);
```
对应的dialog style
```xml
<style name="dialog_bottom" parent="android:style/Theme.Dialog">
    <!--dialog浮现在Activity之上-->
    <item name="android:windowIsFloating">true</item>
    <!--dialog的背景透明-->
    <item name="android:windowBackground">@android:color/transparent</item>
    <item name="android:windowContentOverlay">@null</item>
    <!--dialog 的窗口边框-->
    <item name="android:windowFrame">@null</item>
    <!--dialog意外的部分模糊显示-->
    <item name="android:backgroundDimEnabled">true</item>
    <!--窗口没有标题-->
    <item name="android:windowNoTitle">true</item>
    <!--dialog进入和退出的动画-->
    <item name="android:windowAnimationStyle">@style/dialog_bottom_animation</item>
</style>

<style name="dialog_bottom_animation" parent="@android:style/Animation.Dialog">
    <item name="android:windowEnterAnimation">@anim/dialog_enter</item>
    <item name="android:windowExitAnimation">@anim/dialog_out</item>
</style>
```
dialog_enter.xml
```xml
<translate xmlns:android="http://schemas.android.com/apk/res/android"
    android:duration="200"
    android:fromYDelta="100%"
    android:interpolator="@android:anim/overshoot_interpolator"
    android:toYDelta="0" />
```
dialog_out.xml
```xml
<translate xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromYDelta="0"
    android:toYDelta="100%"
    android:duration="200"
    />
```