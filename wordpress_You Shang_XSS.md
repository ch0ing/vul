# You Shang<=1.0.1 Authenticated Stored Cross-Site Scripting(XSS)

## Description

    The plugin doesn't properly sanitise qrcode links, which result into a Stored Cross-Site Scripting(XSS).

## Affects Plugins

    Cookie Bar<=1.0.1
    https://wordpress.org/plugins/you-shang/

## Author

    yangshengcheng@webray.com.cn inc

## Proof of Concept

Open wechat switch and edit the "qrcode links " text area to "
'''
http://127.0.0.1/wo"onerror=alert(1);\&quot;
'''

![image-20210730181143910](/img/image-20210730181143910.png)

Visit the posts page. We can see the alert page.


![image-20210730180550253](/img/image-20210730180550253.png)

![image-20210730180628529](/img/image-20210730180628529.png)
