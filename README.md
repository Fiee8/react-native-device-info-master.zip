反应本机设备信息
npm 版本 npm 总下载量 npm 每月下载量 npm 每周下载量

React Native的设备信息。

目录
安装
链接
用法
API
钩子和事件
故障排除
发行说明
react-native-dom / react-native-web
v6 到 v7 升级
您的 iOS Podfile 需要至少升级到 iOS 10。此模块的 v7 不再支持 iOS9。

安装
使用 npm：

npm install --save react-native-device-info
或使用纱线：

yarn add react-native-device-info
保卫
如果您想使用 Install Referrer 跟踪，您需要将此配置添加到您的 Proguard 配置中

-keepclassmembers class com.android.installreferrer.api.** {
  *;
}
如果您在发布 apk 时遇到 hasGms() 问题，请将以下规则添加到您的 Proguard 配置中

-keep class com.google.android.gms.common.** {*;}
AndroidX 支持
此模块默认为 AndroidX，您应该在android/build.gradle文件的“ext”块中配置与此类似的库版本

安卓
如果您需要非 AndroidX，则需要以反向模式使用 jetifier 包，该包提供的文档。

链接
本地模块中的链接对于新的 react-native 开发人员来说是一个常见的麻烦来源，导致诸如“RNDeviceInfo 为空”等错误。因此实现了自动链接，并且应该在您的项目中使用它。

所有平台都支持自动链接（甚至是 React native >= 0.63 上的窗口！）

以前的版本需要手动链接。这些以前的 react-native 版本不提供支持，但如果您愿意，可以参考此 README 的旧版本。升级到现代版本的 react-native。如果需要，请使用upgrade-helperInternet 上的工具。

用法
import DeviceInfo from 'react-native-device-info';

// or ES6+ destructured imports

import { getUniqueId, getManufacturer } from 'react-native-device-info';
API
请注意，许多 API 是特定于平台的。如果平台没有实现，那么您将收到的“默认”返回值是"unknown"字符串、-1数字和false布尔值。数组和对象将为空（[]和{}分别）。

大多数 API 返回一个 Promise，但也有一个相应的 API 以Sync同步运行。例如，您可能更喜欢isCameraPresentSync()在应用引导期间调用，以避免在应用启动的第一部分进行异步调用。

此存储库中的示例应用程序显示了每个 API 的示例用法，如果您有任何问题，请咨询示例应用程序，如果您认为您发现问题，请确保您可以在报告之前使用示例应用程序重现它，谢谢。

