# EzCheckInSchool
最简单的完美校园自动健康打卡，基于Github Actions免服务器运行。

- 多人打卡👨‍👩‍👧‍👦
- 仅需学号姓名🎫
- 随机校内经纬度🗺️
- 打卡结果微信推送💬
- 随机温度(36.2℃-36.5℃)🌡
- 校内打卡三次:06:05,12:35,21:05🕑

**Github Actions定时任务可能出现几分钟的误差**

**推荐迁移到腾讯云云函数，修改`input()`为对应字符串后设置定时触发器即可**

## 更新日志

部分老版本可能存在打卡失败 Gateway timeout 504错误，建议更新新版本。

2020.9.16 21:35 更新多用户版，使用WxPusher，致谢[@themanforfree](https://github.com/themanforfree)

2020.9.14 12:40 使用方法优化

## 使用方法    

首先，点击页面上方`Star`和`Fork`，此时你将得到复制的项目

![Star and fork](https://s1.ax1x.com/2020/09/16/w22nDx.png)

点击下方链接微信扫码关注，以便获取打卡结果推送

[Wechat QRCode](http://wxpusher.zjiecode.com/api/qrcode/FHFBNBtuM9q4rmR2AS2okzHcBEoh9pFa1JsseEb0PXixltPGFh3UFaw0qwLH4sSJ.jpg)

关注后点击我的->我的UID，获取你的UID

![WxPusher UID](https://s1.ax1x.com/2020/09/16/w2W6H0.png)

接下来你需要设置`Secret` Fork的项目->Settings->Secret->New Secret

![New Secert](https://s1.ax1x.com/2020/09/16/w27Awd.png)

打开完美校园健康打卡，参照打卡页面上方个人信息及如下表格设置

![Add Secert](https://s1.ax1x.com/2020/09/15/wcCRvn.png)

给几个人打就用英文逗号分开填写几个

|Name|Value|示例|
| :-----| :---- | :---- |
|`DEPT_TEXT`|`学院-专业-班级1,2,...`|`理学院-应用物理学-应物1901,理学院-应用物理学-应物1902`|
|`STU_ID`|`学号1,2,...`|`201912340101,201912340201`|
|`STU_NAME`|`姓名1,2,...`|`小明,小华`|
|`WX_UID`|`WxPusher UID1,2,...`|`UID_abcdefghijklm,UID_nopqrstuvwxyz`| 

以上步骤完成后

Fork的项目->Action->I understand... 开启Actions

回到项目主页，修改[README.md](/README.md)随便加几个空格即可

**首次开启若不在打卡时间将会重打早间卡作为测试**

设置完成打卡后打卡时间内会每天自动打卡三次，第一次使用请观察效果。

**注意：本项目默认学校为河南工业大学，其他学校请自行抓包修改代码。**

|Method|URL|修改|
| :-----| :---- | :---- |
|`POST`|`https://reportedh5.17wanxiao.com/sass/api/epmpics`|`main.py`|
|`POST`|`https://reportedh5.17wanxiao.com/api/passcard/queryOrg`|`response.json`|

### 捐赠
最后，如果觉得这个项目对你有帮助的话

![Donate](https://s1.ax1x.com/2020/09/15/wcPVqP.png)

## 友情链接

https://github.com/YooKing/HAUT_autoCheck - 学习Python语法参考

https://github.com/LovelyWhite/Haut-AutoCheckin - iOS捷径版

https://github.com/themanforfree/EzCheckInSchool-MultiUser - 多用户想法

