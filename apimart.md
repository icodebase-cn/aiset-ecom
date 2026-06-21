> ## Documentation Index
> Fetch the complete documentation index at: https://docs.apimart.ai/llms.txt
> Use this file to discover all available pages before exploring further.

# GPT-Image-2 图像生成

>  - 异步处理模式，返回任务ID用于后续查询
- 基于 OpenAI Images 兼容协议，支持文生图 / 图生图
- 支持 13 种图片比例，通过 `size` 字段传入
- 通过 `resolution`（`1k` / `2k` / `4k`）控制实际输出像素档位
- 参考图最多 16 张，支持 URL 与 base64 混填
- 按分辨率档位（1K / 2K / 4K）计费 

<RequestExample>
  ```bash cURL theme={null}
  curl --request POST \
    --url https://api.apimart.ai/v1/images/generations \
    --header 'Authorization: Bearer <token>' \
    --header 'Content-Type: application/json' \
    --data '{
      "model": "gpt-image-2",
      "prompt": "一只橘猫坐在窗台上看夕阳，水彩画风格",
      "n": 1,
      "size": "16:9",
      "resolution": "2k"
    }'
  ```

  ```python Python theme={null}
  import requests

  url = "https://api.apimart.ai/v1/images/generations"

  payload = {
      "model": "gpt-image-2",
      "prompt": "一只橘猫坐在窗台上看夕阳，水彩画风格",
      "n": 1,
      "size": "16:9",
      "resolution": "2k"
  }

  headers = {
      "Authorization": "Bearer <token>",
      "Content-Type": "application/json"
  }

  response = requests.post(url, json=payload, headers=headers)

  print(response.json())
  ```

  ```javascript JavaScript theme={null}
  const url = "https://api.apimart.ai/v1/images/generations";

  const payload = {
    model: "gpt-image-2",
    prompt: "一只橘猫坐在窗台上看夕阳，水彩画风格",
    n: 1,
    size: "16:9",
    resolution: "2k"
  };

  const headers = {
    "Authorization": "Bearer <token>",
    "Content-Type": "application/json"
  };

  fetch(url, {
    method: "POST",
    headers: headers,
    body: JSON.stringify(payload)
  })
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
  ```

  ```go Go theme={null}
  package main

  import (
      "bytes"
      "encoding/json"
      "fmt"
      "io/ioutil"
      "net/http"
  )

  func main() {
      url := "https://api.apimart.ai/v1/images/generations"

      payload := map[string]interface{}{
          "model":      "gpt-image-2",
          "prompt":     "一只橘猫坐在窗台上看夕阳，水彩画风格",
          "n":          1,
          "size":       "16:9",
          "resolution": "2k",
      }

      jsonData, _ := json.Marshal(payload)

      req, _ := http.NewRequest("POST", url, bytes.NewBuffer(jsonData))
      req.Header.Set("Authorization", "Bearer <token>")
      req.Header.Set("Content-Type", "application/json")

      client := &http.Client{}
      resp, err := client.Do(req)
      if err != nil {
          panic(err)
      }
      defer resp.Body.Close()

      body, _ := ioutil.ReadAll(resp.Body)
      fmt.Println(string(body))
  }
  ```

  ```java Java theme={null}
  import java.net.http.HttpClient;
  import java.net.http.HttpRequest;
  import java.net.http.HttpResponse;
  import java.net.URI;

  public class Main {
      public static void main(String[] args) throws Exception {
          String url = "https://api.apimart.ai/v1/images/generations";

          String payload = """
          {
            "model": "gpt-image-2",
            "prompt": "一只橘猫坐在窗台上看夕阳，水彩画风格",
            "n": 1,
            "size": "16:9",
            "resolution": "2k"
          }
          """;

          HttpClient client = HttpClient.newHttpClient();
          HttpRequest request = HttpRequest.newBuilder()
              .uri(URI.create(url))
              .header("Authorization", "Bearer <token>")
              .header("Content-Type", "application/json")
              .POST(HttpRequest.BodyPublishers.ofString(payload))
              .build();

          HttpResponse<String> response = client.send(request,
              HttpResponse.BodyHandlers.ofString());

          System.out.println(response.body());
      }
  }
  ```

  ```php PHP theme={null}
  <?php

  $url = "https://api.apimart.ai/v1/images/generations";

  $payload = [
      "model" => "gpt-image-2",
      "prompt" => "一只橘猫坐在窗台上看夕阳，水彩画风格",
      "n" => 1,
      "size" => "16:9",
      "resolution" => "2k"
  ];

  $ch = curl_init($url);
  curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
  curl_setopt($ch, CURLOPT_POST, true);
  curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($payload));
  curl_setopt($ch, CURLOPT_HTTPHEADER, [
      "Authorization: Bearer <token>",
      "Content-Type: application/json"
  ]);

  $response = curl_exec($ch);
  curl_close($ch);

  echo $response;
  ?>
  ```

  ```ruby Ruby theme={null}
  require 'net/http'
  require 'json'
  require 'uri'

  url = URI("https://api.apimart.ai/v1/images/generations")

  payload = {
    model: "gpt-image-2",
    prompt: "一只橘猫坐在窗台上看夕阳，水彩画风格",
    n: 1,
    size: "16:9",
    resolution: "2k"
  }

  http = Net::HTTP.new(url.host, url.port)
  http.use_ssl = true

  request = Net::HTTP::Post.new(url)
  request["Authorization"] = "Bearer <token>"
  request["Content-Type"] = "application/json"
  request.body = payload.to_json

  response = http.request(request)
  puts response.body
  ```

  ```swift Swift theme={null}
  import Foundation

  let url = URL(string: "https://api.apimart.ai/v1/images/generations")!

  let payload: [String: Any] = [
      "model": "gpt-image-2",
      "prompt": "一只橘猫坐在窗台上看夕阳，水彩画风格",
      "n": 1,
      "size": "16:9",
      "resolution": "2k"
  ]

  var request = URLRequest(url: url)
  request.httpMethod = "POST"
  request.setValue("Bearer <token>", forHTTPHeaderField: "Authorization")
  request.setValue("application/json", forHTTPHeaderField: "Content-Type")
  request.httpBody = try? JSONSerialization.data(withJSONObject: payload)

  let task = URLSession.shared.dataTask(with: request) { data, response, error in
      if let error = error {
          print("Error: \(error)")
          return
      }

      if let data = data, let responseString = String(data: data, encoding: .utf8) {
          print(responseString)
      }
  }

  task.resume()
  ```

  ```csharp C# theme={null}
  using System;
  using System.Net.Http;
  using System.Text;
  using System.Threading.Tasks;

  class Program
  {
      static async Task Main(string[] args)
      {
          var url = "https://api.apimart.ai/v1/images/generations";

          var payload = @"{
              ""model"": ""gpt-image-2"",
              ""prompt"": ""一只橘猫坐在窗台上看夕阳，水彩画风格"",
              ""n"": 1,
              ""size"": ""16:9"",
              ""resolution"": ""2k""
          }";

          using var client = new HttpClient();
          client.DefaultRequestHeaders.Add("Authorization", "Bearer <token>");

          var content = new StringContent(payload, Encoding.UTF8, "application/json");
          var response = await client.PostAsync(url, content);
          var result = await response.Content.ReadAsStringAsync();

          Console.WriteLine(result);
      }
  }
  ```

  ```dart Dart theme={null}
  import 'dart:convert';
  import 'package:http/http.dart' as http;

  void main() async {
    final url = Uri.parse('https://api.apimart.ai/v1/images/generations');

    final payload = {
      'model': 'gpt-image-2',
      'prompt': '一只橘猫坐在窗台上看夕阳，水彩画风格',
      'n': 1,
      'size': '16:9',
      'resolution': '2k'
    };

    final response = await http.post(
      url,
      headers: {
        'Authorization': 'Bearer <token>',
        'Content-Type': 'application/json'
      },
      body: jsonEncode(payload),
    );

    print(response.body);
  }
  ```

  ```r R theme={null}
  library(httr)
  library(jsonlite)

  url <- "https://api.apimart.ai/v1/images/generations"

  payload <- list(
    model = "gpt-image-2",
    prompt = "一只橘猫坐在窗台上看夕阳，水彩画风格",
    n = 1,
    size = "16:9",
    resolution = "2k"
  )

  response <- POST(
    url,
    add_headers(
      Authorization = "Bearer <token>",
      `Content-Type` = "application/json"
    ),
    body = toJSON(payload, auto_unbox = TRUE),
    encode = "raw"
  )

  cat(content(response, "text"))
  ```