方法	返回类型	iOS	安卓	视窗	网络
获取AndroidId()	Promise<string>	❌	✅	❌	❌
getApiLevel()	Promise<number>	❌	✅	❌	❌
获取应用程序名称（）	string	✅	✅	✅	❌
getAvailableLocationProviders()	Promise<Object>	✅	✅	❌	❌
getBaseOs()	Promise<string>	❌	✅	✅	✅
获取BuildId()	Promise<string>	✅	✅	✅	❌
获取电池电量（）	Promise<number>	✅	✅	✅	✅
获取引导加载程序（）	Promise<string>	❌	✅	❌	❌
获得品牌（）	string	✅	✅	✅	❌
getBuildNumber()	string	✅	✅	✅	❌
getBundleId()	string	✅	✅	✅	❌
isCameraPresent()	Promise<boolean>	❌	✅	✅	✅
获取运营商（）	Promise<string>	✅	✅	❌	❌
获取代号（）	Promise<string>	❌	✅	❌	❌
获取设备（）	Promise<string>	❌	✅	❌	❌
获取设备ID()	string	✅	✅	✅	❌
获取设备类型（）	string	✅	✅	❌	❌
获取显示（）	Promise<string>	❌	✅	❌	❌
获取设备名称（）	Promise<string>	✅	✅	✅	❌
获取设备令牌（）	Promise<string>	✅	❌	❌	❌
获取首次安装时间（）	Promise<number>	❌	✅	✅	❌
获取指纹（）	Promise<string>	❌	✅	❌	❌
获取字体缩放（）	Promise<number>	✅	✅	✅	❌
获取FreeDiskStorage()	Promise<number>	✅	✅	✅	✅
getFreeDiskStorageOld()	Promise<number>	✅	✅	✅	✅
获取硬件（）	Promise<string>	❌	✅	❌	❌
获取主机（）	Promise<string>	❌	✅	❌	❌
获取IP地址（）	Promise<string>	✅	✅	✅	❌
获取增量（）	Promise<string>	❌	✅	❌	❌
getInstallerPackageName()	Promise<string>	✅	✅	✅	❌
getInstallReferrer()	Promise<string>	❌	✅	✅	✅
getInstanceId()	Promise<string>	❌	✅	❌	❌
获取最后更新时间（）	Promise<number>	❌	✅	❌	❌
获取Mac地址（）	Promise<string>	✅	✅	❌	❌
获取制造商（）	Promise<string>	✅	✅	✅	❌
获取最大内存（）	Promise<number>	❌	✅	✅	✅
获取模型（）	string	✅	✅	✅	❌
获取电话号码（）	Promise<string>	❌	✅	❌	❌
获取电源状态（）	Promise<object>	✅	✅	✅	✅
获取产品（）	Promise<string>	❌	✅	❌	❌
getPreviewSdkInt()	Promise<number>	❌	✅	❌	❌
获取可读版本（）	string	✅	✅	✅	❌
获取序列号（）	Promise<string>	❌	✅	✅	❌
获取安全补丁（）	Promise<string>	❌	✅	❌	❌
getSystemAvailableFeatures()	Promise<string[]>	❌	✅	❌	❌
获取系统名称（）	string	✅	✅	✅	❌
获取系统版本（）	string	✅	✅	✅	❌
获取标签（）	Promise<string>	❌	✅	❌	❌
获取类型（）	Promise<string>	❌	✅	❌	❌
getTotalDiskCapacity()	Promise<number>	✅	✅	✅	✅
getTotalDiskCapacityOld()	Promise<number>	✅	✅	✅	✅
总内存（）	Promise<number>	✅	✅	❌	✅
getUniqueId()	Promise<string>	✅	✅	✅	❌
getUsedMemory()	Promise<number>	✅	✅	✅	✅
获取用户代理（）	Promise<string>	✅	✅	❌	✅
获取版本（）	string	✅	✅	✅	❌
获取亮度（）	Promise<number>	✅	❌	❌	❌
有Gms()	Promise<boolean>	❌	✅	❌	❌
有Hms()	Promise<boolean>	❌	✅	❌	❌
有缺口（）	boolean	✅	✅	✅	❌
有系统功能（）	Promise<boolean>	❌	✅	❌	❌
isAirplaneMode()	Promise<boolean>	❌	✅	❌	✅
是电池充电（）	Promise<boolean>	✅	✅	✅	✅
模拟器（）	Promise<boolean>	✅	✅	✅	❌
isKeyboardConnected()	Promise<bool>	❌	❌	✅	❌
是风景（）	Promise<boolean>	✅	✅	✅	❌
isLocationEnabled()	Promise<boolean>	✅	✅	❌	✅
isMouseConnected()	Promise<bool>	❌	❌	✅	❌
isHeadphonesConnected()	Promise<boolean>	✅	✅	❌	❌
isPinOrFingerprintSet()	Promise<boolean>	✅	✅	✅	❌
isTablet()	boolean	✅	✅	✅	❌
isTabletMode()	Promise<bool>	❌	❌	✅	❌
支持32BitAbis()	Promise<string[]>	❌	✅	❌	❌
支持64BitAbis()	Promise<string[]>	❌	✅	❌	❌
支持Abis()	Promise<string[]>	✅	✅	✅	❌
同步唯一 ID()	Promise<string>	✅	❌	❌	❌
getApiLevel()
获取 API 级别。

例子
DeviceInfo.getApiLevel().then((apiLevel) => {
  // iOS: ?
  // Android: 25
  // Windows: ?
});
笔记
查看API 级别

获取AndroidId()
获取 ANDROID_ID。请参阅API 文档以了解适当的用途。

例子
DeviceInfo.getAndroidId().then((androidId) => {
  // androidId here
});
获取应用程序名称（）
获取应用程序名称。

例子
let appName = DeviceInfo.getApplicationName();
// AwesomeApp
getBaseOs()
构建产品所基于的基本操作系统。

例子
DeviceInfo.getBaseOs().then((baseOs) => {
  // "Windows", "Android" etc
});
获取电池电量（）
获取设备的电池电量，作为介于 0 和 1 之间的浮点数。

例子
DeviceInfo.getBatteryLevel().then((batteryLevel) => {
  // 0.759999
});
笔记
为了能够获得实际的电池电量，请为应用程序启用电池监控模式。添加此代码：

[UIDevice currentDevice].batteryMonitoringEnabled = true;
到 AppDelegate.m 应用程序：didFinishLaunchingWithOptions：

