元动作是用于对 OneBot 实现进行控制、检查等的动作，例如获取版本信息等，仅与 OneBot 本身交互，与实现对应的机器人平台无关。

## `get_latest_events` 获取最新事件列表

仅 HTTP 通信方式必须支持，用于轮询获取事件。

=== "请求参数"

    字段名 | 数据类型 | 默认值 | 说明
    --- | --- | --- | ---
    `limit` | int64 | 0 | 获取的事件数量上限，0 表示不限制
    `timeout` | int64 | 0 | 没有事件时最多等待的秒数，0 表示使用短轮询，不等待

=== "响应数据"

    除元事件外的事件列表，从旧到新排序。

=== "请求示例"

    ```json
    {
        "action": "get_latest_events",
        "params": {
            "limit": 100,
            "timeout": 0
        }
    }
    ```

=== "响应示例"

    ```json
    {
        "status": "ok",
        "retcode": 0,
        "data": [
            {
                "id": "b6e65187-5ac0-489c-b431-53078e9d2bbb",
                "self": {
                    "platform": "qq",
                    "user_id": "123234"
                },
                "time": 1632847927.599013,
                "type": "message",
                "detail_type": "private",
                "sub_type": "",
                "message_id": "6283",
                "message": [
                    {
                        "type": "text",
                        "data": {
                            "text": "OneBot is not a bot"
                        }
                    },
                    {
                        "type": "image",
                        "data": {
                            "file_id": "e30f9684-3d54-4f65-b2da-db291a477f16"
                        }
                    }
                ],
                "alt_message": "OneBot is not a bot[图片]",
                "user_id": "123456788"
            },
            {
                "id": "b6e65187-5ac0-489c-b431-53078e9d2bbb",
                "self": {
                    "platform": "qq",
                    "user_id": "123234"
                },
                "time": 1632847927.599013,
                "type": "notice",
                "detail_type": "group_member_increase",
                "sub_type": "join",
                "user_id": "123456788",
                "group_id": "87654321",
                "operator_id": "1234567"
            }
        ],
        "message": ""
    }
    ```

## `get_supported_actions` 获取支持的动作列表

=== "请求参数"

    无。

=== "响应数据"

    支持的动作名称列表。

=== "请求示例"

    ```json
    {
        "action": "get_supported_actions",
        "params": {}
    }
    ```

=== "响应示例"

    ```json
    {
        "status": "ok",
        "retcode": 0,
        "data": [
            "get_supported_actions",
            "get_status",
            "get_version",
            "send_message",
            "get_self_info"
        ],
        "message": ""
    }
    ```

## `get_supported_message_segments` 获取支持的消息段列表

=== "请求参数"

    无。

=== "响应数据"

    所支持的消息段列表。

=== "请求示例"

    ```json
    {
        "action": "get_supported_actions",
        "params": {
            "self": "xxxxx"
        }
    }
    ```

=== "响应示例"

    ```json
    {
        "status": "ok",
        "retcode": 0,
        "data": [
            "text",
            "mention",
            "image",
            "reply"
        ],
        "message": ""
    }
    ```

## `get_status` 获取运行状态

=== "请求参数"

    无。

=== "响应数据"

    字段名 | 数据类型 | 说明
    --- | --- | ---
    `good` | bool | 是否各项状态都符合预期，OneBot 实现各模块均正常
    `bots` | list[object] | 当前 OneBot Connect 连接上所有机器人账号的状态列表

    其中，`bots` 的每一个元素具有下面这些字段：

    字段名 | 数据类型 | 说明
    --- | --- | ---
    `self` | self | 机器人自身标识
    `online` | bool | 机器人账号是否在线（可收发消息等）

=== "请求示例"

    ```json
    {
        "action": "get_status",
        "params": {}
    }
    ```

=== "响应示例"

    ```json
    {
        "status": "ok",
        "retcode": 0,
        "data": {
            "good": true,
            "bots": [
                {
                    "self": {
                        "platform": "qq",
                        "user_id": "1234567"
                    },
                    "online": true,
                    "qq.status": "信号弱"
                },
                {
                    "self": {
                        "platform": "telegram",
                        "user_id": "2345678"
                    },
                    "online": true
                }
            ]
        },
        "message": ""
    }
    ```

## `get_version` 获取版本信息

=== "请求参数"

    无。

=== "响应数据"

    字段名 | 数据类型 | 说明
    --- | --- | ---
    `impl` | string | OneBot 实现名称，格式见 [术语表](../../glossary.md#onebot-onebot-implementation)
    `version` | string | OneBot 实现的版本号
    `onebot_version` | string | OneBot 实现的 OneBot 标准版本号

=== "请求示例"

    ```json
    {
        "action": "get_version",
        "params": {}
    }
    ```

=== "响应数据"

    ```json
    {
        "status": "ok",
        "retcode": 0,
        "data": {
            "impl": "go-onebot-qq",
            "version": "1.2.0",
            "onebot_version": "12"
        },
        "message": ""
    }
    ```