</RequestExample>

<ResponseExample>
  ```json 200 theme={null}
  {
    "code": 200,
    "data": [
      {
        "status": "submitted",
        "task_id": "task_01KPQ7J7DWB7QZ3WCEK3YVPBRA"
      }
    ]
  }
  ```

  ```json 400 theme={null}
  {
    "error": {
      "code": 400,
      "message": "参数错误：size 不合法 / 4K 比例不支持 / 像素违规等",
      "type": "invalid_request_error"
    }
  }
  ```

  ```json 401 theme={null}
  {
    "error": {
      "code": 401,
      "message": "身份验证失败，请检查您的API密钥",
      "type": "authentication_error"
    }
  }
  ```

  ```json 402 theme={null}
  {
    "error": {
      "code": 402,
      "message": "账户余额不足，请充值后再试",
      "type": "payment_required"
    }
  }
  ```

  ```json 429 theme={null}
  {
    "error": {
      "code": 429,
      "message": "请求过于频繁，请稍后再试",
      "type": "rate_limit_error"
    }
  }
  ```

  ```json 500 theme={null}
  {
    "error": {
      "code": 500,
      "message": "服务器错误",
      "type": "server_error"
    }
  }
  ```

  ```json 503 theme={null}
  {
    "error": {
      "code": 503,
      "message": "上游暂时不可用，请稍后再试",
      "type": "service_unavailable"
    }
  }
  ```
