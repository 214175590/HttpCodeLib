# HttpCodeLib
C# ,Powerful and easy Http crawler framework.Simple and crude.

If you want to get more help, please visit http://bbs.msdn5.com

![xuanjibbs](http://bbs.msdn5.com/static/image/common/logo.png "Msdn5 Logo")
```C#
/* 
 * 当前版本:v3.3.16.07.01
 * 主版本号 3.3
 * 次版本号 16.07.01(更新日期)
 * 玄机网C# 基类库 Http请求类
 * 基础功能1:基于HttpWebRequest方式 同步/异步 提交数据 包含(Get/Post)
 * 基础功能2:基于Wininet系统API方式提交数据 包含(Get/Post)
 * 基础功能3:集合常用处理方法.处理页面结果/HTML数据更快捷
 * 
 * Coding by 君临
 * 07-12/2014
 * 
 * 使用HttpCode时,请先引用 
 * System.Web (Framework 2.0/4.0 都需要添加)
 * System.Configuration(Framework 2.0/4.0 都需要添加)
 *
 *
 * 如需使用系统自带的Json转换类库,则需要引用  System.Web.Extensions( Framework 2.0不需要 )   具体方法请参考下文链接 与注释
 * 具体引用方法,请查看链接
 * http://bbs.msdn5.com/thread-11-1-1.html  
 * 玄机论坛官方QQ群: 16885911   期待你的加入.! 
*/
            
            
            
            
            
            
             01/07/2016
　　　　　　* 重载懒人方法 一键请求,增加代理
　　　　　　* 修正 httpresults没有被初始化的bug.
　　　　　　* 修正 使用字符串Cookie自动维护时,没有将新内容传递给 httpresults对象
　　　　　　* 修正异步方法自动处理字符串cookie Bug


　　　　　　24-05/2016
　　　　　　!!!!重构内核!!!!
　　　　　　修正所有冗余内核代码.
　　　　　　同步/异步均采用相同逻辑处理.
　　　　　　加强网页编码识别能力
　　　　　　重构HTML/Unicode编码解析方法
　　　　　　优化数据解析/数据提取方法
　　　　　　优化所有模块,清除所有冗余代码逻辑更清晰!
　　　　　　
　　　　　　修正 "服务器提交了协议冲突. Section=ResponseHeader Detail=CR 后面必须是 LF"问题
　　　　　　【解决方案】服务器提交了协议冲突. Section=ResponseHeader Deta...
　　　　　　http://bbs.msdn5.com/thread-1125-1-1.html


　　　　　　修正 "从传输流收到意外的 EOF 或 0 个字节 "
　　　　　　【解决方案】从传输流收到意外的 EOF 或 0 个字节
　　　　　　http://bbs.msdn5.com/thread-1126-1-1.html




　　　　　　16-04/2016
　　　　　　更新冗余,
　　　　　　修正多线程下并发问题.
　　　　　　修正编码解码核心代码...
　　　　　　20-01/2016
　　　　　　修正编码识别的一个小bug.
　　　　　　去除Json转换默认引用,需要时请自行开放.
　　　　　　11-27/2015
　　　　　　增加PostEncoding 允许自定义Post提交数据时的编码.
　　　　　　//例
　　　　　　items.PostEncoding=Encoding.UTF8; //设置提交请求时编码为UTF8 注意,默认为Default,如非必要请勿修改
　　　　　　修正异步请求时超时BUG
　　　　　　修正异常处理BUG
　　　　　　11-15/2015
　　　　　　修正 编码解析异常时Bug 感谢 不懂 635****0 反馈
　　　　　　增加 获取服务器时间方法(从响应头中获取Date头数据)
　　　　　　增加 GMT时间与本地时间互转方法
　　　　　　增加 API 设置本地电脑时间
　　　　　　增加 API 获取本地地电脑时间
　　　　　　增加 急速请求(仅返回请求头,不解析与请求具体数据)
　　　　　　07-11-2015
　　　　　　修正 编码识别的正确率(减少更多识别错误导致的web乱码)
　　　　　　修改 HttpItems 对象增加Encoding对象 设置(如果不指定,默认为每次自动识别网页编码 如非必要请勿修改)
　　　　　　修改 HttpItems 原本对象Encoding字符串为EncodingStr 支持以字符串方式获取编码类型.
　　　　　　04/11-2015
　　　　　　修正 无视编码时个别请求错误无法直接识别bug
　　　　　　修正 HttpHelpers异步请求时Bug.
　　　　　　修正 若干冗余
　　　　　　增加 自动处理字符串Cookie方法
　　　　　　增加 Wininet 方式 使用代理 请求图片
　　　　　　增加 Wininet 方式 使用代理 GET/POST 
　　　　　　增加 Wininet 方式 允许添加自定义Cookie至请求(在JS产生Cookie时使用)
　　　　　　增加 以上几种方式至Demo
　　　　　　06-10/2015
　　　　　　修正 wininet Post提交问题.
　　　　　　修正 懒人方法一键Post[xjhttp] Bug
　　　　　　修正 Wininet 若干BUG(非重要修正)
　　　　　　增加 字符串Cookie使用Demo
　　　　　　增加 Wininet 自定义协议头Demo
　　　　　　30-08/2015
　　　　　　修正 FromUnicodeString 中书写BUG.感谢 纳兰小寒 反馈
　　　　　　修正 iso-8859-1 编码为 utf8.
　　　　　　修正 Wininet代理方法重载为(GetHtmlPro方法)
　　　　　　修正 自动识别编码书写bug.
　　　　　　26-08/2015
　　　　　　修复自动获取编码的Bug.
　　　　　　新增Wininet 支持携带代理请求网页.
　　　　　　新增方法描述
　　　　　　/// 

　　　　　　 /// 重载提交数据(允许使用代理)
　　　　　　 /// 

　　　　　　 /// 请求地址　　　　　　 /// 提交的数据(Get时为空)　　　　　　 /// 代理地址(IP:端口 例如 127.0.0.1:8888)　　　　　　 /// 设置cookie,例如 JS增加的cookie.如非需要可不填写　　　　　　 /// 设置数据头,如非需要可不填写　　　　　　 /// 是否允许跳转(允许3xx 跳转)　　　　　　 /// 
　　　　　　 public MemoryStream GetHtmlPro(string Url, string Postdata, string proxy = null, string subcookie = null, string subheader = null, bool isMoved = true)
　　　　　　26-07/2015
　　　　　　增加wininet 超时判断.
　　　　　　如果需要设置超时,请设置
　　　　　　WininetTimeOut 属性
　　　　　　设置后请求结果将返回 长度为零的字符串 ,即""字符.
　　　　　　默认不触发超时(WininetTimeOut 为0)
　　　　　　注意: 此方法非官方方法,官方wininet存在超时bug,使用Thread.Join来完成伪超时操作.
　　　　　　设置属性后每次请求都会阻塞 设置的毫秒数 .如非必要,请勿使用...
　　　　　　25-07/2015
　　　　　　修正 GetStringMid bug
　　　　　　修正 自动转换编码时转换错误bug
　　　　　　优化部分代码,去除冗余...
　　　　　　01-07/2015
　　　　　　修正异步代理超时bug
　　　　　　20-06 / 2015
　　　　　　新增 Right 方法 取文本右边 
　　　　　　默认取出右边所有文本,如果需要取固定长度请设置 length参数
　　　　　　异常则返回空字符串
　　　　　　新增 Left 方法 取文本左边
　　　　　　默认取出左边所有文本,如果需要取固定长度请设置 length参数
　　　　　　异常则返回空字符串
　　　　　　优化 FromUnicodeString 方法, Unicode字符转汉字. 
　　　　　　默认处理 \u7384\u673a\u8bba\u575b 
　　　　　　如果遇到 &7384 &673a &8bba &575b 请对SplitString赋值为&
　　　　　　优化异常时读取异常页面代码方法.
　　　　　　优化部分冗余代码
　　　　　　11-06 /2015
　　　　　　*修改默认timeout为15s..
　　　　　　增加 文字Cookie添加到Container对象方法,不用再传递domain了.自动从stringcookie中分析 更新失败时,返回原来的CookieContainer对象
　　　　　　最后一个domain默认为"",自动从字符串cookie中获取,如果获取失败返回原来的Container对象,那么需要手动填写domain地址
　　　　　　方法名 AddCookieToContainer()
　　　　　　使用方法: 
　　　　　　cc = AddCookieToContainer(cc,hr.Cookie);
　　　　　　cc 为当前自动处理cookie对象,
　　　　　　hr.Cookie 为当前请求后返回的字符串Cookie
　　　　　　优化部分代码
　　　　　　增加 Unicode编码转换的方法. FromUnicodeString
　　　　　　09-06/2015
　　　　　　*修复一个书写错误导致的bug..
　　　　　　07-06 /2015
　　　　　　修复 SetRequest 方法至 GetHttpRequestData() 为了准确捕获异常
　　　　　　增加 JsonToObject(Json转实体对象) ObjectToJson(实体对象转Json字符串) (Json转换为实体对象.实体对象请从 玄机宝盒转换代码) 
　　　　　　仅Framework 4.0可用 需要自行引用命名空间 System.Web.Extensions 
　　　　　　Framework 2.0 下请使用外部解析方法
　　　　　　增加 GetHtmlTitle(html数据) 提取网页Title
　　　　　　增加 GetMidHtml(原始Html,起始字符串,终止字符串) 取文本中间的其他写法
　　　　　　增加 ReplaceNewLine 过滤所有换行
　　　　　　增加 StripHTML 过滤html标签
　　　　　　增加 GetImgList 获取所有的Img标签 
　　　　　　增加 GetAList 获取所有的A标签
　　　　　　增加 RunJsMethod 执行js代码(JS代码,参数,调用方法名,方法名[默认Eval 可选Run])
　　　　　　增加 HttpResults 中的属性: 
　　　　　　 
　　　　　　 ResponseUrl 获取响应结果的URL(可获取自动跳转后地址) ,如果获取跳转后地址失败,请使用RedirectUrl属性,并设置HttpItems对象的Allowautoredirect =false;
　　　　　　 
　　　　　　 RedirectUrl 获取重定向的URL ;使用本属性时,请先关闭自动跳转属性;设置方法如下:设置HttpItems对象的Allowautoredirect =false; 
　　　　　　 20-05 /2015
　　　　　　修复 在Http1.0/Http1.1 协议下 服务端遇到错误直接断开连接,此时类库只能获取到状态码,无法获取相信信息的bug
　　　　　　异步模式: AsyncResponseData / 同步模式: GetHttpRequestData 均修复此bug.
　　　　　　清理代码冗余数据.删除测试上传方法(已过时)
　　　　　　修正部分编码格式问题. 
　　　　　　29-04/2015
　　　　　　增加 HttpItems 中的 Expect100Continue属性 
　　　　　　属性介绍:
　　　　　　https://msdn.microsoft.com/zh-cn ... r.expect100continue(v=VS.80).aspx
　　　　　　08-05/2015
　　　　　　具体使用方法请见demo 
　　　　　　新增 ClaerIECookie 删除IE Cookie
　　　　　　新增 SetIeCookie 设置IE Cookie
　　　　　　 新增 OpenUrl(string url, int openType = 0) 方法说明:打开指定URL openType:0使用IE打开,!=0 使用默认浏览器打开
　　　　　　新增 RunCmd 方法 参数为CMD 调用的命令
　　　　　　调用 new() XJHTTP().ClaerIECookie()
　　　　　　 new() XJHTTP().SetIeCookie()
　　　　　　 new() XJHTTP().RunCmd()
　　　　　　 new() XJHTTP().OpenUrl()
　　　　　　 
　　　　　　如果失败,请自行执行以下语句:
　　　　　　 //获取旧的Cookie 函数 例子
　　　　　　 StringBuilder cookie = new StringBuilder(new String(' ', 2048));
　　　　　　 int datasize = cookie.Length;
　　　　　　 bool b = InternetGetCookie(GetUrl, null, cookie, ref datasize);
　　　　　　 //删除旧的
　　　　　　 foreach (string fileName in System.IO.Directory.GetFiles(System.Environment.GetFolderPath(Environment.SpecialFolder.Cookies)))
　　　　　　 {
　　　　　　 if (fileName.ToLower().IndexOf("expires") > 0)
　　　　　　 {
　　　　　　 System.IO.File.Delete("expires");
　　　　　　 }
　　　　　　 }
　　　　　　 //设置新COOKIE 函数
　　　　　　 参数说明
　　　　　　 GetUrl: 需要设置COOKIE的URL
　　　　　　 name: COOKIE split后的name
　　　　　　 value:COOKIE split后的value
　　　　　　 InternetSetCookie(GetUrl, name, value);
　　　　　　 foreach (string c in NewCookie.Split(';'))
　　　　　　 {
　　　　　　 string[] item = c.Split('=');
　　　　　　 string name = item[0];
　　　　　　 string value = item[1] + ";expires=Sun,22-Feb-2099 00:00:00 GMT";
　　　　　　 InternetSetCookie(GetUrl, name, value);
　　　　　　 InternetSetCookie(GetUrl, name, value);
　　　　　　 InternetSetCookie(GetUrl, name, value);
　　　　　　 }
　　　　　　14-04/2015
　　　　　　修正 添加代理时不能使用 127.0.0.1:8888 这种方式 重构了下代码 感谢(永远的沉默 ofnhkb1(8224xxx))反馈
　　　　　　增加Demo中使用代理请求
　　　　　　所更新方法全部在XJHttp类中
　　　　　　增加 HttpResults 中的StatusCode StatusDescription 属性, 感谢(永远的沉默 ofnhkb1(8224xxx))反馈
　　　　　　StatusCode 用于获取当前请求的状态码.
　　　　　　StatusDescription 用户获取当前请求状态码描述.
　　　　　　当请求异常时 StatusCode:NotFound StatusDescription:异常信息描述
　　　　　　异步与同步都有这两个属性.
　　　　　　增加 GetString2Base64 转换普通字符串为base64
　　　　　　增加 GetStringbyBase64 转换base64字符串为普通字符串
　　　　　　//代理访问IP138获取当前IP
　　　　　　item = new HttpItems()
　　　　　　 {
　　　　　　 URL = "http://1111.ip138.com/ic.asp",
　　　　　　 ProxyIp = "127.0.0.1:8888"
　　　　　　 };
　　　　　　 string info= http.GetHtml(item).Html;
　　　　　　所更新方法全部在XJHttp类中
　　　　　　增加 GetTime 方法;将时间戳转换为C#的DateTime,配合gettimebyjs
　　　　　　增加 Bytes2HexString 方法;将字节数组转化为十六进制字符串，每字节表示为两位
　　　　　　增加 HexToStr方法;将普通字符串转化为十六进制
　　　　　　增加 HexString2Bytes 方法;将十六进制字符串转化为字节数组
　　　　　　增加 GetAscii2string方法;将byte数组转换为AscII字符
　　　　　　修复上传文件bug.
　　　　　　取消测试上传文件方法
　　　　　　所更新方法全部在XJHttp类中
　　　　　　增加DownLoad方法[使用HttpCode] Get
　　　　　　增加WebClientDonwnLoad方法 Get
　　　　　　增加UploadPost方法 Post
　　　　　　修复请求异常bug.
　　　　　　修复Cookie处理Bug
　　　　　　08-12/2014
　　　　　　增加 " 取文本中间 "方法 GetStringMid
　　　　　　增加 "批量取文本中间" 方法 GetStringMids
　　　　　　增加 "url编码,url解码方法" UrlEncoding / UrlDecoding
　　　　　　增加 Webbrowser 获取Cookie到HttpCode使用方法Demo
　　　　　　30-11/2014
　　　　　　修正 Wininet 在framework 4.0下的"PInvoke调用导致堆栈不对称" 异常. 
　　　　　　修正在异步模式中的Hander处理
　　　　　　修正异步模式中的Cookie处理
　　　　　　更改 获取Wininet的Cookie方法为 GetCookieByWininet
　　　　　　新增 字符串类型Cookie处理方法 ClearCookie 去除Cookie中的无用项.
　　　　　　增加一键获取JS时间戳方法 (13位) 更改GetTime 方法为 GetTimeByJs
　　　　　　增加一键获取C#时间戳方法(10位) 更改GetTimeStamp方法为 GetTimeByCSharp
```