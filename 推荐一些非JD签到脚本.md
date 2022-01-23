> # JD脚本实在太多，来点新鲜的



![image-20211117122541293](https://mo.lincloud.pro/blog/images/image-20211117122541293.png)

本文的脚本全部应用在青龙面板，如不知道什么是青龙面板可以参考[这篇文章](https://blog.lincloud.pro/archives/40.html)，保证大有裨益。
Sitoi/Dailycheckin 盖了主流签到脚本，适合日常升级领道具使用。


<!--more-->


####  Sitoi/Dailycheckin 仓库

- 文档地址: https://sitoi.github.io/dailycheckin/

- 国内地址: https://sitoi.gitee.io/dailycheckin/

  

**支持的签到内容**

🟢: 正常运行 🔴: 脚本暂不可用 🔵: 可以执行(需更新) 🟡: 待测试 🟤: 看脸

| 类别 | 任务名称   | 名称                                                      | 备注                                                         | 终端   | Cookie 时长 | 状态 |
| ---- | ---------- | --------------------------------------------------------- | ------------------------------------------------------------ | ------ | ----------- | ---- |
| 签到 | IQIYI      | [爱奇艺](https://www.iqiyi.com/)                          | 签7天奖1天，14天奖2天，28天奖7天；日常任务4成长值；随机成长值；三次抽奖 | WEB    | 待测试      | 🟢️    |
| 签到 | KGQQ       | [全民K歌](https://kg.qq.com/index-pc.html)                | 每日签到获取鲜花 每日大约 150 鲜花左右                       | WEB    | 待测试      | 🟢️    |
| 签到 | VQQ        | [腾讯视频](https://v.qq.com/)                             | 每日两次腾讯视频签到获取成长值                               | WEB    | 待测试      | 🟢️    |
| 签到 | YOUDAO     | [有道云笔记](https://note.youdao.com/web/)                | 每日签到获取存储空间                                         | WEB    | 待测试      | 🟢️    |
| 签到 | MUSIC163   | [网易云音乐](https://music.163.com/)                      | 每日刷歌 310 首，登录失效                                    | WEB    | 永久        | 🟢    |
| 签到 | ONEPLUSBBS | [一加手机社区官方论坛](https://www.oneplusbbs.com/)       | 论坛每日签到 + 10 次抽奖任务                                 | WEB    | 待测试      | 🟢️    |
| 签到 | TIEBA      | [百度贴吧](https://tieba.baidu.com/index.html)            | 贴吧每日签到                                                 | WEB    | 待测试      | 🟢️    |
| 签到 | BILIBILI   | [Bilibili](https://www.bilibili.com)                      | 直播签到，漫画签到，每日经验任务，自动投币，银瓜子换硬币等功能 | WEB    | 待测试      | 🟢️    |
| 签到 | V2EX       | [V2EX](https://www.v2ex.com/)                             | 铜币奖励                                                     | WEB    | 待测试      | 🟢️    |
| 签到 | WWW2NZZ    | [咔叽网单](https://www.2nzz.com/)                         | 论坛金币                                                     | WEB    | 待测试      | 🟢️    |
| 签到 | SMZDM      | [什么值得买](https://www.smzdm.com)                       | 每日签到                                                     | WEB    | 待测试      | 🟢️    |
| 签到 | ACFUN      | [AcFun](https://www.acfun.cn/)                            | 每日签到香蕉                                                 | WEB    | 永久        | 🟢    |
| 签到 | CLOUD189   | [天翼云盘](https://cloud.189.cn/)                         | 每日签到 +2次抽奖获得空间奖励                                | WEB    | 永久        | 🟢️    |
| 签到 | POJIE      | [吾爱破解](https://www.52pojie.cn/index.php)              | 2枚吾爱币                                                    | WEB    | 待测试      | 🟤    |
| 签到 | PICACOMIC  | [哔咔漫画](https://www.picacomic.com)                     | 成长值奖励                                                   | WEB    | 永久        | 🟤    |
| 签到 | MEIZU      | [MEIZU 社区](https://bbs.meizu.cn)                        | 每日签到、可配置抽奖                                         | WEB    | 待测试      | 🟢️    |
| 签到 | ZHIYOO     | [智友邦](http://zhizhiyoo.net/)                           | 每日签到获取金币                                             | WEB    | 待测试      | 🟢️    |
| 签到 | CSDN       | [CSDN](https://www.csdn.net/)                             | 每日签到、抽奖                                               | WEB    | 待测试      | 🟢️    |
| 签到 | EVERPHOTO  | [时光相册](https://web.everphoto.cn/)                     | 每日签到                                                     | WEB    | 待测试      | 🟢️    |
| 签到 | WOMAIL     | 联通沃邮箱                                                | 每日签到，签到7天得2元话费                                   | 公众号 | 待测试      | 🟢    |
| 签到 | WZYD       | 王者营地                                                  | 每日签到（仅限 QQ 区）                                       | APP    | 待测试      | 🟢    |
| 签到 | WEIBO      | 微博                                                      | 每日钱包签到、打卡                                           | APP    | 待测试      | 🟢️    |
| 签到 | DUOKAN     | 多看阅读                                                  | 获取书豆，用于购买书籍                                       | APP    | 待测试      | 🟢️    |
| 签到 | MGTV       | 芒果 TV                                                   | 签到获取体验会员                                             | APP    | 待测试      | 🟢️    |
| 签到 | HEYTAP     | 欢太商城                                                  | 获取积分                                                     | APP    | 待测试      | 🟢    |
| 签到 | UNICOM     | 联通营业厅                                                | 获取积分、流量等                                             | APP    | 待测试      | 🟢    |
| 签到 | FMAPP      | Fa 米家                                                   | 连续签到7天总计获得6粒Fa米粒，每月15号23.59分清空Fa米粒。理论一个月最少获得24粒fa米粒。 | APP    | 待测试      | 🟢️    |
| 其他 | MIMOTION   | 小米运动                                                  | 每日小米运动刷步数                                           | APP    | 永久        | 🟢    |
| 其他 | BAIDU      | [百度搜索资源平台](https://ziyuan.baidu.com/site/index#/) | 提交网站页面供百度收录                                       | WEB    | 永久        | 🟢️    |

**一、进入青龙容器内部**

```
docker exec -it ql bash
```

**二、安装依赖**

```
apk add --no-cache gcc g++ python python-dev py-pip mysql-dev linux-headers libffi-dev openssl-dev
pip3 install dailycheckin --upgrade
```

> 如果上述命令仍然安装失败运行下面的命令

```
apk add --no-cache --virtual .build-deps gcc musl-dev python2-dev python3-dev
pip3 install pip setuptools --upgrade
pip3 install cryptography~=3.2.1
```
> 如再次失败可以更改PIP源再试

**三、新建并编写 `/ql/scripts/config.json` 配置文件**

参考[配置说明文档](https://sitoi.gitee.io/dailycheckin/settings/) ，并修改 `config.json`

配置说明文档：https://sitoi.gitee.io/dailycheckin/settings/

> 配置文件是必须要有的，这个配置文件记录了需要运行的任务类型，以及每个任务的账号信息，**运行脚本只是让脚本根据配置信息来执行每个任务**，一些提醒和推送也是在配置中设置的，需要好好看一看

**四、配置定时任务**

1. 运行全部脚本（默认）

![ql-base](https://mo.lincloud.pro/blog/images/ql-base.png)

1. 运行**部分**脚本（例如配置文件中配置了多个任务，但是想运行**部分**的任务可以这么设置，可同时选择多个，用「空格」分开），

      ![ql-base](https://mo.lincloud.pro/blog/images/ql-include.png)

2. 运行部分脚本(**排除法**)（例如配置文件中配置了多个任务，但是想**排除**部分任务可以这么设置，可同时选择多个，用「空格」分开排除），可以同时选择多个，用「空格」分开   

   ![ql-exclude](https://mo.lincloud.pro/blog/images/ql-exclude.png)

3. 配置定时更新   

   ![ql-update](https://mo.lincloud.pro/blog/images/ql-update.png)

