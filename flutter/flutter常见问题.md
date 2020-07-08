### AndroidX

[!] Your app isn't using AndroidX.

​    To avoid potential build failures, you can quickly migrate your app by following the steps on https://goo.gl/CP92wY.

在gradle.properties中添加如下代码即可

```
android.enableJetifier=true
android.useAndroidX=true
```

