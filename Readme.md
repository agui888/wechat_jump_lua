##
微信跳一跳 触动精灵脚本
----------

----
这个东西其实网上有现成的外挂了，各种方式。图形识别，人肉丈量。都是不错的选择，可以参考这个链接https://github.com/wangshub/wechat_jump_game。基于安卓adb实现的外挂。我没用过这个，但是识别效率肯定比在手机上会高一些。其实我还是想自己实现一个外挂，没别的意思，就是纯粹好玩。

----
于是就想基于触动精灵来实现一个外挂，为了简单。于是想到了下面的识别办法：
-
1. 逐行进行扫描来识别要跳转的目标坐标。为了提高效率可以适当增加扫描步进。定义一个矩形区域，要跳转的目标相对来说位置都比较固定。
2. 获取小人的位置，通过触动精灵的查找颜色功能进行定位坐标，虽然有一定误差，但是只要能获取到坐标，用来计算还是基本没问题的。
3. 计算跳跃距离，通过直接三角形的勾股定理进行计算。按压时间需要根据距离进行修正，我在小米 5s上测试用的1.2 基本还算可以。

----
已知问题：
-
1. 通过触动精灵进行颜色匹配搜索坐标的做法效率较低，需要比较长的时间。
2. 运行一段时间之后，找色函数和获取小人坐标的函数会发生错误，导致无法获取到真正的坐标。我加了几个判断，出现问题的时候直接重新启动脚本就可以了。
3. 由于是基于颜色进行匹配的，因而相对来时识别的坐标的准确度比上面的python版本要低很多。

改进方式：
-
1. 针对搜索坐标的函数进行匹配，折半查找，如果小人在左侧，直接搜索右侧。如果小人在右侧直接搜索左侧。
2. 匹配到错误之后直接重启脚本，使用触动精灵的循环运行功能
3. 其他未知的功能修改？我也不知道有啥。哈哈


------

http://www.h4ck.org.cn
----------
http://www.findu.co
----------