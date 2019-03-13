# DialogFragment
Android官方推荐在Android 3.0之后，使用 DialogFragment 来代替 Dialog。

## 简单实用
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
