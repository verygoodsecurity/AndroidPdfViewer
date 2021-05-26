![GitHub](https://img.shields.io/github/license/heartexlabs/label-studio?logo=heartex) 

# Android PdfViewer
PdfViewer - Library for displaying PDF documents on Android, with animations, gestures, zoom and double tap support. It is improved version of [AndroidPdfViewer](https://github.com/barteksc/AndroidPdfViewer) library for easy integration with VGS products for Android.

## Installation
Add to your application module build.gradle file:

`implementation 'com.github.barteksc:android-pdf-viewer:2.8.2'`

## ProGuard
If you are using ProGuard, add following rule to proguard config file:

```proguard
-keep class com.shockwave.**
```

## Possible questions
### Why resulting apk is so big?
Android PdfViewer depends on PdfiumAndroid, which is set of native libraries (almost 16 MB) for many architectures.
Apk must contain all this libraries to run on every device available on market.
Fortunately, Google Play allows us to upload multiple apks, e.g. one per every architecture.
There is good article on automatically splitting your application into multiple apks,
available [here](http://ph0b.com/android-studio-gradle-and-ndk-integration/).
Most important section is _Improving multiple APKs creation and versionCode handling with APK Splits_, but whole article is worth reading.
You only need to do this in your application, no need for forking PdfiumAndroid or so.

### Why I cannot open PDF from URL?
Downloading files is long running process which must be aware of Activity lifecycle, must support some configuration, 
data cleanup and caching, so creating such module will probably end up as new library.

### How can I show last opened page after configuration change?
You have to store current page number and then set it with `pdfView.defaultPage(page)`, refer to sample app
