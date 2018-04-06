# Gradle 속성

## app의 build.gradle
#### BuildType
개발 과정에 따라 debug, alpha, beta, release로 나누눈데
Android studio에서는 기본적으로 release의 빌드 타입을 생성한다. <br>
``` gradle
android {
    ...
    buildTypes {
        alpha {
            applicationIdSuffix '.alpha'
            debuggable true
            minifyEnabled false
        }
        beta {
            applicationIdSuffix '.beta'
            debuggable true
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
        release {
            applicationIdSuffix '.release'
            debuggable false
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
    ...
}
```
