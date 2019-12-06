# 文字转语音

### 安卓文字转语音的几种方式
-[TTS的几种方案](https://blog.csdn.net/cu1234567890/article/details/51767158)

### 讯飞语音的使用
-[在线语音Android SDK文档](https://www.xfyun.cn/doc/tts/online_tts/Android-SDK.html#_1、简介)
-[Android SDK文档下载地址](https://www.xfyun.cn/doc/)
-集成步骤
  - [下载SDK](https://www.xfyun.cn/sdk/dispatcher)，导入libs文件到项目
  - 添加用户权限
```
  <!--连接网络权限，用于执行云端语音能力 -->
  <uses-permission android:name="android.permission.INTERNET"/>
  <!--获取手机录音机使用权限，听写、识别、语义理解需要用到此权限 -->
  <uses-permission android:name="android.permission.RECORD_AUDIO"/>
  <!--读取网络信息状态 -->
  <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
  <!--获取当前wifi状态 -->
  <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
  <!--允许程序改变网络连接状态 -->
  <uses-permission android:name="android.permission.CHANGE_NETWORK_STATE"/>
  <!--读取手机信息权限 -->
  <uses-permission android:name="android.permission.READ_PHONE_STATE"/>
  <!--读取联系人权限，上传联系人需要用到此权限 -->
  <uses-permission android:name="android.permission.READ_CONTACTS"/>
  <!--外存储写权限，构建语法需要用到此权限 -->
  <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
  <!--外存储读权限，构建语法需要用到此权限 -->
  <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>
  <!--配置权限，用来记录应用配置信息 -->
  <uses-permission android:name="android.permission.WRITE_SETTINGS"/>
  <!--手机定位信息，用来为语义等功能提供定位，提供更精准的服务-->
  <!--定位信息是敏感信息，可通过Setting.setLocationEnable(false)关闭定位请求 -->
  <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
  <!--如需使用人脸识别，还要添加：摄相头权限，拍照需要用到 -->
  <uses-permission android:name="android.permission.CAMERA" />
```
  - 混淆
```
  -keep class com.iflytek.**{*;}
  -keepattributes Signature
```
  - 初始化
```
  // 将“12345678”替换成您申请的APPID，申请地址：http://www.xfyun.cn
  // 请勿在“=”与appid之间添加任何空字符或者转义符
  SpeechUtility.createUtility(context, SpeechConstant.APPID +"=12345678");
```
  - 使用
``` java
public class TTSUtility {
        // 发音人
        public final static String[] COLOUD_VOICERS_VALUE = {"xiaoyan", "xiaoyu", "catherine", "henry", "vimary", "vixy", "xiaoqi", "vixf", "xiaomei","xiaolin", "xiaorong", "xiaoqian", "xiaokun", "xiaoqiang", "vixying", "xiaoxin", "nannan", "vils",};

        private static final String TAG = "TTSUtility";
        // 语音合成对象
        private static SpeechSynthesizer mTts;
        //上下文
        private  Context mContext;

        private volatile static TTSUtility instance;
        /**
         * 合成回掉监听
         */
        private static SynthesizerListener mTtsListener = new SynthesizerListener() {
            @Override
            public void onSpeakBegin() {
                Log.d(TAG, "开始播放");
            }

            @Override
            public void onBufferProgress(int percent, int beginPos, int endPos, String info) {
                // TODO 缓冲的进度
                Log.d(TAG, "缓冲 : " + percent);
            }

            @Override
            public void onSpeakPaused() {
                Log.d(TAG, "暂停播放");

            }

            @Override
            public void onSpeakResumed() {
                Log.d(TAG, "继续播放");
            }

            @Override
            public void onSpeakProgress(int percent, int beginPos, int endPos) {
                // TODO 说话的进度
                Log.d(TAG, "合成 : " + percent);
            }

            @Override
            public void onCompleted(SpeechError error) {
                if (error == null) {
                    Log.d(TAG, "播放完成");

                } else if (error != null) {
                    Log.d(TAG, error.getPlainDescription(true));
                }
            }

            @Override
            public void onEvent(int eventType, int arg1, int arg2, Bundle obj) {

            }
        };
        /**
         * 构造方法
         *
         * @param context 上下文
         */
        private TTSUtility(Context context) {
            mContext = context;
            // 初始化合成对象
            mTts = SpeechSynthesizer.createSynthesizer(mContext, new InitListener() {
                @Override
                public void onInit(int code) {
                    if (code != ErrorCode.SUCCESS) {
                        Log.d("fjj", "初始化失败,错误码：" + code);
                    }
                    Log.d("fjj", "初始化失败,q错误码：" + code);
                }
            });
        }
        public static TTSUtility getInstance(Context context) {
            if (instance == null) {
                synchronized (TTSUtility.class) {
                    if (instance == null) {
                        instance = new TTSUtility(context);
                    }
                }
            }
            return  instance;
        }
        /**
         * 停止语音播报
         */
        public static void stopSpeaking() {
            // 对象非空并且正在说话
            if (null != mTts && mTts.isSpeaking()) {
                // 停止说话
                mTts.stopSpeaking();
            }
        }
        /**
         * 判断当前有没有说话
         *
         * @return
         */
        public  static boolean isSpeaking() {
            if (null != mTts) {
                return mTts.isSpeaking();
            } else {
                return false;
            }
        }
        /**
         * 开始合成
         *
         * @param text
         */
        public void speaking(String text) {
            if (TextUtils.isEmpty(text))
                return;
            int code = mTts.startSpeaking(text, mTtsListener);

            Log.d("fjj", "-----" + code + "++++++++++");

            if (code != ErrorCode.SUCCESS) {
                if (code == ErrorCode.ERROR_COMPONENT_NOT_INSTALLED) {
                    Toast.makeText(mContext, "没有安装语音+ code = " + code, Toast.LENGTH_SHORT).show();
                } else {
                    Toast.makeText(mContext, "语音合成失败,错误码: " + code, Toast.LENGTH_SHORT).show();
                }
            }
        }
        /**
         * 参数设置
         *
         * @return
         */
        private void setParam() {
            // 清空参数
            mTts.setParameter(SpeechConstant.PARAMS, null);
            // 引擎类型 网络
            mTts.setParameter(SpeechConstant.ENGINE_TYPE, SpeechConstant.TYPE_CLOUD);
            // 设置发音人
            mTts.setParameter(SpeechConstant.VOICE_NAME, COLOUD_VOICERS_VALUE[0]);
            // 设置语速
            mTts.setParameter(SpeechConstant.SPEED, "50");
            // 设置音调
            mTts.setParameter(SpeechConstant.PITCH, "50");
            // 设置音量
            mTts.setParameter(SpeechConstant.VOLUME, "100");
            // 设置播放器音频流类型
            mTts.setParameter(SpeechConstant.STREAM_TYPE, "3");
            // mTts.setParameter(SpeechConstant.TTS_AUDIO_PATH, Environment.getExternalStorageDirectory() + "/KRobot/wavaudio.pcm");
            // 背景音乐  1有 0 无
            // mTts.setParameter("bgs", "1");
        }
}
```