</ResponseExample>

## Authorizations

<ParamField header="Authorization" type="string" required>
  所有接口均需要使用 Bearer Token 进行认证

  获取 API Key：

  访问 [API Key 管理页面](https://apimart.ai/keys) 获取您的 API Key

  使用时在请求头中添加：

  ```
  Authorization: Bearer YOUR_API_KEY
  ```
</ParamField>

## Body

<ParamField body="model" type="string" default="gpt-image-2" required>
  图像生成模型名称

  固定填写 `gpt-image-2`
</ParamField>

<ParamField body="prompt" type="string" required>
  图像生成的文本描述

  * 支持中英文，建议详细描述
  * 提交前会经过平台敏感词 / 安全审核，命中违规内容会直接返回错误
</ParamField>

<ParamField body="n" type="integer" default="1">
  生成图片张数

  取值范围：`1`

  <Warning>
    必须传入纯数字（如 `1`），不要加引号
  </Warning>
</ParamField>

<ParamField body="size" type="string" default="1:1">
  图像生成的比例

  支持以下比例，也可传入 `auto` 由服务端自动选择合适比例：

  | size   | 类型 |
  | ------ | -- |
  | `auto` | 自动 |
  | `1:1`  | 正方 |
  | `3:2`  | 横图 |
  | `2:3`  | 竖图 |
  | `4:3`  | 横图 |
  | `3:4`  | 竖图 |
  | `5:4`  | 横图 |
  | `4:5`  | 竖图 |
  | `16:9` | 横图 |
  | `9:16` | 竖图 |
  | `2:1`  | 横图 |
  | `1:2`  | 竖图 |
  | `21:9` | 横图 |
  | `9:21` | 竖图 |
</ParamField>

<ParamField body="resolution" type="string" default="1k">
  输出分辨率档位

  可选值：`1k` / `2k` / `4k`

  `size × resolution` → 实际像素对应关系：

  | size   | `1k`      | `2k`      | `4k`          |
  | ------ | --------- | --------- | ------------- |
  | `1:1`  | 1024×1024 | 2048×2048 | ❌             |
  | `3:2`  | 1536×1024 | 2048×1360 | ❌             |
  | `2:3`  | 1024×1536 | 1360×2048 | ❌             |
  | `4:3`  | 1024×768  | 2048×1536 | ❌             |
  | `3:4`  | 768×1024  | 1536×2048 | ❌             |
  | `5:4`  | 1280×1024 | 2560×2048 | ❌             |
  | `4:5`  | 1024×1280 | 2048×2560 | ❌             |
  | `16:9` | 1536×864  | 2048×1152 | **3840×2160** |
  | `9:16` | 864×1536  | 1152×2048 | **2160×3840** |
  | `2:1`  | 2048×1024 | 2688×1344 | **3840×1920** |
  | `1:2`  | 1024×2048 | 1344×2688 | **1920×3840** |
  | `21:9` | 2016×864  | 2688×1152 | **3840×1648** |
  | `9:21` | 864×2016  | 1152×2688 | **1648×3840** |

  <Warning>
    4K 仅支持 6 个比例（`16:9` / `9:16` / `2:1` / `1:2` / `21:9` / `9:21`），其它比例 + 4K 因总像素超上限不可用。
  </Warning>
</ParamField>

<ParamField body="image_urls" type="array">
  参考图数组（OpenAI 标准字段），传入后走图生图模式

  <Expandable title="详细说明">
    * 最多 16 张参考图，超过会返回 `image_urls exceeds max 16`
    * 支持 `图片 URL`（公网可访问的稳定链接）
    * 支持 `base64 data URI`（形如 `data:image/png;base64,...`）
    * 同一数组里可以 URL 与 base64 混填，服务端会自行处理
    * 不传 `size` 时输出分辨率 = 输入图分辨率；传 `size` 则强制按指定尺寸出图
  </Expandable>
</ParamField>

<ParamField body="official_fallback" type="boolean" default="false">
  是否使用官方渠道兜底

  * `false`：不使用（默认）
  * `true`：使用官方渠道
</ParamField>

## 使用场景示例

**文生图（最简请求）**

```json theme={null}
{
  "model": "gpt-image-2",
  "prompt": "一只橘猫坐在窗台上看夕阳，水彩画风格"
}
```

**文生图（指定比例 + 2K）**

```json theme={null}
{
  "model": "gpt-image-2",
  "prompt": "a corgi astronaut on the moon, cinematic, 8k",
  "size": "16:9",
  "resolution": "2k"
}
```

**文生图（4K 输出）**

```json theme={null}
{
  "model": "gpt-image-2",
  "prompt": "星空下的古老城堡",
  "size": "16:9",
  "resolution": "4k"
}
```

**图生图（参考图 = URL）**

```json theme={null}
{
  "model": "gpt-image-2",
  "prompt": "把这张照片变成水彩画风格",
  "image_urls": [
    "https://example.com/photo.jpg"
  ]
}
```

**图生图（参考图 = base64）**

```json theme={null}
{
  "model": "gpt-image-2",
  "prompt": "把这张照片变成水彩画风格",
  "image_urls": [
    "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA..."
  ]
}
```

**图生图（多参考图融合，URL + base64 混填）**

```json theme={null}
{
  "model": "gpt-image-2",
  "prompt": "把这两张照片融合成一张海报",
  "size": "4:3",
  "resolution": "2k",
  "image_urls": [
    "https://example.com/photo-a.jpg",
    "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA..."
  ]
}
```

## Response

<ResponseField name="code" type="integer">
  响应状态码
</ResponseField>

<ResponseField name="data" type="array">
  返回数据数组

  <Expandable title="属性">
    <ResponseField name="status" type="string">
      任务状态

      * `submitted` - 已提交
    </ResponseField>

    <ResponseField name="task_id" type="string">
      任务唯一标识符，用于后续查询任务结果
    </ResponseField>
  </Expandable>
</ResponseField>

## 查询任务结果

提交成功后返回 `task_id`，通过 `GET /v1/tasks/{task_id}` 轮询任务状态，详见 [任务查询接口](/cn/api-reference/tasks/status)。

### 成功响应示例

```json theme={null}
{
  "code": 200,
  "data": {
    "id": "task_01KPQ7J7DWB7QZ3WCEK3YVPBRA",
    "status": "completed",
    "progress": 100,
    "created": 1776748674,
    "completed": 1776748726,
    "actual_time": 52,
    "cost": 0.05279,
    "estimated_time": 100,
    "result": {
      "images": [
        {
          "url": [
            "https://upload.apimart.ai/f/image/xxxxxxxx-gpt_image_2_task_xxx_0.png"
          ],
          "expires_at": 1776835126
        }
      ]
    }
  }
}
```

取图方式：`data.result.images[0].url[0]`

### 任务状态说明

| 状态           | 含义                    |
| ------------ | --------------------- |
| `submitted`  | 已提交                   |
| `processing` | 上游处理中                 |
| `completed`  | 成功，`result.images` 可用 |
| `failed`     | 失败，查看 `error.message` |

### 轮询建议

* **首次查询延迟**：提交后等待 10\~20 秒再开始查询
* **查询间隔**：建议 3\~5 秒一次，避免无脑毫秒级轮询
* **超时参考**：单张图一般 30~~60 秒完成（实测 `actual_time` 44~~53s）
* **批量查询**：若需同时查询多个任务，请使用 `POST /v1/tasks/batch`，请求体 `{"task_ids": ["task_xxx", "task_yyy"]}`

## 注意事项

1. **异步处理**：提交后返回 `task_id`，需轮询 `/v1/tasks/{task_id}` 获取最终图片 URL
2. **内容审核**：`prompt` 会先经过平台敏感词 / 安全审核，命中违规内容会直接拒绝并不会计费
3. **结果 URL**：平台已将上游临时签名链接镜像到自家 R2 对象存储，返回的是稳定链接，客户端可直接访问
4. **URL 时效**：响应中的 `expires_at = completed + 24h` 是业务层提示字段，建议尽快下载或转存到自己的 CDN
5. **比例冲突**：推荐只通过 `size` 字段传比例，不要在 `prompt` 里重复写比例，避免上游理解冲突
6. **计费规则**：按分辨率档位（1K / 2K / 4K）计费，失败不扣费，审核未通过不扣费
7. **4K 限制**：仅 `16:9` / `9:16` / `2:1` / `1:2` / `21:9` / `9:21` 六个比例支持 4K
8. **任务保留**：`task_id` 在数据库里默认保留若干天（由 `TASK_RETENTION_DAYS` 配置），过期后查询会返回"任务不存在或已过期"
