# LTScrollView

实现原理： [http://blog.csdn.net/glt_code/article/details/78576628](http://blog.csdn.net/glt_code/article/details/78576628)

[![CI Status](http://img.shields.io/travis/1282990794@qq.com/LTScrollView.svg?style=flat)](https://travis-ci.org/1282990794@qq.com/LTScrollView)
[![Version](https://img.shields.io/cocoapods/v/LTScrollView.svg?style=flat)](http://cocoapods.org/pods/LTScrollView)
[![License](https://img.shields.io/cocoapods/l/LTScrollView.svg?style=flat)](http://cocoapods.org/pods/LTScrollView)
[![Platform](https://img.shields.io/cocoapods/p/LTScrollView.svg?style=flat)](http://cocoapods.org/pods/LTScrollView)

![image](https://github.com/gltwy/LTScrollView/blob/master/demo.gif)

## Demo文件路径以及说明

- LTScrollView / Example : 为 Swift 使用示例.
- LTScrollView / OCExample : 为 OC 使用示例.
- 支持的子View为UIScrollView、UICollectionView、UITableView.
- 无限轮播 + 拖动移动

## CocoaPods安装

安装[CocoaPods](http://cocoapods.org) 使用以下命令：

```bash
$ gem install cocoapods
```

### Podfile

在你的 `Podfile`中添加LTScrollView

```ruby
source 'https://github.com/CocoaPods/Specs.git'
platform :ios, '8.0'

target 'TargetName' do
# 注意此处需要添加use_frameworks!
use_frameworks!

# 当前最新版本 - 2021-11-20
pod 'LTScrollView', '~> 0.4.3'

# 无限轮播框架 + 预加载子组件
#pod 'LTScrollView/LTLoopsPlay'

# 跟随拖动移动子组件
#pod 'LTScrollView/LTFollowMove'

end
```

然后，使用以下命令安装

```bash
$ pod install
```

提示错误 `[!] Unable to find a specification for LTScrollView ` 解决办法：

```
$ pod repo remove master
$ pod setup
```

## Swift使用说明

### Swift.LTSimple使用说明

1. 创建LTSimpleManager实例对象
```objective-c
@objc public init(frame: CGRect, viewControllers: [UIViewController], titles: [String], currentViewController:UIViewController, layout: LTLayout)
```
2. 设置headerView
```objective-c
@objc public func configHeaderView(_ handle: (() -> UIView?)?)
```
3. 子控制器中glt_scrollView进行赋值
```objective-c
self.glt_scrollView = self.tableView（self.scrollView / self.collectionView）
```
4. 更多使用说明请参考Demo（LTScrollView / Example）


### Swift.LTAdvanced使用说明

1. 创建LTAdvancedManager实例对象、并设置headerView
```objective-c
@objc public init(frame: CGRect, viewControllers: [UIViewController], titles: [String], currentViewController:UIViewController, layout: LTLayout, headerViewHandle handle: () -> UIView)
```
2. 子控制器中glt_scrollView进行赋值
```objective-c
self.glt_scrollView = self.tableView（self.scrollView / self.collectionView）
```
3. 更多使用说明请参考Demo（LTScrollView / Example）

## OC使用说明

### OC.LTSimple使用说明
1. 创建LTSimpleManager实例对象
```objective-c
[[LTSimpleManager alloc] initWithFrame:frame viewControllers:self.viewControllers titles:self.titles currentViewController:self layout:self.layout]
```
2. 设置headerView
```objective-c
[self.managerView configHeaderView:^UIView * _Nullable{ }]
```
3. 子控制器中glt_scrollView进行赋值
```objective-c
self.glt_scrollView = self.tableView（self.scrollView / self.collectionView）
```
4. 更多使用说明请参考Demo（LTScrollView / OCExample）

### OC.LTAdvanced使用说明
1. 创建LTAdvancedManager实例对象、并设置headerView
```objective-c
 [[LTAdvancedManager alloc] initWithFrame:frame viewControllers:self.viewControllers titles:self.titles currentViewController:self layout:self.layout headerViewHandle:^UIView * _Nonnull{}]
```
2. 子控制器中glt_scrollView进行赋值
```objective-c
self.glt_scrollView = self.tableView（self.scrollView / self.collectionView）
```
3. 更多使用说明请参考Demo（LTScrollView / OCExample）

## LTLayout属性说明
详情查看[LTLayout.swift](https://github.com/gltwy/LTScrollView/blob/master/Example/LTScrollView/Lib/LTLayout.swift)

## 更新说明

2022.03.13 - 0.4.4
```objective-c
1. 自定义标题模块修改
2. 修复进阶版部分机型小数导致无法悬停问题
```

2022.03.05 - 0.4.3
```objective-c
1. 新增嵌套混合视图的切换（支持悬停+左右切换）
2. 新增无限轮播+预加载视图框架
3. 新增跟随拖动隐藏视图框架

建议所有用户都升级～
```

2021.11.20 - 0.4.2
```objective-c
1. 完美适配iOS15
2. 修复OC不能自定义标题的Bug
3. 修复进阶版无法滚动到指定位置的Bug
4. 完善OC Demo的使用示例
5. 修复部分开发者使用中反馈的问题

建议所有用户都升级～
```

2020.08.22 - 0.3.0
```objective-c
1. 兼容Swift5
2. 新增自定义标题功能, 任意样式随你设置
3. 修复子控制器不释放Bug
4. 优化内部实现、修复已知问题、性能更佳

目前仅优化了除LTAdvancedManager以外的其他功能，LTAdvancedManager近期优化！
```

2018.09.16 - 0.2.0
```objective-c
新增自定义选项卡
```

2018.09.02 - 0.1.9
```objective-c
1. 修修复LTAdvancedManager子控制为CollectionView时的Bug
2. 解决issue中的部分问题
```

2018.07.29 - 0.1.8
```objective-c
1. 新增LTLayout中关闭左右滑动的属性isScrollEnabled
2. 修复LTAdvancedManager数据较少时切换Bug
3. 解决issue中的部分问题
```

2018.06.30 - 0.1.7
```objective-c
1. 修复LTAdvancedManager数据较少时，其他子控制器自动下落Bug
2. 解决issue中的部分问题
3. 优化内部实现
```

## Author
- 微信公众号:  [技术大咖社](https://mp.weixin.qq.com/mp/profile_ext?action=home&__biz=Mzg4OTYwMTc3NQ==#wechat_redirect)（如有任何疑问、均可在公众号内留言）
- -Blog:  https://blog.csdn.net/glt_code

## License

LTScrollView is available under the MIT license. See the LICENSE file for more info.


