# DialogFragment
Android官方推荐在Android 3.0之后，使用 DialogFragment 来代替 Dialog。

## 简单使用
- 继承DialogFragment
``` kotlin
class SwitchDoorDialog : DialogFragment() {
    override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle?): View? {
        return inflater.inflate(R.layout.dialog_switch_door, container, false)
    }
}
```
- 使用
``` kotlin
SwitchDoorDialog().show(supportFragmentManager,"Vi")
```

## 其他方法
- dialog消失方法
``` kotlin
    //点击其他区域消失
    dialog.setCanceledOnTouchOutside(true)

    //dialog弹出后会点击屏幕或物理返回键，dialog不消失
    dialog.setCancelable(false)

    //dialog弹出后会点击屏幕，dialog不消失；点击物理返回键dialog消失
    dialog.setCanceledOnTouchOutside(false)
```

- 设置style

Style代码
``` xml
    <style name="DialogStyle" parent="@android:style/Theme.Holo.Light.Dialog">
        <!-- 窗口背景色 -->
        <item name="android:windowBackground">@android:color/transparent</item>
        <!--是否有覆盖-->
        <item name="android:windowContentOverlay">@null</item>
        <!-- 浮于Activity之上 -->
        <item name="android:windowIsFloating">true</item>
        <!-- 边框 -->
        <item name="android:windowFrame">@null</item>
        <!-- Dialog以外的区域模糊效果 -->
        <item name="android:backgroundDimEnabled">true</item>
        <!-- 无标题 -->
        <item name="android:windowNoTitle">true</item>
        <!-- 半透明 -->
        <item name="android:windowIsTranslucent">true</item>
        <!--进出动画-->
        <item name="android:windowAnimationStyle">@android:style/Animation.Translucent</item>
    </style>
```
使用
``` kotlin
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setStyle(DialogFragment.STYLE_NO_FRAME, R.style.DialogStyle)
    }
```
