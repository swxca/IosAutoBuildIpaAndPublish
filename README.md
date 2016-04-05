# IosAutoBuildIpaAndPublish

# 证书相关

# 本机证书的配置

---

CSR文件：证书签名请求文件

[TOC]

## App id 注册

[创建](https://developer.apple.com/account/ios/identifier/bundle/create)新的app id
需要填写：

1. Name，就是app的显示名称
2. Explicit App ID，bundle ID：就是xcode里的bundle identifier
3. 选择需要启用的服务![选择服务][1]
4. Continue
5. Create

## 证书申请

1. [新建](https://developer.apple.com/account/ios/certificate/create)一个证书
2. 在列表中选择证书类型，包括
  1. **Development**类证书![开发类][2]
  2. **Distribution**类证书![发布类][3]
3. 例如选择Distribution中的第一个`App Store and Ad Hoc`，点击下一步
4. 提示生成**CSR文件**即**证书签名请求文件**，步骤为：
  1. 打开KeyChain Access
  2. 点击菜单栏中苹果图标右边的第一项即**钥匙串访问** *KeyChain Access*，选择**证书助理** *Certificate Assistant* $\rightarrow$ **从证书颁发机构请求证书** *Request a Certificate from a Certificate Authority...*
  3. 填写电子邮件地址，选择**保存到磁盘** *Saved to disk*
  4. 保存到本地某个位置
5. 回到浏览器，Continue，并上传刚才的CSR文件
6. 上传完成后，下载安装生成的证书文件`.cer`
7. 打开KeyChain Access找到这个证书，可以看到一个十位的标识码，由数字和大写字母组成。

## PP文件

1. [创建](https://developer.apple.com/account/ios/profile/create)新的PP文件
2. 选择PP文件类型，这里选择`Distribution -> App Store`类型![PP文件类型][4]
3. 选择App ID，就是需要上传的App的ID![选择App ID][5]
4. 选择一个证书，继续
5. 输入一个文件名，生成，下载，双击安装


## 上传IAP到App Store

1. 确保项目的Bundle Identifier和上面申请的App ID相同，code sign identity选择的上面生成的证书，通过那个十位的标识码区分，如`CODE_SIGN_IDENTITY = "iPhone Distribution: Developer Name (**********)";`。这两项使用Xcode的话，是在项目的设置里更改，


  [1]: http://static.zybuluo.com/zhengbuqian/0jfb0p0jpow95tg4nzvul2lh/Snip20160405_1.png
  [2]: http://static.zybuluo.com/zhengbuqian/dp6tr9u9twdww8rkaqtuvx8k/Snip20160405_2.png
  [3]: http://static.zybuluo.com/zhengbuqian/736830kps7hi2l7qkssxainb/Snip20160405_3.png
  [4]: http://static.zybuluo.com/zhengbuqian/09ee5tmqdj2ek945no0ov2m9/Snip20160405_5.png
  [5]: http://static.zybuluo.com/zhengbuqian/f0lxusw1bpz9llgtmgcekfg6/Snip20160405_6.png
  
## 以上过程可以使用fastlane库。(很强大)  
  
