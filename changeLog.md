
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
