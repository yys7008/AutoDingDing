## ⏰ AutoDingDing

<img width="796" src="https://user-images.githubusercontent.com/49583943/138620009-32d16b4a-d38b-4cb7-9650-db7f45f14520.png"/>

## 📖 简介

钉钉全自动打卡 + 远程打卡脚本，无需 root，基于 auto.js，适用于蓝牙考勤机。

## 💥 功能

- 定时打卡
- 远程打卡
- 发送考勤结果

## ⚙️ 工具

- auto.js
- Tasker
- 一款通讯应用（示例脚本中使用的是 QQ / 网易邮箱大师 / ServerChan / PushDeer，彼此互为备用方案）

## 💡 原理

通过 auto.js 脚本监听本机通知，在 Tasker 中创建定时任务，发出通知，或在另一设备上发送消息到本机，即可触发脚本中的打卡进程，实现定时打卡和远程打卡。

![image](https://user-images.githubusercontent.com/49583943/163506300-7ef7693b-a273-442f-8449-dcef31063069.png)

同理，监听到钉钉发出的打卡成功通知后，将通知文本通过 QQ消息 或 邮件正文 发送，实现发送考勤结果的功能。



## 📐 工具介绍

### Auto.js

Auto.js 是利用安卓系统的 「无障碍服务」 实现类似于按键精灵一样，可以通过代码模拟一系列界面动作的辅助工具。

与 「按键精灵」 不同的是，它的模拟动作并不是简单的使用在界面定坐标点来实现，而是找控件来实现的。

免费版：[Auto.js 4.1.1a Alpha2-armeabi-v7a-release](https://github.com/georgehuan1994/DingDing-Automatic-Clock-in/raw/master/Autojs%204.1.1a%20Alpha2-armeabi-v7a-release.apk "Auto.js 4.1.1a Alpha2-armeabi-v7a-release")

github：[GitHub - hyb1996/Auto.js](https://github.com/hyb1996/Auto.js)

官方文档：[首页 - Auto.js](https://hyb1996.github.io/AutoJs-Docs/)

推荐使用[VS Code 插件](https://github.com/hyb1996/Auto.js-VSCode-Extension)进行调试，调试完成后，还能通过此插件将脚本保存到手机上。

### Tasker
[Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm) 也是一个安卓自动化神器，与 Auto.js 结合使用可胜任日常工作流。

此处仅提供 Tasker 5.0 及以下的官方原版，原版不含正版验证，使用不受限制：

[Tasker.4.9u4m.apk](https://github.com/georgehuan1994/DingDing-Automatic-Clock-in/blob/master/Tasker.4.9u4m.apk)

[Tasker.5.0u7m.apk](https://github.com/georgehuan1994/DingDing-Automatic-Clock-in/blob/master/Tasker.5.0u7m.apk)

Tasker 定时打卡配置：

1. 添加一个 「通知」 操作任务，通知标题修改为 「定时打卡」，通知文字随意，通知优先级设为 1。
2. 添加两个配置文件，使用日期和时间作为条件，分别在上班前和下班后触发。

你也可以[下载配置文件](https://github.com/georgehuan1994/DingDing-Automatic-Clock-in/tree/master/Tasker配置)，导入到 Tasker 中使用，方法如下：

1. 长按 菜单栏-任务，导入"发送通知.tsk.xml"。
2. 长按 菜单栏-配置文件，导入"上班打卡.prf.xml" 和 "下班打卡.prf.xml"。
3. 在任务编辑界面左下方有一个三角形的播放按钮，点击即可发送通知，方便调试。

## 🕹️ 使用方法

### 远程打卡

- 向本机的 QQ 发送消息 「打卡」，或回复标题为 「打卡」 的邮件，或向 PushDeer 发送标题为「打卡」 的推送请求，即可触发打卡进程。
- 向本机的 QQ 发送消息 「查询」，或回复标题为 「查询」 的邮件，或向 PushDeer 发送标题为「查询」 的推送请求，即可查询最新一次打卡结果。

### 暂停/恢复定时打卡

- 向本机的 QQ 发送消息 「暂停」，或回复标题为 「暂停」 的邮件，或向 PushDeer 发送标题为「暂停」 的推送请求，即可暂停定时打卡功能（仅暂停定时打卡，不影响远程打卡功能）
- 向本机的 QQ 发送消息 「恢复」，或回复标题为 「恢复」 的邮件，或向 PushDeer 发送标题为「恢复」 的推送请求，即可恢复定时打卡功能。

## ⚠️ 注意事项 (必读!!!)

- AutoJs Pro 版本屏蔽了一些主流应用，如果要使用 QQ 作为回复方式，不要使用 AutoJs Pro 版！
- 首次启动 AutoJs，需要为其开启无障碍权限。
- 运行脚本前，请在 AutoJs 菜单栏中（从屏幕左边划出），开启 「通知读取权限」。
- 若无法通过 `app.launchPackage()` 方法启动应用，请开启该应用的「自启动」「允许后台弹窗」。
- AutoJs、Tasker 可息屏运行，需要在系统设置中开启通知亮屏。
- 为保证 AutoJs、Tasker 进程不被系统清理，可调整它们的电池管理策略、加入管理应用的白名单，为其开启前台服务、添加应用锁...
- 虽然脚本可执行完整的打卡步骤，但推荐开启钉钉的极速打卡功能，在钉钉启动时即可完成打卡，应把后续的步骤视为极速打卡失败后的保险措施。

## 📜 更新日志

### 2022-03-26
<details open>
<summary></summary>

1. 可以通过 PushDeer 接收通知、推送考勤结果
</details>

### 2022-03-01
<details open>
<summary></summary>

1. 可以通过Server酱来推送考勤结果
</details>

### 2021-10-23
<details open>
<summary></summary>

1. 适配网易邮箱大师7.0
</details>

### 2021-09-02
<details open>
<summary></summary>

1. 新增获取日志功能，发送 「日志」，可将运行日志作为邮件附件发送（最好使用内置邮件）
2. 优化通知过滤器，过滤 Tasker 发出的无效通知
</details>


### 2021-07-07
<details open>
<summary></summary>

1. 登录流程自动同意隐私协议
</details>

### 2021-05-27
<details open>
<summary></summary>

1. 修改了部分常量的命名
2. 移除了休息日不打卡的判断
3. 在邮件的基础上，增加QQ作为新的通讯方式。除发送考勤结果需要手动指定应用外，使用QQ向本机发送 「查询、暂停、恢复」 指令，则会用QQ来回复查询或操作结果；使用邮件向本机发送指令则用邮件回复。
</details>

### 2021-05-06
<details open>
<summary></summary>

1. 增加音量上键监听，按下后中断所有子线程，也可以利用回调来进行调试
2. 不再使用考勤机名称来判断连接状态
3. 重新进入打卡界面前，先返回上级菜单，以解决顶号登录无法正常连接到考勤机的问题
4. 启动钉钉时，将媒体音量和通知音量设为0
</details>

### 2021-03-15
<details open>
<summary></summary>

1. 运行时检查Auto.js版本，脚本需要在Auto.js 4.1.0及以上版本中运行
2. 新增解锁是否成功的判断，若解锁失败则停止运行脚本
3. 优化 `signIn()` 方法，使用 bundleId + activity 来判断登录情况
4. 优化部分控件和信息的获取方式
</details>

### 2021-03-09
<details open>
<summary></summary>

1. 移除 「结束钉钉」、「检查更新」 这个两个过程，使用最近一次监测到的正在运行的应用的包名进行判断
2. 补充一个万能锁屏方案：向Tasker发送广播，触发Tasker中的系统锁屏操作。

    - 在Tasker中添加一个任务，在任务中添加操作 「系统锁屏（关闭屏幕）」
    - 在Tasker中添加一个事件类型的配置文件，事件类别：系统-收到的意图
    - 在事件操作中填写：autojs.intent.action.LOCK_SCREEN ，保持发送方与接收方的action一致即可

```javascript
app.sendBroadcast({
        action: 'autojs.intent.action.LOCK_SCREEN'
    });
```
</details>

### 2021-02-07
<details open>
<summary></summary>

1. 防止监听事件被耗时操作阻塞。
</details>

### 2021-01-15
<details open>
<summary></summary> 

1. 移除 「进入工作台」 以及 「进入考勤打卡界面」 这两个过程
2. 启动并成功登录钉钉后，直接使用intent拉起考勤打卡界面
</details>

### 2021-01-08
<details open>
<summary></summary>

1. 修复：通知过滤器报错
</details>

### 2020-12-30
<details open>
<summary></summary>

1. 优化：现在可以通过邮件来 暂停/恢复 定时打卡功能，以应对停工停产，或其他需要暂时停止定时打卡的特殊情况
</details>

### 2020-12-04
<details open>
<summary></summary>

1. 优化：打卡过程在子线程中执行，钉钉返回打卡结果后，直接中断子线程，减少无效操作
</details>

### 2020-10-27
<details open>
<summary></summary>

1. 修复：当钉钉的通知文本为null时，indexOf()方法无法正常执行
</details>

### 2020-09-24
<details open>
<summary></summary>

1. 优化：使用URL Scheme直接拉起考勤打卡界面

```javascript
function attendKaoqin(){
    var a = app.intent({
        action: "VIEW",
        data: "dingtalk://dingtalkclient/page/link?url=https://attend.dingtalk.com/attend/index.html"
      });
      app.startActivity(a);
      sleep(5000)
}
```
#### 获取URL的方式如下：

1. 在PC端找到 「智能工作助理」 联系人
2. 发送消息 “打卡” ，点击 「立即打卡」 
3. 弹出一个二维码。此二维码就是拉起考勤打卡界面的 URL，用自带的相机或其他应用扫描，并在浏览器中打开，即可获得完整URL
4. 观察获取到的URL，找到 `CorpId=xxxxxxxxxxxxxxxxxxx` ，将CorpId的值填写到的脚本开头的CORP_ID这个常量中
5. 仅使用 `dingtalk://dingtalkclient/page/link?url=https://attend.dingtalk.com/attend/index.html`，也可以拉起旧版打卡界面，钉钉会自动获取企业的CorpId。如果加入了多个组织，且没有填写CorpId，则在拉起考勤界面时会弹出一个选择组织的对话框。
</details>

### 2020-09-11
<details open>
<summary></summary>

1. 将上次考勤结果储存在本地
2. 将运行日志储存在本地 /sdcard/脚本/Archive/
3. 修复在下班极速打卡之后，重复打卡的问题
</details>

### 2020-09-04
<details open>
<summary></summary>

1. 将 "打卡" 与 "发送邮件" 分离成两个过程，打卡完成后，将钉钉返回的考勤结果作为邮件正文发送
</details open>

### 2020-09-02
<details open>
<summary></summary>

1. 改为使用 "去打卡" 文本获取按钮。若找不到 "去打卡" 按钮，则直接点击 "考勤打卡" 的屏幕坐标
</details>



## 📢 声明

此仓库及脚本仅供学习交流，欢迎转载。旨在让人们关注996制度的存在和非法性，并尝试改变这种现象。

根据1994年第八届全国人大常委会通过和2018年第十三届全国人大常委会修正的《中华人民共和国劳动法》规定，劳动者**每日工作时间不超过8小时，平均每周工作时间不超过44小时，而996工作制每周至少要工作72个小时**，远超法律标准，因此996工作制度违反劳动法。

<font color=red>而钉钉却允许企业管理者违反法律，非法排班！</font> 

<blockquote>

**第三十六条**　国家实行劳动者每日工作时间不超过八小时、平均每周工作时间不超过四十四小时的工时制度。

**第四十一条**　用人单位由于生产经营需要，经与工会和劳动者协商后可以延长工作时间，一般每日不得超过一小时；因特殊原因需要延长工作时间的，在保障劳动者身体健康的条件下延长工作时间每日不得超过三小时，但是每月不得超过三十六小时。

**第四十四条**　有下列情形之一的，用人单位应当按照下列标准支付高于劳动者正常工作时间工资的工资报酬：

（一）安排劳动者延长工作时间的，支付不低于工资的百分之一百五十的工资报酬；  
（二）休息日安排劳动者工作又不能安排补休的，支付不低于工资的百分之二百的工资报酬；  
（三）法定休假日安排劳动者工作的，支付不低于工资的百分之三百的工资报酬。  

**第九十条**　用人单位违反本法规定，延长劳动者工作时间的，由劳动行政部门给予警告，责令改正，并可以处以罚款。

**第九十一条**　用人单位有下列侵害劳动者合法权益情形之一的，由劳动行政部门责令支付劳动者的工资报酬、经济补偿，并可以责令支付赔偿金：

（二）拒不支付劳动者延长工作时间工资报酬的；

</blockquote>

---

    如果觉得还不错的话，就点击右上角, 给我个Star ⭐️ 鼓励一下我吧~
