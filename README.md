# VideoPlsCytronSDK

[![CI Status](http://img.shields.io/travis/Zard1096/VideoPlsCytron.svg?style=flat)](https://travis-ci.org/Zard1096/VideoPlsCytron)
[![Version](https://img.shields.io/cocoapods/v/VideoPlsCytron.svg?style=flat)](http://cocoapods.org/pods/VideoPlsCytron)
[![License](https://img.shields.io/cocoapods/l/VideoPlsCytron.svg?style=flat)](http://cocoapods.org/pods/VideoPlsCytron)
[![Platform](https://img.shields.io/cocoapods/p/VideoPlsCytron.svg?style=flat)](http://cocoapods.org/pods/VideoPlsCytron)

## Example

To run the example project, clone the repo, and run `pod install` from the Example directory first.

## Requirements

## Installation

VideoPlsCytronSDK is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod "VideoPlsCytronSDK"
```

## Usage
##### 1. 引入头文件

  1)打开`*AppDelegate.m`(`*`代表你的工程名字)导入头文件:

  ```js
  #import <VideoPlsCytronSDK/VideoPlsCytronSDK.h>
  在didFinishLaunchingWithOptions方法中调用`VideoPlsCytronSDK.h`的 `setAppKey`方法来设置相应`appkey`,代码如下:

  - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
  // "Nktcz4C5-" 此处替换为自己的APPKEY
  [VideoPlsCytronSDK setAppKey:@"Nktcz4C5-"]; return YES;
  }
  ```

  2)添加实现代码

  ```js
  在需要用到互动层的地方添加头文件:
  #import < VideoPlsCytronSDK/VPCytronView.h>
  #import < VideoPlsCytronSDK/VPCytronNotificationNameSet.h>

  在播放器层上面添加 VPCytronView 代码如下:
  VPCytronView cytronView = [[VPCytronView alloc] initWithFrame:player.view.boun ds videoIdentifier:identifier videoType:videotype videoTitle:@”titleString” isLive:NO];
  [self.player.view addSubview: cytronView];

  接着，设置互动层显示区域，代码如下所示:
  (注:frame 与播放器实际位置一致,videoRect 与视频实际显示区域一致,isFullScreen 控制 全屏小、窗口，全屏显示互动。参数根据需要自行调整，可参考头文件)
  [self. cytronView updateFrame:self.view.bounds videoRect:self.view.bounds isFullScreen:YES];

  然后，播放点播视频时必须开启一个计时器持续传递给互动层当前的播放时间传 递时间单位为毫秒(若为秒请自行转换)，直播时使用 MQTT 所以不需要设置， 代码如下:

  self.playtimer = [NSTimer scheduledTimerWithTimeInterval:0.03 target:self selector:@selector(updateCurrentTime) userInfo:nil repeats:YES];

  updateCurrentTime 方法里设置时间，代码如下:
  -(void)updateCurrentTime {
  NSTimeInterval time = self. player.currentPlaybackTime * 1000;
  [self. cytronView updateCurrentPlaybackTime:time];
  }

  最后，调用 startLoading 方法，如下: (注:所有参数必须放在 startLoading 之前设置)
  [cytronView startLoading];
  当接收到 VPCytronLoadCompleteNotification 的通知时表示互动层加载完 成，可以开始显示互动。当接收到 VPCytronViewLoadErrorNotification 通 知时，说明互动层加载失败，请根据错误信息，自行查找原因。 播放结束后，需调用 stop 方法来确保内存能够正确释放。
  [cytronView stop];

  ```
##### 2.注意事项
  ```
  1. videoIdentifier参数为视频的标识(原url),可以用url作为参数 或 使用拼接 ID的方式来识别(前提为与pc对接并通过)。
  2.文档中的代码仅供参考，实际参数请根据项目自行配置。
  3.互动层会向下层 view 发放点击手势，不用担心控制器界面会被阻挡手势。
  4.请将互动层置于合适位置以防阻挡手势。
  5.最佳位置为加载控制栏的下方,并且于手势层的上方,请不要将 cytronView 放 入包含手势操作的 View 中。
  6.请使用 Xcode5 及以上版本，SDK 目前支持系统为 iOS7 以上。
  7.旧版本互动层 SDK 只可以用旧版本 video++后台打点，Cytron 是新版本互 动层，新版本 SDK 只可以用新版本 videoOS 后台打点，新版本与旧版本后台 热点数据不互通。
  ```

## Author

Zard1096, mr.zardqi@gmail.com		
Lishaoshuai, lishaoshuai1990@gmail.com	 
Bill, fuleiac@gmail.com

## License

VideoPlsCytronSDK is available under the MIT license. See the LICENSE file for more info.
