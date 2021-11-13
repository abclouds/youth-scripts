

  [toc]  

 # <center> 中青看点使用说明 赞赏:中青邀请码`51767260`万分感谢</center> 

### IOS配置教程
 ```
[MITM]
hostname = kd.youth.cn, kandian.wkandian.com
 ```
#### Surge:
* [模块地址](https://raw.githubusercontent.com/abclouds/youth-scripts/master/surge.sgmodule)

 ```
https://raw.githubusercontent.com/abclouds/youth-scripts/master/surge.sgmodule
 ```
 * 本地重写
 
 ```
[Script]
中青看点 = type=cron,cronexp=35 5 0 * * *,script-path=https://raw.githubusercontent.com/abclouds/youth-scripts/master/js/youth.js,script-update-interval=0
中青看点 = type=http-request,pattern=https:\/\/kd\.youth\.cn\/WebApi\/NewTaskIos\/getTaskList,script-path=https://raw.githubusercontent.com/abclouds/youth-scripts/master/js/youth.js
中青看点 = type=http-request,pattern=https:\/\/ios\.baertt\.com\/v5\/article\/info\/get\.json,script-path=https://raw.githubusercontent.com/abclouds/youth-scripts/master/js/youth.js, requires-body=true
中青看点 = type=http-request,pattern=https:\/\/ios\.baertt\.com\/v5\/user\/stay\.json,script-path=https://raw.githubusercontent.com/abclouds/youth-scripts/master/js/youth.js, requires-body=true
中青看点 = type=http-request,pattern=https:\/\/ios\.baertt\.com\/v5\/\w+\/withdraw\d?\.json,script-path=https://raw.githubusercontent.com/abclouds/youth-scripts/master/js/youth.js, requires-body=true
```
#### Shadowrocket(Cron配置): 

```
[Script]
中青看点 = type=cron,script-path=https://raw.githubusercontent.com/abclouds/youth-scripts/master/js/youth.js,cronexpr="1 */6 * * *",timeout=20,enable=true
```
####  Loon:

* [插件地址](https://raw.githubusercontent.com/abclouds/youth-scripts/master/youth/loon.plugin)

 ```
https://raw.githubusercontent.com/abclouds/youth-scripts/master/youth/loon.plugin
 ```
* 本地重写
  
 ```
[Script]
cron "04 00 * * *" script-path=https://raw.githubusercontent.com/abclouds/youth-scripts/master/js/youth.js, enabled=true, tag=中青看点
http-request https:\/\/kd\.youth\.cn\/WebApi\/NewTaskIos\/getTaskList script-path=https://raw.githubusercontent.com/abclouds/youth-scripts/master/js/youth.js, enabled=true, tag=中青看点
http-request https:\/\/ios\.baertt\.com\/v5\/article\/info\/get\.json script-path=https://raw.githubusercontent.com/abclouds/youth-scripts/master/js/youth.js, requires-body=true, enabled=true, tag=中青看点
http-request https:\/\/ios\.baertt\.com\/v5\/user\/stay\.json script-path=https://raw.githubusercontent.com/abclouds/youth-scripts/master/js/youth.js, requires-body=true, enabled=true, tag=中青看点
http-request https:\/\/ios\.baertt\.com\/v5\/\w+\/withdraw\d?\.json script-path=https://raw.githubusercontent.com/abclouds/youth-scripts/master/js/youth.js, requires-body=true, enabled=true, tag=中青看点
```
#### Quantumult X:
   * [远程重写配置](https://raw.githubusercontent.com/abclouds/youth-scripts/main/qx_rewite.txt)
   
```
[rewrite_remote]
https://raw.githubusercontent.com/abclouds/youth-scripts/main/qx_rewite.txt
https://raw.githubusercontent.com/abclouds/youth-scripts/main/qx_youthread.txt
```
   * 本地重写配置
   
```
[rewrite_local]
https:\/\/kd\.youth\.cn\/WebApi\/NewTaskIos\/getTaskList url script-request-header https://raw.githubusercontent.com/abclouds/youth-scripts/master/js/youth.js
https:\/\/ios\.baertt\.com\/v5\/article\/info\/get\.json url script-request-header https://raw.githubusercontent.com/abclouds/youth-scripts/master/js/youth.js
https:\/\/ios\.baertt\.com\/v5\/user\/stay\.json url script-request-body https://raw.githubusercontent.com/abclouds/youth-scripts/master/js/youth.js
https:\/\/ios\.baertt\.com\/v5\/\w+\/withdraw\d?\.json url script-request-body https://raw.githubusercontent.com/abclouds/youth-scripts/master/js/youth.js
```


   * 本地任务配置
   
```
[task_local]
1 */5 * * * https://raw.githubusercontent.com/abclouds/youth-scripts/master/js/youth.js, enabled=true, tag=中青看点
```
###  获取Cookie方法
  * 打开极速版APP，进去我的"任务中心"，提示获取Cookie
  - 打开一篇短文资讯，提示获取阅读请求
  * 多阅读几篇短文，随机获取阅读时长请求(至少1分钟左右，增加时长有关)
  - 正常提现一次，获取提现请求(可选，AC无添加)
  
 >>> [回到顶部](#IOS配置教程)
 
### 食用方法：
youth.js
1.到[重写]-[引用],启动qx_rewite.txt禁用qx_youthread.txt,先获取cookie
签到cookie:
进入app，进入任务中心或者签到一次
阅读请求body&阅读时长:
阅读一篇文章或者视频到获取金币奖励
惊喜红包:
在阅读文章拉下面有个惊喜红包，点击获取

2.手动执行一次定时脚本-”中青看点极速版”,看签到是不是正常
3.到[重写]-[引用],启动qx_youthread.txt禁用qx_rewite.txt,获取文章body
阅读请求body:阅读一篇文章或者视频到获取金币奖励,通知提示body1
4.手动执行一次定时脚本-”中青阅读”,是不是运行正常
5.获取更多的body,一天一般上限7200金币,建议获取200个body

### Nodejs 配置密钥 (Github Actions)

<details>

  <summary>
    <span style="font-size:22">
       Actions Secrets 
    </span>
  </summary>  

| Name | 脚本相关YML | Value分割符 | 必须 / 可选 | 注意事项及样式(其中"xxx"代表任意字符) |
| :-------: | :------: | :-------: | ------ | ------- |
| YOUTH_HEADER | <span style="font-size:18; color:#0000ff"> 中青看点 youth.yml </span> |  #或者换行  | 必须 | 请求地址:  "https://kd.youth.cn/WebApi/NewTaskIos/getTaskList"，  <br>中青签到请求头引用: uid=xxx&cookie_id=xxx&cookie=xxx |
| YOUTH_ARTBODY | 同上 | &或者换行 | 必须 | 请求地址: "https://ios.baertt.com/v5/article/complete"， <br>阅读请求体: p=xxx |
| YOUTH_TIME | 同上 | &或者换行 | 必须 | 请求地址: "https://ios.baertt.com/v5/user/stay.json"，  <br>阅读时长请求体: p=xxx |
| YOUTH_NOTIFY_CONTROL | 同上 | true/false | 可选 | 中青通知开关 <br>默认当转盘次数为50或者100并且余额大于10元时推送通知 |
|  |  |  | - |  |
| YOUTH_READ | <span style="font-size:18; color:#0000ff">中青阅读 youth_read.yml</span> | &或者换行 | 必须 | 请求地址: "https://ios.baertt.com/v5/article/complete"，  <br>阅读请求体: p=xxx |
| YOUTH_START | <span style="font-size:18; color:#0000ff">中青浏览赚 youth_gain.yml</span> | & | 必须 | 请求地址: "https://ios.baertt.com/v5/task/browse_start.json"，  <br>阅读请求体: p=xxx |
| YOUTH_END | 同上 | & | 必须 | 请求地址: "https://ios.baertt.com/v5/task/browse_end.json"，  <br>阅读请求体: p=xxx |

</details>

 
### 注意事项:
 - __提现金额需该请求一致，只更改提现金额无效，默认30元__
 
 * __惊喜红包已下架，现所有请求均采用IOS新版APP任务__



  
  
  
  
