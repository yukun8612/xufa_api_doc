# 请求地址

### 测试域名
```
   http://106.54.231.188:8081

```


### 发送消息
```
POST /
```
**参数:**

名称 | 类型 | 是否必须 | 描述
------------ | ------------ | ------------ | ------------
model | STRING | YES |固定chatglm3-6b|
messages | ARRAY | YES | 消息列表|
messages[0].role| STRING |YES | system表示系统,role表示用户发送的信息|
messages[0].content |STRING | YES | 消息内容 |

**请求例子:**

```
{
  "model": "chatglm3-6b",
  "messages": [
    {
      "role": "system", 
      "content": "You are ChatGLM3, a large language model trained by Zhipu.AI. Follow the user’s instructions carefully. Respond using markdown."
    },
    {
      "role": "user",
      "content": "你好，给我讲一个故事，大概100字"
    }
  ],
  "stream": false,
  "max_tokens": 100,
  "temperature": 0.8,
  "top_p": 0.8
}


```

**响应:**


名称 | 类型 | 是否必须 | 描述
------------ | ------------ | ------------ | ------------
model | STRING | YES |固定 chatglm3-6b|
choices | ARRAY | YES | 结果 |
choices[0].index| INT |YES | 行号|
choices[0].message |OBJECT | YES | 消息体 |
choices[0].message.role |STRING | YES | 角色信息 (只有系统) |
choices[0].message.content |STRING | YES | 消息内容 |
choices[0].created |NUMBER | YES | 时间 单位秒 |

**响应例子:**

```
{
    "model": "chatglm3-6b",
    "id": "",
    "object": "chat.completion",
    "choices": [
        {
            "index": 0,
            "message": {
                "role": "assistant",
                "content": "从前，有一个美丽的村庄，里面住着一个勇敢善良的少年。他叫小明，总是乐于助人。有一天，村子附近的一座山发生了滑坡，巨石滚下山坡，堵住了村子里唯一的一条河流。这使得村民们生活陷入困境，无法获取清洁的水源。\n\n为了拯救村子，小明决定冒险上山寻找一条新的河流。经过几天的艰苦努力，他终于找到了一条清澈见底、 flow 顺畅的新河。村民们非常",
                "name": null,
                "function_call": null
            },
            "finish_reason": "stop"
        }
    ],
    "created": 1723468449,
    "usage": {
        "prompt_tokens": 54,
        "total_tokens": 154,
        "completion_tokens": 100
    }
}


```

