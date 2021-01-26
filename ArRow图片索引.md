> 此文档阐述了 ArRow 系统中的 3 种图片索引方式。

为了增强图片复用性以节约流量，ArRow 使用了 3 种图片地址：ID、Url、Base64。

# ID

ID 索引一般在图片可公开且复用率较高的情况下使用，它的特征即以 `@id=` 开头。

解析它的方式非常简单，仅需将"@id="后的字符串追加在地址 `https://www.atatc.net/arrow/resources/img/` 后即可。

例如 `@id=1.jpeg`，则其指向 `https://www.atatc.net/arrow/resources/img/1.jpeg`。

# Url

Url 索引一般在图片本就在外部固定地址的情况下使用，它的特征即以"@url="开头。

解析它的方式更为简单，"@url="后的字符串即图片地址。

例如 `@url=https://www.atatc.net/arrow/resources/img/1.jpeg`，则其指向 `https://www.atatc.net/arrow/resources/img/1.jpeg`。

# Base64

Base64 索引一般在图片不可公开或复用率较低的情况下使用，它没有特征，如果你得到的图片索引不符合上述两种索引的特征，那它就是 Base64 索引。

解析它的方式不大简单。顾名思义，这种索引本身就是图片的 Base64 编码格式，你需要根据不同平台的方法解析它。

例如 `...`，在安卓平台，则需要将这段字符串解码为 Bitmap 对象然后使用 Glide 或直接加载在 ImageView 中。

