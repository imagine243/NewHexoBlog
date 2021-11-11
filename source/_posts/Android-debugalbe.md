title: Android中debug和release区分
date: 2015-10-13 17:46:23
tags: Android
tags: log
categories : Android
---

### Android中debug和release区分

在所有的软件项目中都有debug和release的区分
之前android都是通过自己手写一个boolean的变量分辨
现在发现android会在gen下自动生成BuildConfig,其中的DEBUG变量也是自动生成的。
DEBUG在平时调试是true，在签名打包后是false；


根据这个DEBUG添加了Log类

	public class TDLog {
		
		private static String TAG = "TDLog";
		
		public static void v(String tag, String msg) {
			if (BuildConfig.DEBUG) {
				Log.v(tag, msg);
			}
		}
		
		public static void i(String tag, String msg) {
			if (BuildConfig.DEBUG) {
				Log.i(tag, msg);
			}
		}
		
		public static void d(String tag, String msg) {
			if (BuildConfig.DEBUG) {
				Log.d(tag, msg);
			}
		}
		
		public static void w(String tag, String msg) {
			if (BuildConfig.DEBUG) {
				Log.w(tag, msg);
			}
		}
		
		public static void e(String tag, String msg) {
			if (BuildConfig.DEBUG) {
				Log.e(tag, msg);
			}
		}
		
		public static void assertTrue(Boolean isTrue, String msg)
		{
			if (BuildConfig.DEBUG) {
				if (isTrue) {
	//				Log.v(TAG, msg);
				}else {
					Log.e(TAG, msg);
					throw new RuntimeException(msg);
				}
				
			}
		}
	}