在 iOS 模拟器上返回 -1

获取引导加载程序（）
系统引导加载程序版本号。

例子
DeviceInfo.getBootloader().then((bootloader) => {
  // "mw8998-002.0069.00"
});
获得品牌（）
获取设备品牌。

例子
let brand = DeviceInfo.getBrand();
// iOS: "Apple"
// Android: "xiaomi"
// Windows: ?
getBuildNumber()
获取应用程序内部版本号。

例子
let buildNumber = DeviceInfo.getBuildNumber();
// iOS: "89"
// Android: "4"
// Windows: ?
getBundleId()
获取应用程序包标识符。

例子
let bundleId = DeviceInfo.getBundleId();
// "com.example.AwesomeApp"
isCameraPresent()
告诉设备现在是否有任何摄像头。

例子
DeviceInfo.isCameraPresent()
  .then((isCameraPresent) => {
    // true or false
  })
  .catch((cameraAccessException) => {
    // is thrown if a camera device could not be queried or opened by the CameraManager on Android
  });
笔记
支持热添加/移除摄像头。
返回相机物理存在的状态。如果相机存在但您的应用没有使用它的权限，isCameraPresent 仍将返回 true
获取运营商（）
获取运营商名称（网络运营商）。

例子
DeviceInfo.getCarrier().then((carrier) => {
  // "SOFTBANK"
});
获取代号（）
当前开发代号，或者如果这是发布版本，则为字符串“REL”。

例子
DeviceInfo.getCodename().then((codename) => {
  // "REL"
});
获取设备（）
工业设计的名称。

例子
DeviceInfo.getDevice().then((device) => {
  // "walleye"
});
获取设备ID()
获取设备 ID。

例子
let deviceId = DeviceInfo.getDeviceId();
// iOS: "iPhone7,2"
// Android: "goldfish"
// Windows: "Y3R94UC#AC4"
获取显示（）
用于向用户显示的构建 ID 字符串。

例子
DeviceInfo.getDisplay().then((display) => {
  // "OPM2.171026.006.G1"
});
获取设备名称（）
获取设备名称。

例子
DeviceInfo.getDeviceName().then((deviceName) => {
  // iOS: "Becca's iPhone 6"
  // Android: ?
  // Windows: ?
});
这曾经需要 android.permission.BLUETOOTH 但 v3 中的新实现不需要它。如果你有这个 API，你可以从你的 AndroidManifest.xml 中删除它。

获取设备令牌（）
获取设备令牌（请参阅DeviceCheck）。仅适用于真实设备上的 iOS 11.0+。当不支持 getDeviceToken 时，这将拒绝承诺，请注意异常处理。

例子
DeviceInfo.getDeviceToken().then((deviceToken) => {
  // iOS: "a2Jqsd0kanz..."
});
获取首次安装时间（）
获取应用程序首次安装的时间，以毫秒为单位。

例子
DeviceInfo.getFirstInstallTime().then((firstInstallTime) => {
  // Android: 1517681764528
});
获取指纹（）
唯一标识此构建的字符串。

例子
DeviceInfo.getFingerprint().then((fingerprint) => {
  // "google/walleye/walleye:8.1.0/OPM2.171026.006.G1/4820017:user/release-keys"
});
获取字体缩放（）
获取设备字体比例。字体比例是当前系统字体与“正常”字体大小的比例，因此如果普通文本为 10pt，而系统字体当前为 15pt，则字体比例为 1.5 这可用于确定是否已设置可访问性针对设备进行了更改；如果字体比例明显更大（> 2.0），您可能需要重新布局某些视图

例子
DeviceInfo.getFontScale().then((fontScale) => {
  // 1.2
});
获取FreeDiskStorage()
获取可用存储大小（以字节为单位）的方法，同时考虑了根文件系统和数据文件系统的计算。

例子
DeviceInfo.getFreeDiskStorage().then((freeDiskStorage) => {
  // Android: 17179869184
  // iOS: 17179869184
});
笔记
此方法用于 Android 的 API 在v6.0.0中已更改。旧版本已在下面维护为getFreeDiskStorageOld(). 在 iOS 上，getFreeDiskStorage()并getFreeDiskStorageOld()返回相同的值。

getFreeDiskStorageOld()
获取可用存储大小的方法的旧实现，以字节为单位。

例子
DeviceInfo.getFreeDiskStorageOld().then((freeDiskStorage) => {
  // Android: 17179869184
  // iOS: 17179869184
});
笔记
来自developer.android.com：

