## AccessibilityService

### Service
- 配置
AndroidManifest.xml
``` xml
  <!-- 服务监听 -->
  <service
          android:name=".service.ViAccessibilityService"
          android:permission="android.permission.BIND_ACCESSIBILITY_SERVICE">
      <intent-filter>
          <action android:name="android.accessibilityservice.AccessibilityService" />
      </intent-filter>

      <!--  配置监听数据  -->
      <meta-data
              android:name="android.accessibilityservice"
              android:resource="@xml/accessibility_config" />
  </service>
```

- 监听数据详细
accessibility_config.xml
```
<?xml version="1.0" encoding="utf-8"?>
<accessibility-service
        xmlns:android="http://schemas.android.com/apk/res/android"
        android:accessibilityEventTypes="typeAllMask"
        android:accessibilityFeedbackType="feedbackGeneric"
        android:canRetrieveWindowContent="true"
        android:description="@string/app_str"
        android:notificationTimeout="100"
        android:packageNames="com.tencent.mm"/>

        <!-- 配置你需要监听的事件类型、要监听哪个程序，最小监听间隔等属性。
        这里有两种方式可以进行配置，一种是在manifest中通过meta-data配置，
        一种是在代码中通过setServiceInfo(AccessibilityServiceInfo)设置。 -->

        <!-- accessibilityEventTypes
            指定要监听的事件类型
            typeAllMask：接收所有事件。-窗口事件相关（常用）t
            ypeWindowStateChanged：监听窗口状态变化，比如打开一个popupWindow，dialog，Activity切换等等。
            typeWindowContentChanged：监听窗口内容改变，比如根布局子view的变化。
            typeWindowsChanged：监听屏幕上显示的系统窗口中的事件更改。 此事件类型只应由系统分派。
            typeNotificationStateChanged：监听通知变化，比如notifacation和toast。
            typeViewClicked：监听view点击事件。
            typeViewLongClicked：监听view长按事件。
            typeViewFocused：监听view焦点事件。
            typeViewSelected：监听AdapterView中的上下文选择事件。
            typeViewTextChanged：监听EditText的文本改变事件。
            typeViewHoverEnter、typeViewHoverExit：监听view的视图悬停进入和退出事件。
            typeViewScrolled：监听view滚动，此类事件通常不直接发送。
            typeViewTextSelectionChanged：监听EditText选择改变事件。
            typeViewAccessibilityFocused：监听view获得可访问性焦点事件。
            typeViewAccessibilityFocusCleared：监听view清除可访问性焦点事件。

            手势事件相关
            typeGestureDetectionStart、typeGestureDetectionEnd：监听手势开始和结束事件。
            typeTouchInteractionStart、typeTouchInteractionEnd：监听用户触摸屏幕事件的开始和结束。
            typeTouchExplorationGestureStart、typeTouchExplorationGestureEnd：监听触摸探索手势的开始和结束。
         -->

        <!-- accessibilityFeedbackType
                指定反馈方式
                feedbackAllMask、所有的反馈
                feedbackGeneric、通用反馈
                feedbackAudible、表示声音(不是语音)反馈
                feedbackSpoken、语音反馈
                feedbackHaptic、触感反馈
                feedbackVisual 视觉反馈
         -->

        <!-- canRetrieveWindowContent="true"
            允许服务检索窗口内容
            是否希望能够检索活动窗口内容。此设置无法在运行时更改。
        -->

        <!-- description
            该服务的简要说明
         -->

        <!-- notificationTimeout
            两个相同类型的可访问性事件之间的最短间隔时间（以毫秒为单位）
         -->

        <!-- packageNames
            要监听的应用的包名
            如果要监听多个应用，则用,去分隔
         -->

        <!-- canPerformGestures
            是否可以执行手势（api 24新增）
         -->

```
