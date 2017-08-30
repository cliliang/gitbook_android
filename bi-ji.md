1、将dialog显示有屏幕底部
```java
Window window = dialog.getWindow();
WindowManager.LayoutParams params = window.getAttributes();
Display display = window.getWindowManager().getDefaultDisplay();
params.width = display.getWidth();
params.height = WindowManager.LayoutParams.WRAP_CONTENT;
dialog.getWindow().setGravity(Gravity.BOTTOM);
```