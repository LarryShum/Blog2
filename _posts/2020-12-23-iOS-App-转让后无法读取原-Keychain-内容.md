# iOS App转让后无法读取原Keychain内容

### Keychain介绍
Keychain Services 是 macOS 和 iOS 都提供一种安全的存储敏感信息的工具,比如,网络密码:用户访问服务器或者网站,通用密码:用来保存应用程序或者数据库密码.与此同时,用于认证的证书,密钥,和身份信息,也可以存储在Keychain中,Keychain Services 的安全机制保证了存储这些敏感信息不会被窃取。简单说来，Keychain 就是一个安全容器。

### Keychain的特点
数据并不存放在App的Sanbox中，即使删除了App，资料依然保存在keychain中。如果重新安装了app，还可以从keychain获取数据。
keychain的数据可以通过group方式，让程序可以在App间共享。不过得要相同TeamID
keychain的数据是经过加密的

### Keychain的应用
因为keychain的数据不存放在App的Sanbox中，即使删除了App，资料依然保存在keychain中。如果重新安装了app，还可以从keychain获取数据，通常用来保存账号、密码、设备标识等数据。

### iOS 应用间共享 Keychain 数据
在 iOS 3.0 之后，应用间共享 keychain 数据成为了一种可能。但这是被严格限制的,只有拥有相同 App ID 前缀的应用才有可能共享 keychai,并且各应用存储的 keychain item 都标记了相同的 kSecAccessGroup 字段值

**相同的Team ID**

有相同的 Team ID这个是应用间共享 Keychain 数据的前提条件。一个 App ID 分两部分：

Apple 为你生成的 Team ID

开发者注册的 Bundle ID

一个典型的 App ID 如：GPZ8FX842Q.com.apple.app, GPZ8FX842Q即为你的Team ID,是 Apple 为你生成的

一个开发者账号可以有不同的几个 Team ID。但 Apple 不会为不同的开发者生成一样的 Team ID。这样，不同的开发者账号发布的应用想共享 keychain 数据，在现在来看是无法实现的。而要做到 Keychain 数据共享，要求是同一个开发账号开发的，同时选择了相同的 Team ID

### App转让后无法读取原Keychain内容

![](https://cdn7a.y523.com/images/blog/images/keychain.png)

因为App转让后team ID变了，从而App ID也变了，导致无法读取原来的keychain数据

###应对方案
* 保存数据到keychain同时也保存一份到sandbox，当keychain数据为空时候读取sandbox的数据（受影响的是转让App前卸载，转让App后重新安装的用户）
* App用户量较少前转让，受影响的用户就减少（转让后新增的用户不受影响）
