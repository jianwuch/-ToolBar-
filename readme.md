平时都是自定义app的头部titlebar，这次UI给的效果发现很适合官方的ToolBar
## 1.style_toolbar.xml一些常用修改主题方式达到的效果，可以直接拷贝改改
```
<resources>
   <style name="ToolBarStyle">
        <!--弹窗的窗口在actionbar下面-->
        <item name="overlapAnchor">false</item>
        <!-- 设置popupMenu背景颜色-->
        <item name="android:colorBackground">@color/colorPrimary</item>
        <!-- 修改menu item显示字体大小 -->
        <item name="android:textSize">16sp</item>
        <item name="android:textStyle">bold</item>
        <!-- 修改字体颜色 -->
        <item name="android:textColor">@color/charcoalGrey</item>

        <!--修改字体颜色，大小，style....-->
        <item name="android:actionMenuTextAppearance">@style/actionMenuText</item>

        <!--修改展示的按钮样式-->
        <item name="actionButtonStyle">@style/ActionButtonStyle</item>
        
        <!--资源替换-->
        <!--menu溢出情况下三个点图片替换-->
        <item name="actionOverflowButtonStyle">@style/ActionButton.Overflow.Menu</item>
        <!--返回按键的替换-->
        <item name="homeAsUpIndicator">@drawable/ic_back_read_book</item>

        <!--溢出情况下弹窗列表展示修改-->
        <item name="android:dropDownListViewStyle">@style/dropDownStyle</item>
    </style>
    
    <!--用于修改popmenu的分割线-->
    <style name="dropDownStyle" parent="android:style/Widget.Holo.ListView.DropDown">
        <item name="android:listSelector">@drawable/selector_common_bg</item>
        <item name="android:divider">@color/nb.divider.common</item>
        <item name="android:dividerHeight">0.5dp</item>
    </style>
 
    <!--设置action menu文字的显示样式，大小，加黑，颜色-->
    <style name="actionMenuText">
        <item name="android:textSize">16sp</item>
        <item name="android:textStyle">bold</item>
        <item name="android:textColor">@color/paleGrey</item>
    </style>
    
    <!--针对action menu按钮样式设置:21版本之后要使用paddingEnd,下面的效果是调整按钮之间的距离，包括只有一个action时距离屏幕右边的距离-->
    <style name="ActionButtonStyle" parent="Widget.AppCompat.Light.ActionButton">
        <item name="android:paddingLeft">0dp</item>
        <item name="android:paddingRight">16dp</item>
        <item name="android:paddingEnd">16dp</item>
    </style>
    </resources>
```
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