此方法在 API 级别 29 中已弃用。

返回主要的共享/外部存储目录。

注意：不要被这里的“外部”这个词弄糊涂了。最好将此目录视为媒体/共享存储。它是一个文件系统，可以保存相对大量的数据，并且在所有应用程序之间共享（不强制执行权限）。传统上这是一张 SD 卡，但它也可以作为设备中的内置存储实现，与受保护的内部存储不同，并且可以作为文件系统安装在计算机上。

获取硬件（）
硬件的名称（来自内核命令行或 /proc）。

例子
DeviceInfo.getHardware().then(hardware => {
  // "walleye"
};
获取主机（）
主机名

例子
DeviceInfo.getHost().then((host) => {
  // "wprd10.hot.corp.google.com"
});
获取IP地址（）
不推荐使用获取设备当前 IP 地址。（仅限 wifi）切换到react-native-netinfo/netinfo或react-native-network-info

例子
DeviceInfo.getIpAddress().then((ip) => {
  // "92.168.32.44"
});
安卓权限
android.permission.ACCESS_WIFI_STATE
笔记
在 0.22.0 中添加了对 iOS 的支持

获取增量（）
底层源代码控制用于表示此构建的内部值。

例子
DeviceInfo.getIncremental().then((incremental) => {
  // "4820017"
});
getInstallerPackageName()
底层源代码控制用于表示此构建的内部值。

例子
DeviceInfo.getInstallerPackageName().then((installerPackageName) => {
  // Play Store: "com.android.vending"
  // Amazon: "com.amazon.venezia"
  // Samsung App Store: "com.sec.android.app.samsungapps"
  // iOS: "AppStore", "TestFlight", "Other"
});
getInstallReferrer()
在应用程序安装时获取引用者字符串。

例子
DeviceInfo.getInstallReferrer().then((installReferrer) => {
  // If the app was installed from https://play.google.com/store/apps/details?id=com.myapp&referrer=my_install_referrer
  // the result will be "my_install_referrer"
});
getInstanceId()
获取应用程序实例 ID。

例子
DeviceInfo.getInstanceId().then((instanceId) => {
  // Android: ?
});
笔记
请参阅https://developers.google.com/instance-id/

获取最后更新时间（）
获取应用程序上次更新的时间，以毫秒为单位。

例子
DeviceInfo.getLastUpdateTime().then((lastUpdateTime) => {
  // Android: 1517681764992
});
获取Mac地址（）
获取网络适配器 MAC 地址。

例子
DeviceInfo.getMacAddress().then((mac) => {
  // "E5:12:D8:E5:69:97"
});
安卓权限
android.permission.ACCESS_WIFI_STATE
笔记
iOS：此方法始终返回“02:00:00:00:00:00”，因为自 iOS 7 起已禁用检索 MAC 地址

获取制造商（）
获取设备制造商。

例子
DeviceInfo.getManufacturer().then((manufacturer) => {
  // iOS: "Apple"
  // Android: "Google"
  // Windows: ?
});
获取最大内存（）
返回 VM 将尝试使用的最大内存量（以字节为单位）。

例子
DeviceInfo.getMaxMemory().then((maxMemory) => {
  // 402653183
});
获取模型（）
获取设备型号。

iOS 警告：设备名称列表由社区维护，可能会滞后于新设备。建议使用它，getDeviceId()因为它更可靠并且始终与新的 iOS 设备保持同步。我们确实接受将新 iOS 设备添加到带有设备名称的列表的拉取请求。

例子
let model = DeviceInfo.getModel();
// iOS: ?
// Android: ?
// Windows: ?
获取电话号码（）
获取设备电话号码。

例子
DeviceInfo.getPhoneNumber().then((phoneNumber) => {
  // Android: null return: no permission, empty string: unprogrammed or empty SIM1, e.g. "+15555215558": normal return value
});
安卓权限
有关所需权限的信息，请参阅Android 文档，具体取决于您支持的 Android 版本。阅读下面的注释以获取更多信息。

笔记
这可以undefined在某些情况下返回，不应依赖。SO条目上的主题。

如果上述权限不起作用，您可以尝试使用android.permission.READ_SMS. 但是，这不在 Android 文档中。如果您支持 Android 10 及更低版本：android.permission.READ_PHONE_STATE。如果您支持 Android 11 及更高版本：android.permission.READ_SMS

获取电源状态（）
获取设备的电源状态，包括电池电量、是否插入以及系统当前是否在低功耗模式下运行。如果未启用电池监控或在模拟器上尝试（无法监控），则在 iOS 上显示警告

例子
DeviceInfo.getPowerState().then((state) => {
  // {
  //   batteryLevel: 0.759999,
  //   batteryState: 'unplugged',
  //   lowPowerMode: false,
  // }
});
获取产品（）
整体产品的名称。

例子
DeviceInfo.getProduct().then((product) => {
  // "walleye"
});
getPreviewSdkInt()
预发布 SDK 的开发者预览版。

例子
DeviceInfo.getPreviewSdkInt().then((previewSdkInt) => {
  // 0
});
获取可读版本（）
获取应用程序可读版本（与 getVersion() + '.' + getBuildNumber() 相同）

例子
let readableVersion = DeviceInfo.getReadableVersion();
// iOS: 1.0.1.32
// Android: 1.0.1.234
// Windows: ?
获取序列号（）
获取设备序列号。几乎在所有情况下都是“未知”的，除非你有一个特权应用程序并且你知道你在做什么。

例子
DeviceInfo.getSerialNumber().then((serialNumber) => {
  // iOS: unknown
  // Android: ? (maybe a serial number, if your app is privileged)
  // Windows: ? (a serial number, if your app has the "capability smbios")
});
笔记
能力 smbios
如果您想在 Windows 中使用此方法，您必须在您的应用程序中添加 smbios 功能。请按照此文档在清单文件中添加功能。

获取安全补丁（）
用户可见的安全补丁级别。

例子
DeviceInfo.getSecurityPatch().then((securityPatch) => {
  // "2018-07-05"
});
获取系统名称（）
获取设备操作系统名称。

例子
let systemName = DeviceInfo.getSystemName();
// iOS: "iOS" on newer iOS devices "iPhone OS" on older devices (including older iPad models), "iPadOS" for iPads using iPadOS 15.0 or higher.
// Android: "Android"
// Windows: ?
获取系统版本（）
获取设备操作系统版本。

例子
let systemVersion = DeviceInfo.getSystemVersion();
// iOS: "11.0"
// Android: "7.1.1"
// Windows: ?
获取BuildId()
获取操作系统的内部版本号。

例子
DeviceInfo.getBuildId().then((buildId) => {
  // iOS: "12A269"
  // tvOS: not available
  // Android: "13D15"
  // Windows: not available
});
获取标签（）
描述构建的逗号分隔标签。

例子
DeviceInfo.getTags().then((tags) => {
  // "release-keys, unsigned, debug",
});
获取类型（）
构建类型。

例子
DeviceInfo.getType().then((type) => {
  // "user", "eng"
});
getTotalDiskCapacity()
获取完整磁盘存储大小（以字节为单位）的方法，同时考虑了根文件系统和数据文件系统的计算。

例子
DeviceInfo.getTotalDiskCapacity().then((capacity) => {
  // Android: 17179869184
  // iOS: 17179869184
});
笔记
此方法用于 Android 的 API 在v6.0.0中已更改。旧版本已在下面维护为getTotalDiskCapacityOld(). 在 iOS 上，getTotalDiskCapacity()并getTotalDiskCapacityOld()返回相同的值。

getTotalDiskCapacityOld()
获取完整磁盘存储大小的方法的旧实现，以字节为单位。

例子
DeviceInfo.getTotalDiskCapacityOld().then((capacity) => {
  // Android: 17179869184
  // iOS: 17179869184
});
总内存（）
获取设备总内存，以字节为单位。

例子
DeviceInfo.getTotalMemory().then((totalMemory) => {
  // 1995018240
});
getUniqueId()
此标识符在某些应用商店（例如华为或 Google Play）中被视为敏感信息，如果未经用户同意或用于未经批准的目的，可能会导致您的应用被删除或拒绝。有关更多信息，请参阅商店政策（请参阅下面的注释）。

获取设备唯一 ID。在 Android 上，它目前与getAndroidId()此模块中的相同。在 iOS 上，它使用DeviceUIDuid 标识符。在 Windows 上，它使用Windows.Security.ExchangeActiveSyncProvisioning.EasClientDeviceInformation.id.

例子
DeviceInfo.getUniqueId().then((uniqueId) => {
// iOS: "FCDBD8EF-62FC-4ECB-B2F5-92C9E79AC7F9"
// Android: "dd96dec43fb81c97"
// Windows: "{2cf7cb3c-da7a-d508-0d7f-696bb51185b4}"
});
笔记
iOS：IDFV如果 IDFV 不可用，则为随机字符串。一旦生成了 UID，它就会存储在 iOS Keychain 和 NSUserDefaults 中。因此，即使您删除应用程序或重置 IDFV，它也会保持不变。您可以仔细考虑它是一个持久的、交叉安装的唯一 ID。只有在有人手动覆盖 Keychain/NSUserDefaults 中的值或 Apple 会更改 Keychain 和 NSUserDefaults 实现的情况下才能更改它。注意：IDFV 是使用您的捆绑标识符计算的，因此在应用扩展中会有所不同。
android：在 Oreo 之前，一旦您设置了手机，此 id ( ANDROID_ID ) 将始终相同。
android：Google Play 政策，请参阅“永久设备标识符”。华为 - AppGallery 审核指南参见“永久设备标识符”和“获得用户同意”。
同步唯一 ID()
此方法适用于 iOS。

这将 uniqueId 与随机字符串同步IDFV或设置新的随机字符串。

在 iOS 上，它使用DeviceUIDuid 标识符。在其他平台上，它只是getUniqueId()在这个模块中调用。

例子
DeviceInfo.syncUniqueId().then((uniqueId) => {
  // iOS: "FCDBD8EF-62FC-4ECB-B2F5-92C9E79AC7F9"
  // Android: "dd96dec43fb81c97"
  // Windows: ?
});
笔记
如果用户将数据从一台 iOS 设备移动或恢复到第二台 iOS 设备，那么他将拥有两个uniqueId在 Keychain/NSUserDefaults 中相同的不同设备。用户可以syncUniqueId()在新的 iOS 设备上通话。这将更新他的uniqueIdfromIDFV或随机字符串。
getUsedMemory()
获取应用程序内存使用情况，以字节为单位。

⚠️ 来自 Android 文档的注释。

注意：此方法仅用于调试或构建面向用户的流程管理 UI。

例子
DeviceInfo.getUsedMemory().then((usedMemory) => {
  // 23452345
});
获取用户代理（）
获取设备用户代理。

例子
DeviceInfo.getUserAgent().then((userAgent) => {
  // iOS: "Mozilla/5.0 (iPhone; CPU iPhone OS 9_1 like Mac OS X) AppleWebKit/601.1.46 (KHTML, like Gecko) Version/9.0 Mobile/13B143"
  // tvOS: not available
  // Android: ?
  // Windows: ?
});
获取版本（）
获取应用程序版本。考虑到版本字符串是设备/操作系统格式的，并且可以包含任何其他数据（例如内部版本号等）。如果您想确定版本格式，可以使用正则表达式来获取返回的版本字符串的所需部分。

例子
let version = DeviceInfo.getVersion();
// iOS: "1.0"
// Android: "1.0" or "1.0.2-alpha.12"
// Windows: ?
isAirplaneMode()
告知设备是否处于飞行模式。

例子
DeviceInfo.isAirplaneMode().then((airplaneModeOn) => {
  // false
});
笔记
这仅在远程调试器被禁用时才有效。
是电池充电（）
告诉电池当前是否正在充电。

例子
DeviceInfo.isBatteryCharging().then((isCharging) => {
  // true or false
});
模拟器（）
判断应用程序是否在模拟器中运行。

例子
DeviceInfo.isEmulator().then((isEmulator) => {
  // false
});
isKeyboardConnected()
告诉设备是否连接了键盘。

例子
let isKeyboardConnected = DeviceInfo.isKeyboardConnected();
// true
isPinOrFingerprintSet()
告知是否为设备设置了 PIN 码或指纹。

例子
DeviceInfo.isPinOrFingerprintSet().then((isPinOrFingerprintSet) => {
  if (!isPinOrFingerprintSet) {
    // ...
  }
});
isTablet()
判断设备是否为平板电脑。

例子
let isTablet = DeviceInfo.isTablet();
// true
isTabletMode()
告知设备是否处于平板电脑模式。

例子
let isTabletMode = DeviceInfo.isTabletMode();
// true
是风景（）
告知设备当前是否处于横向模式。

例子
DeviceInfo.isLandscape().then((isLandscape) => {
  // true
});
isMouseConnected()
告诉设备是否连接了鼠标。

例子
let isMouseConnected = DeviceInfo.isMouseConnected();
// true
有Gms()
告知设备是否支持 Google 移动服务。

例子
DeviceInfo.hasGms().then((hasGms) => {
  // true
});
有Hms()
告知设备是否支持华为移动服务。

例子
DeviceInfo.hasHms().then((hasHms) => {
  // true
});
有缺口（）
告诉设备是否有缺口。

例子
let hasNotch = DeviceInfo.hasNotch();
// true
获取设备类型（）
将设备的类型作为字符串返回，该类型将是以下之一：

Handset
Tablet
Tv
Desktop
GamingConsole
unknown
例子
let type = DeviceInfo.getDeviceType();
// 'Handset'
支持32BitAbis()
此设备支持的 32 位 ABI 的有序列表。

例子
DeviceInfo.supported32BitAbis().then((abis) => {
  // ["armeabi-v7a", "armeabi"]
});
支持64BitAbis()
此设备支持的 64 位 ABI 的有序列表。

例子
DeviceInfo.supported64BitAbis().then((abis) => {
  // ["arm64-v8a"]
});
支持Abis()
返回支持的处理器架构版本列表

例子
DeviceInfo.supportedAbis().then((abis) => {
  // [ "arm64 v8", "Intel x86-64h Haswell", "arm64-v8a", "armeabi-v7a", "armeabi", "win_x86", "win_arm", "win_x64" ]
});
hasSystemFeature(功能)
告知设备是否具有特定的系统功能。

例子
DeviceInfo.hasSystemFeature('amazon.hardware.fire_tv').then((hasFeature) => {
  // true or false
});
getSystemAvailableFeatures()
返回 Android 上可用系统功能的列表。

例子
DeviceInfo.getSystemAvailableFeatures().then((features) => {
  // ["android.software.backup", "android.hardware.screen.landscape", "android.hardware.wifi", ...]
});
isLocationEnabled()
告知设备是否在设备级别关闭了位置服务（与特定于应用程序的权限无关）

例子
DeviceInfo.isLocationEnabled().then((enabled) => {
  // true or false
});
isHeadphonesConnected()
判断设备是否连接到有线耳机或蓝牙耳机

例子
DeviceInfo.isHeadphonesConnected().then((enabled) => {
  // true or false
});
getAvailableLocationProviders()
返回特定于平台的boolean位置提供程序/服务的对象，无论它们当前是否可用，都带有值。

注意：此功能需要访问 Android 上的位置权限

安卓示例
DeviceInfo.getAvailableLocationProviders().then((providers) => {
  // {
  //   gps: true
  //   network: true
  //   passive: true
  // }
});
iOS 示例
DeviceInfo.getAvailableLocationProviders().then((providers) => {
  // {
  //   headingAvailable: false
  //   isRangingAvailable: false
  //   locationServicesEnabled: true
  //   significantLocationChangeMonitoringAvailable: true
  // }
});
获取亮度（）
获取设备主屏幕的当前亮度级别。目前仅限 iOS。返回一个介于 0.0 和 1.0 之间的数字，包括 0.0 和 1.0。

例子
DeviceInfo.getBrightness().then((brightness) => {
  // iOS: 0.6
});
钩子和事件
目前仅限 iOS 和 Android（电池/充电相关 API 的网络支持）。

useBatteryLevel 或 RNDeviceInfo_batteryLevelDidChange
当电池电量变化时触发；发送频率不超过每分钟一次。

例子
import { useBatteryLevel } from 'react-native-device-info';

const batteryLevel = useBatteryLevel(); // 0.759999

<Text>{batteryLevel}</Text>;
import { NativeEventEmitter, NativeModules } from 'react-native';
const deviceInfoEmitter = new NativeEventEmitter(NativeModules.RNDeviceInfo);

deviceInfoEmitter.addListener('RNDeviceInfo_batteryLevelDidChange', (level) => {
  // 0.759999
});
useBatteryLevelIsLow 或 RNDeviceInfo_batteryLevelIsLow
当电池电量下降被认为是低电量时触发

平台	百分比
iOS	20
安卓	15
网络	20
例子
import { useBatteryLevelIsLow } from 'react-native-device-info';

const batteryLevelIsLow = useBatteryLevelIsLow(); // 0.19

<Text>{batteryLevelIsLow}</Text>;
import { NativeEventEmitter, NativeModules } from 'react-native';
const deviceInfoEmitter = new NativeEventEmitter(NativeModules.RNDeviceInfo);

deviceInfoEmitter.addListener('RNDeviceInfo_batteryLevelIsLow', (level) => {
  // 0.19
});
usePowerState 或 RNDeviceInfo_powerStateDidChange
当电池状态改变时触发，例如当设备进入充电模式或拔出电源时。

例子
import { usePowerState } from 'react-native-device-info';

const powerState = usePowerState(); // 'charging'

<Text>{powerState}</Text>;
import { NativeEventEmitter, NativeModules } from 'react-native'
const deviceInfoEmitter = new NativeEventEmitter(NativeModules.RNDeviceInfo)

deviceInfoEmitter.addListener('RNDeviceInfo_powerStateDidChange', { batteryState } => {
  // 'charging'
});
使用首次安装时间
获取应用程序首次安装的时间，以毫秒为单位。

例子
import { useFirstInstallTime } from 'react-native-device-info';

const { loading, result } = useFirstInstallTime(); // { loading: true, result: 1517681764528}

<Text>{loading ? 'loading...' : result}</Text>;
使用设备名称
获取设备名称。

例子
import { useDeviceName } from 'react-native-device-info';

const { loading, result } = useDeviceName(); // { loading: true, result: "Becca's iPhone 6"}

<Text>{loading ? 'loading...' : result}</Text>;
使用HasSystemFeature
告知设备是否具有特定的系统功能。

例子
import { useHasSystemFeature } from 'react-native-device-info';

const { loading, result } = useHasSystemFeature('amazon.hardware.fire_tv'); // { loading: true, result: false }

<Text>{loading ? 'loading...' : result}</Text>;
使用IsEmulator
获取应用程序是否在模拟器中运行。

例子
import { useIsEmulator } from 'react-native-device-info';

const { loading, result } = useIsEmulator(); // { loading: true, result: false }

<Text>{loading ? 'loading...' : result}</Text>;
使用制造商
获取设备制造商。

例子
import { useManufacturer } from 'react-native-device-info';

const { loading, result } = useManufacturer(); // { loading: true, result: "Apple"}

<Text>{loading ? 'loading...' : result}</Text>;
使用是耳机已连接
告知设备是否连接到有线耳机或蓝牙耳机。

这个钩子订阅事件，RNDeviceInfo_headphoneConnectionDidChange并相应地更新result字段。

例子
import { useIsHeadphonesConnected } from 'react-native-device-info';

const { loading, result } = useIsHeadphonesConnected(); // { loading: true, result: false}

<Text>{loading ? 'loading...' : result}</Text>;
使用亮度
获取设备主屏幕的当前亮度级别。目前仅限 iOS。返回一个介于 0.0 和 1.0 之间的数字，包括 0.0 和 1.0。

这个钩子订阅事件，RNDeviceInfo_brightnessDidChange并相应地更新brightness字段。

例子
import { useBrightness } from 'react-native-device-info';

const brightness = useBrightness(); // 0.46578987897654567

<Text>{brightness}</Text>;
import { NativeEventEmitter, NativeModules } from 'react-native';

const deviceInfoEmitter = new NativeEventEmitter(NativeModules.RNDeviceInfo);

deviceInfoEmitter.addListener('RNDeviceInfo_brightnessDidChange', (brightness) => {
  // 0.46578987897654567
});
=======

本机互操作性
如果您需要从本机端检查设备类型，可以使用以下内容：

import com.learnium.resolver.DeviceTypeResolver

...
deviceTypeResolver = new DeviceTypeResolver(context);
...
//Check if the device is a Tablet:
if(deviceTypeResolver.isTablet){
  ...
}else{
  ...
}
故障排除
安装或使用react-native-device-info时，可能会遇到以下问题：

[android] - 无法合并 dex / 多个 dex 文件 / `com.google.android.gms` 的问题
[ios] - ld：找不到 -lRNDeviceInfo-tvOS 的库
[ios] - [NetworkInfo] 描述符查询返回错误：错误域 = NSCocoaErrorDomain 代码 = 4099 “与名为 com.apple.commcenter.coretelephony.xpc 的服务的连接无效。”
[ios] - 使用 CocoaPods 时的多个 React 版本“尝试要求‘react-native’，但有几个文件提供了这个模块”
[测试] - 使用此库时无法运行我的测试套件
[警告] - 我收到太多警告（电池状态等）
发行说明
请参阅CHANGELOG.md。

贡献
请参阅contributing guide.

反应原生dom
作为对开发人员的礼貌，这个库在 v0.21.6 中与react-native-dom和react-native-web兼容，提供了一个空的 polyfill 以避免破坏构建。

只有getUserAgent()会返回正确的值。所有其他 API 方法将返回其记录的返回类型的“空”值：0对于数字、''对于字符串、false对于布尔值。
