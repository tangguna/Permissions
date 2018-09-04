# Permissions
Android权限管理，适配到Android O
### 配置
#### 在根构建中添加
     allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
#### 添加依赖关系
     dependencies {
	        implementation 'com.github.tangguna:Permissions:1.0.1'
	}
  
  
### 权限设置
#### 库中包含Android 6.0 以上需要动态添加的权限，在类Permisssion中包括一下权限：
    public static final String[] CALENDAR; //日历
    public static final String[] CAMERA; //摄像机
    public static final String[] CONTACTS; //联系人
    public static final String[] LOCATION; //位置
    public static final String[] MICROPHONE; //麦克风
    public static final String[] PHONE;//电话
    public static final String[] SENSORS;//传感器
    public static final String[] SMS;//短信
    public static final String[] STORAGE;//存储
    
###使用方式
#### 此库可以动态设置，支持在activity与fragment中配置，使用时调用方法：
      PermissionBuilder.needPermission(MainActivity.this, 20, Permission.STORAGE, new IPermissionsCallback() {
            @Override
            public void onPermissionSuccess(int i, String s) {
                Log.d("输出",s);
            }

            @Override
            public void onPermissionFailure(int i, String s) {
                Log.d("输出",s);
            }
        });
方法 needPermission(Activity activity, int requestCode, String[] permissions,IPermissionsCallback callback) 
参数requestCode为请求状态码，可以自己定义数值；permissions为请求权限，IPermissionsCallback为请求回调结果（成功或者失败）
可以根据回调返回参数String判断（成功返回授权成功，失败返回授权失败）