# Vercel wecomchan

The wecomchan project running on vercel serverless function.

## Deploy Your Own

Deploy your own vercel project with Vercel.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/import/project?template=https://github.com/mapxn/vercel-wecomchan)

## Add your custom Environment Variables
|No.|Name| Value                     |
|:---|:---|:--------------------------|
|1|wecom_id| your corp id              |
|2|send_key| your send key,customlized |
|3|wecom_agentid| your AgentId              |
|4|wecom_secret| your Secret               |

## Redeploy your project
You need redeploy your project and waiting for the Environment Variables take effect.


## Enjoy

### use case

POST the following content to the public network access address of the function in json format.

| column | description                      | is necessary              |
|--------|----------------------------------|---------------------------|
| key    | 设置的 sendkey                      | yes                       |
| type   | text, image, markdown or file    | no, default value was `text` |
| msg    | 消息主体(需要推送的文本或图片/文件的 Base64 编码)   | yes                       |
| uid    | user id, it looks like `zhangsan\|lisi\|wangwu` | no, the default value is `@all` |

Example:

```
{"key":"123", "msg": "Hello, World!"}
```

```
{"key":"123", "msg": "Hello, World!", "uid": "zhangsan"}
```

```
{"key":"123", "type": "markdown", "msg": "**Markdown Here!**"}
```

```
{
    "key": "123",
    "type": "text",
    "msg": "Support<a href=\"https://www.baidu.com\">hyperlink</a>"
}
```