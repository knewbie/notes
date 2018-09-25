# Mac使用问题总结。

## mac应用总结
    软件[Cracked]获取地方:[!macx](http://soft.macx.cn), [waitsun](https://www.waitsun.com)
   `Alfred`, `Dash` etc

## mac安装破解软件提示已损坏
**解决问题办法：**
    系统偏好设置 -> 安全性与隐私 -> 通用 -\> 选择“任何来源”
    "通用”里如果没有“任何来源”这个选项:
        显示"任何来源"选项在控制台中执行：
        `sudo spctl --master-disable`
        不显示"任何来源"选项（macOS 10.12默认为不显示）在控制台中执行：
        `sudo spctl --master-enable`


