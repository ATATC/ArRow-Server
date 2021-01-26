> 此文档列举了 ArRow 服务器通信接口支持的命令。
> 如果你尚不了解 ArRow 服务器通信接口的调用方法，请阅读[《ArRow通信接口-规范》](ArRow通信接口-规范.md)相关文档。
>
> <span style="color: orange;">这是需要 Token 的命令</span>
>
> <span style="color: red;">这是需要管理员权限的命令</span>

# 目录

- ### [测试组](#测试组)

  - #### [hello](#hello)

  - #### [adv](#adv)

  - #### [args](#args)

- ### [信息组](#信息组)

  - #### [version](#version)

  - #### [latest_app_version](#latest_app_version)

  - #### [copyright](#copyright)

- ### [后台组](#后台组)

  - #### [count_user](#count_user)

  - #### [count_articles](#count_articles)

- ### [数据组](#数据组)

  - #### [get_banner](#get_banner)

1. # <span id="测试组">测试组</span>

   1. ## <span id="hello">hello</span>

      1. ### 应答

         "nice_to_meet_you"

      2. ### 副词

         不支持副词。

      3. ### 参数

         不支持参数。

      4. ### 例

         ```json
         {"command": "hello", "adv": "", "args": ""}
         ```

         ```
         nice_to_meet_you
         ```

   2. ## <span id="adv">adv</span>

      1. ### 应答

         返回请求中的副词。

      2. ### 副词

         任意。

      3. ### 参数

         不支持参数。

      4. ### 例

         ```json
         {"command": "adv", "adv": "adv_test", "args": ""}
         ```

         ```
         adv_test
         ```

   3. ## <span id="args">args</span>

      1. ### 应答

         返回请求中的参数。

      2. ### 副词

         不支持副词。

      3. ### 参数

         任意。

      4. ### 例

         ```json
         {"command": "args", "adv": "", "args": "W3sibmFtZSI6ICJsYW5ndWFnZSIsICJ6aC1jbiJ9LCB7Im5hbWUiOiAiLi4uIiwgInZhbHVlIjogIi4uLiJ9XQ=="}
         ```

         ```
         ["language": "zh-cn", "...": "..."]
         ```

2. # <span id="信息组">信息组</span>

   1. ## <span id="version">version</span>

      1. ### 应答

         返回当前服务器版本。

      2. ### 副词

         不支持副词。

      3. ### 参数

         不支持参数。

      4. ### 例

         ```json
         {"command": "version", "adv": "", "args": ""}
         ```

         ```
         2.7.4
         ```

   2. ## <span id="latest_app_version">latest_app_version</span>

      1. ### 应答

         返回最新的 APP 版本。

      2. ### 副词

         | 字符串  | 作用           |
         | :------ | -------------- |
         | ""      | 仅正式版本。   |
         | "beta"  | 包括公测版本。 |
         | "alpha" | 包括内测版本。 |

      3. ### 参数

         | 名称 | 值        | 作用                        |
         | ---- | --------- | --------------------------- |
         | "os" | "android" | 返回安卓 APP 最新版本。     |
         |      | "ios"     | 返回 iOS APP 最新版本。     |
         |      | "windows" | 返回 Windows APP 最新版本。 |
         |      | "macos"   | 返回 Mac OS APP 最新版本。  |

      4. ### 例

         ```json
         {"command": "latest_app_version", "adv": "beta", "args": "W3sibmFtZSI6ICJvcyIsICJ2YWx1ZSI6ICJhbmRyb2lkIn1d"}
         ```

         ```
         1.9.8@β0.0.8
         ```

   3. ## <span id="copyright">copyright</span>

      1. ### 应答

         返回服务器的版权信息，可用于区分官方服务器与镜像服务器。

      2. ### 副词

         不支持副词。

      3. ### 参数

         不支持参数。

      4. ### 例

         ```json
         {"command": "copyright", "adv": "", "args": ""}
         ```

         ```
         Copyright ©️ 2020 ATATC All rights reserved.
         ```

3. # <span id="后台组">后台组</span>

   1. ## <span id="count_user" style="color: red;">count_user</span>

      1. ### 应答

         返回用户总数。

         或以下错误信息：

         | 字符串              | 意义                     |
         | ------------------- | ------------------------ |
         | "lack_of_arguments" | 缺少参数。               |
         | "invalid_token"     | Token 无效。             |
         | "access_denied"     | Token 不具有管理员权限。 |

      2. ### 副词

         不支持副词。

      3. ### 参数

         | 名称    | 值           | 作用       |
         | ------- | ------------ | ---------- |
         | "token" | 客户端 Token | 验证身份。 |

      4. ### 例

         ```json
         {"command": "count_user", "adv": "", "args": "W3sibmFtZSI6ICJ0b2tlbiIsICJ2YWx1ZSI6ICIuLi4ifV0="}
         ```

         ```
         1
         ```

   2. ## <span id="count_articles" style="color: red;">count_articles</span>

      1. ### 应答

         返回文章总数。

         或以下错误信息：

         | 字符串              | 意义                     |
         | ------------------- | ------------------------ |
         | "lack_of_arguments" | 缺少参数。               |
         | "invalid_token"     | Token 无效。             |
         | "access_denied"     | Token 不具有管理员权限。 |

      2. ### 副词

         不支持副词。

      3. ### 参数

         | 名称    | 值           | 作用       |
         | ------- | ------------ | ---------- |
         | "token" | 客户端 Token | 验证身份。 |

      4. ### 例

         ```json
         {"command": "count_articles", "adv": "", "args": "W3sibmFtZSI6ICJ0b2tlbiIsICJ2YWx1ZSI6ICIuLi4ifV0="}
         ```

         ```
         1
         ```

4. # <span id="数据组">数据组</span>

   1. ## <span id="get_banner">get_banner</span>

      1. ### 应答

         返回横幅信息，一个 json 列表，如下：

         ```json
         [{"title": "...", "titleColor": "...", "content": "...", "contentColor": "...", "backgroundImg": "...", "articleID": "..."}, ...]
         ```

         | 名称            | 值的格式                             | 意义                   | 是否可能不含或为空 |
         | --------------- | ------------------------------------ | ---------------------- | ------------------ |
         | "title"         |                                      | 横幅的标题。           | 否                 |
         | "titleColor"    | 十六进制颜色无透明度，如"#FFFFFF"。  | 横幅的标题的字体颜色。 | 是                 |
         | "content"       |                                      | 横幅的简介。           | 是                 |
         | "contentColor"  | 十六进制颜色无透明度，如"#FFFFFF"。  | 横幅的简介的字体颜色。 | 否                 |
         | "backgroundImg" | [ArRow 图片索引](ArRow图片索引.md)。 | 横幅的背景图片。       | 是                 |
         | "articleID"     | [ArRow 文章索引](ArRow文章索引.md)。 | 横幅指向的文章。       | 否                 |

      2. ### 副词

         不支持副词。

      3. ### 参数

         不支持参数。

      4. ### 例

         ```json
         {"command": "get_banner", "adv": "", "args": ""}
         ```

         ```json
         [{
           "title": "title 1", "titleColor": "#FFFFFF", "content": "content 1", "backgroundImg": "@id=1.jpeg", "articleID": "@id=AN7EopK"
}, {
           "title": "title 2", "titleColor": "", "articleID": "@id=AN7EopL"
         }]
         ```
         
         

