平时都是自定义app的头部titlebar，这次UI给的效果发现很适合官方的ToolBar
## 1.style_toolbar.xml一些常用修改主题方式达到的效果
## 2.让溢出菜单情况下显示的menu 列表弹窗显示icon方式
```
 override fun onPrepareOptionsMenu(menu: Menu) {
        if (menu != null) {
            if (menu.javaClass.getSimpleName().equals("MenuBuilder")) {
                try {
                    val method = menu.javaClass.getDeclaredMethod(
                        "setOptionalIconsVisible",
                        java.lang.Boolean.TYPE
                    )
                    method.isAccessible = true
                    method.invoke(menu, true)
                } catch (e: Exception) {
                    e.printStackTrace()
                }
            }
        }
        super.onPrepareOptionsMenu(menu)
    }
```
