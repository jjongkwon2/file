# Flavor

### Flavor란 ?
소스코드는 대부분 같으나 특정 부분을 다르게 구현해야할 경우 유용하게 쓰인다.<br>
예를들어 앱이름, 아이콘을 달리해야하거나 유료앱 or 무료앱을 만들어야 할 경우(광고차이?) <br>
고객용 or 관리자용 or 업체용 <br>

### 사용방법
1. app의 build.gradle에 productFlacors 추가 ( 무료 or 유료 )
``` java
android {
    ...
    flavorDimensions 'tier'
    productFlavors {
        free {
            applicationIdSuffix ".free"
            versionCode 1
            versionName "1.0.0"
            dimension 'tier'
            buildConfigField 'boolean', 'IS_FREE', "true"
            manifestPlaceholders = [ appLabel: "Flavor(Free)" ]
        }

        paid {
            applicationIdSuffix ".paid"
            versionCode 2
            versionName "1.0.1"
            dimension 'tier'
            buildConfigField 'boolean', 'IS_FREE', "false"
            manifestPlaceholders = [ appLabel: "Flavor(Paid)" ]
        }
    }
}
```
> applicationIdSuffix가 있으면 기존의 applicationId 뒤에 설정한 아이디가 붙는다. <br>
> com.yjk.test.free <br>
> com.yjk.test.paid <br>
> buildConfigField를 사용하용하여 무료와 유료를 나눌 수 있다.

  ``` java
    if(BuildConfig.IS_FREE){
      // 무료앱
    }else{
      // 유료앱
    }
  ```
> manifestPlaceholders를 사용하여 앱 이름을 달리할 수 있다.

  ``` xml
  <application
      android:allowBackup="true"
      android:icon="@mipmap/ic_launcher"
      android:label="${appLabel}"
      <!-- here --!>
      android:supportsRtl="true"
      android:theme="@style/AppTheme">
      <activity android:name=".MainActivity">
          <intent-filter>
              <action android:name="android.intent.action.MAIN"/>

              <category android:name="android.intent.category.LAUNCHER"/>
          </intent-filter>
      </activity>
  </application>
  ```
