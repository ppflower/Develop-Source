# Android设备信息

## Android 简单的设备信息获取
```
# begin build properties
# autogenerated by buildinfo.sh
ro.build.id=LMY47V
ro.build.display.id=N928Dt_CNMobileB_1.18
ro.build.sw_internal_version=N928Dt_Z78_CN_MSXPH1C500J118
ro.build.sw_outer_version=N928Dt_CNMobileB_1.18
ro.build.version.incremental=eng.jiangxiaojun.20150829.170221
ro.build.version.sdk=22
ro.build.version.codename=REL
ro.build.version.all_codenames=REL
ro.build.version.release=5.1.1
ro.build.date=Sat Aug 29 17:03:44 CST 2015
ro.build.date.utc=1440839024
ro.build.type=user
ro.build.user=jiangxiaojun
ro.build.host=hipad25
ro.build.tags=release-keys
ro.build.flavor=N928Dt-user
ro.product.model=ZTE N928Dt
ro.product.brand=ZTE
ro.product.name=N928Dt
ro.product.device=N928Dt
ro.product.board=msm8909
# ro.product.cpu.abi and ro.product.cpu.abi2 are obsolete,
# use ro.product.cpu.abilist instead.
ro.product.cpu.abi=armeabi-v7a
ro.build.display.dcc.version=N928Dt.user.V1.18.Rev14539.20150829
ro.build.display.software.id=N928Dt_Z78_CN_MSXPH1C500J118
ro.build.display.hardware.id=P1
ro.build.display.hardware=P1
ro.product.svn.info=14539
ro.product.cpu.abi2=armeabi
ro.product.cpu.abilist=armeabi-v7a,armeabi
ro.product.cpu.abilist32=armeabi-v7a,armeabi
ro.product.cpu.abilist64=
ro.product.manufacturer=ZTE
ro.product.locale.language=zh
ro.product.locale.region=CN
ro.wifi.channels=
ro.board.platform=msm8909
# ro.build.product is obsolete; use ro.product.device
ro.build.product=N928Dt
# Do not try to parse description, fingerprint, or thumbprint
ro.build.description=N928Dt-user 5.1.1 LMY47V eng.jiangxiaojun.20150829.170221 release-keys
ro.build.fingerprint=ZTE/N928Dt/N928Dt:5.1.1/LMY47V/jiangxiaojun08291703:user/release-keys
ro.build.characteristics=default
# end build properties
#
# from device/qcom/N928Dt/system.prop
#
#
# system.prop for msm8909
#
```

通过这些key我们就可以获取值，以获取系统sdk版本号为例 具体命令如下：

```
  adb shell getprop ro.build.version.sdk
  27
```

获取方法：
```
public static String getSystemProp(String key, String defVal) {
    try {
        Class clazz = Class.forName("android.os.SystemProperties");
        Method method = clazz.getMethod("get", String.class, String.class);
        Object object = method.invoke(null, key, defVal);
        return (String) object;
    } catch (Exception e) {
        e.printStackTrace();
    }
    return "null";
}

private static String getVerNumber() {
    String key = "ro.gn.gnznvernumber";
    return getSystemProp(key, "");
}
```