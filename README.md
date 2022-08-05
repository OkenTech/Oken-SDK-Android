
# What is the Oken SDK?

This is library you can you for tracking attention and comprehension during reading via frontal camera.

## Installing

### 1. Get api key
Please contact info@oken.tech to get your credentials.

### 2. Download latest build
Download latest AAR build from [https://github.com/OkenTech/Oken-SDK-Android/releases/](https://github.com/OkenTech/Oken-SDK-Android/releases/)  
And put it into your `app/libs` folder.


### 3. Set up your development environment
Add the required dependencies and client libraries to your app module:
```
dependencies {
    implementation files('libs/tech.oken-sdk.android-0.0.14-dev-debug.aar')
}
```

### 4. Set up api key
Put your api key in AndroidManifest.xml inside the `<applicatoin>` tag:
```
<manifest...
    <application...
        <meta-data android:name="oken_api_key"
            android:value="<OKEN_API_KEY>" />
```
### 5. Set up app permissions
```
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.CAMERA" />
<uses-feature android:name="android.hardware.camera.front" />
```
## Usage
Instantiate Oken SDK:
```
IOkenSdk okenSdk = new OkenSdk();
```
Initialize it. At this moment Oken SDK will ask for permissions:
```
okenSdk.init(activity, "<USER_UNIQUE_ID>");
```
And when permissions received call:
```
okenSdk.onRequestPermissionsResult(requestCode, permissions, grantResults)
```
### Open book
Initialize reading session:
```
IOkenSdk.IOkenBook book = okenSdk.bookOpened(bookUniqueId, view, lifecycleOwner);
```
And call methods when page was opened:
```
book.pageOpened(pageNum)
```
And closed:
```
book.pageClosed()
```
