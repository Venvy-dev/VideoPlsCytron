# VideoPlsCytronSDK
###1.8.11

###1.8.10

###1.8.9

###1.8.8

###1.8.7

###1.8.6

###1.8.5

###1.8.4

###1.8.3

###1.8.2

###1.8.1

###1.8.0


###1.7.5
1. 去掉关闭视频的小白点

###1.7.3


###1.7.0
1. 气泡上方增加半透明层，产生渐隐效果
2. 默认主题投票，隐藏`icon`
3. 百科/轮播：自动轮播时间设置为3秒
4. 百科信息层只有1张图片，不显示小圆点
5. 增加广告投放后台开关
6. 统一沙盒文件路径

###1.6.12
1. 添加1.6.11没有打包功能(http拉取新闻)

###1.6.11
1. 关闭MQTT

###1.6.10

###1.6.9
1. 将对UI修改扔到主线程

###1.6.8
1. 修复在快速遍历中修改内容

###1.6.7
1. 修改关闭按钮样式，增大点击区域
2. 气泡增加按北京时间关闭功能
3. 修改SDKInfo调用
4. 增加对adServer的开关
5. 增加气泡应用15s关闭
6. 修复mqtt获取参数为空设置倒Dict中闪退
7. 修改小白点请求使用的manager

###1.6.6
1. 优化结构体请求流程 

###1.6.5
1. 修复了气泡在某些播放器会在旋转时移除导致的`contentOffset`位置异常

###1.6.4
1. 修复了第二次出现小白点不会发送预加载和正式加载的`bug`

###1.6.3
1. 增加暂停`cytronView`的功能

###1.6.2
1. 修复MQTT热点下线视频点时可能导致的`crash`

###1.6.0
1. 热点增加广告和关闭按钮
2. 修改结构体请求链路，将结构体请求前置，在每次打开视频时进行增量更新

###1.5.0
1. 增加统一对外接口

###1.4.0+1
1. 修复`monitor`未发送的bug

###1.4.0
1. 增加`LogReport`埋点设置
2. 轮播应用新增旋转效果

###1.3.6
1. 解决轮播以及海报图片统计重复曝光的问题
2. 数据请求接口更改为动态接口
