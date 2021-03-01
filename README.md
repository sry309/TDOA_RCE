# 工具说明
**通达OA综合利用工具_20200224**


## 集成POC如下
任意用户登录POC: 4个<br />
SQL注入POC: 2个<br />
后台文件上传POC: 3个<br />
本地文件包含POC: 2个<br />
前台文件上传POC(非WEB目录): 1个<br />
任意文件删除POC: 1个<br />

<br />
<br />

## 工具面板截图
![image.png](https://cdn.nlark.com/yuque/0/2021/png/516736/16141329552479f1b3b4d901946658925b36d4a6c141b.png#align=left&display=inline&height=518&margin=%5Bobject%20Object%5D&name=image.png&originHeight=518&originWidth=716&size=36652&status=done&style=stroke&width=716)

<br />
<br />

## 工具利用流程
**1.优先利用本地文件包含漏洞**
<br />
原因是本地文件包含漏洞, 配合前台文件上传可以直接getshell, 无需获取有效Cookie<br />

**2.若本地文件包含漏洞利用失败, 其次利用任意用户登录漏洞与SQL注入漏洞**
<br />
这两个漏洞的利用方式集成在了"获取Cookie"按钮上<br />
共计6个POC, 其中任意一个POC利用成功<br />
都会自动停止, 并自动填充有效的Cookie到工具上<br />
获取有效Cookie后, 即可选择后台文件上传一键利用<br />
如目标存在弱口令, 可手动填写有效Cookie后配合文件上传一键利用<br />
**如目标存在弱口令, 可手动填写有效Cookie后配合文件上传一键利用**<br />

### 特定版本v11.6存在任意文件删除漏洞的利用
当目标为v11.6版本时, 一键利用即可(该漏洞利用存在一些风险).<br />
代码实现流程如下:<br />
	删除auth.inc.php文件
    上传webshell
    上传auth.inc.php源文件
    上传处理文件(移动auth.inc.php到原本位置,删除自身)
    检测auth.inc.php源文件是否恢复

<br />
<br />
<br />
本工具仅供安全测试人员运用于授权测试, 禁止用于未授权测试, 违者责任自负.


