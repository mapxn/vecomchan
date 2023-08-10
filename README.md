# Vercel wecomchan

The wecomchan project running on vercel serverless function.

## Deploy Your Own

Deploy your own vercel project with Vercel.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/import/project?template=https://github.com/mapxn/vecomchan)

## Add your custom Environment Variables
|No.|Name|Value                       |
|:---|:---|:--------------------------|
|1|wecom_id| your corp id             |
|2|app_1| your app name, customelize|
|3|send_key_1| your send key,customlized|
|4|wecom_agentid_1| your AgentId        |
|5|wecom_secret_1| your Secret          |
|6|...| ...|
|7|app_7| your app name, customelize|
|8|send_key_7| your send key,customlized|
|9|wecom_agentid_7| your AgentId        |
|10|wecom_secret_7| your Secret         |

## Redeploy your project
You need redeploy your project and waiting for the Environment Variables take effect.


## Enjoy

### use case

POST the following content to the public network access address of the function in json format.

| column | description                                                       | is necessary              |
|--------|-------------------------------------------------------------------|---------------------------|
| app    | your app name                                                     | yes                       | 
| key    | your sendkey                                                      | yes                       |
| type   | text, image, markdown or file                                     | no, default value is `text` |
| msg    | Message body (Base64 encoding of text or image/file to be pushed) | yes                       |
| uid    | user id, it looks like `zhangsan\|lisi\|wangwu`                   | no, the default value is `@all` |

Example:

Curl:
```bash
curl --silent --location 'https://your-custom.domain.com/api/' \
--header 'Content-Type: application/json' \
--data '{
    "app": "app1",
    "key": "abcdefg1234",
    "type": "text",
    "msg": "CURL test!"
}'
```

Python:
```python
import requests
import json

url = "https://vechat.txwd.eu.org/api/"

payload = json.dumps({
  "app": "app1",
  "key": "abcdefg1234",
  "type": "text",
  "msg": "Python test!"
})
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

Various type of data that you can have a try:

```
{"app":"test", "key":"123", "msg": "Hello, World!"}
```

```
{"app":"test", "key":"123", "msg": "Hello, World!", "uid": "zhangsan"}
```

```
{"app":"test", "key":"123", "type": "markdown", "msg": "**Markdown Here!**"}
```

```
{
    "app": "test",
    "key": "123",
    "type": "text",
    "msg": "Support<a href=\"https://www.baidu.com\">hyperlink</a>"
}
```