###一、理解 URL Session 概念
#####1、会话类型（Types of Sessions）
NSURLSession API 支持三种会话类型，通过配置对象类型来决定如何创建会话:

* 对于 URLs 下载，默认的会话行为模拟其它的 Foundation中的方法。
* 短暂的会话不要存储任何数据到磁盘；所有的缓存，证书存储，还有其它一些会话绑定在内存中。从而，当你的 app 会话无效，它们是自动清除的。
* 后台的会话也是模拟默认的会话，除了那个单独的进程处理所有的数据传输。后台会话还添加了一些限制，参考下面的后台传输考虑。

#####2、任务类型（Types of Tasks）
NSURLSession 类支持三种任务类型：数据任务，下载任务，还有上传任务。

* 数据任务使用 NSData 对象发送和接受数据。数据任务的作用是从你的服务器少量的、频繁的请求。数据任务能够返回从你的 app 接受一次数据或者所有的数据一次后，完成处理。
* 下载任务从一个文件取回数据，它只吃后台下载，当这个app不运行的时候。
* 上传任务从一个文件发送数据，它支持后台上传，当这个app不运行的时候。

#####3、后台传输考虑（Background Transfer Considerations）
NSURL Session 类支持后台传输，当你的 app 挂起的时候。后台传输仅仅支持通过会话创建配置的一个后台会话对象（例如返回通过调用 backgroundSessionConfiguration:）。

在后台会话中，因为这个传输是通过一个单独的进程执行，它的消耗是相对高的，一些功能是不可以使用的，导致有一些限制：

* 这个会话必须提供代理事件的传递。（对于上传和下载，和它们有着相同的传输代理行为）
* 仅仅支持 HTTP 和 HTTPS 协议，不支持自定义协议。
* Redirects are always followed.
* 仅仅支持从一个文件上传任务（上传从一个数据对象或者流，在程序退出后会失败）。
* 如果启动后台传输，而 app 在后台，需要配置 discretionary 属性为 true.

**注意：iOS 8 和 OSX 10.10，数据任务不支持后台会话**

....未完

#####4、生命周期和 delegate 作用（Life Cycle and Delegate Interaction）
....未完

#####5、NSCopying 行为（NSCopying Behavior）
会话和任务对象需要遵守 NSCopying 协议：

* 当你的 app 有一个会话副本或者任务对象，你可以得到一个相同的对象。
* 当您的 app 有一个 configuration 对象副本，你可以得到一个新的副本，从而你可以单独修改。

### 二、简单的代理类接口
。。。。













