---
title: "数据工厂"
date: 2021-05-01T10:07:47+06:00
draft: false

# post thumb
image: "images/post/post-4-0.jpg"

# meta description
description: "this is meta description"

# taxonomies
categories:
  - "Golang"
tags:
  - "Golang"
  - "Data"
  - "开源"

# post type
type: "post"
---

## 概要

数据工人，数据生成器。通过配置文件，可以批量生成一系列随机数据。

## 应用场景

- 大数据测试
- Demo 演示
- 开发过程中的单元测试

## 特性

- [x] 配置文件，定义输出的字段和一些参数。
- [x] 加载外部字典，获取更多数据。
- [x] 自定义格式化输出数据

## Github 地址

[![alt travis](https://travis-ci.org/lalolv/data-worker.svg?branch=master)](https://travis-ci.org/lalolv/data-worker)
[![alt report](https://goreportcard.com/badge/github.com/lalolv/data-worker)](https://goreportcard.com/report/github.com/lalolv/data-worker)

[访问 Github 代码库](https://github.com/lalolv/data-worker "Github")

## 如何使用

### 创建一个 json 格式的配置文件，保存在 config 目录

```json
{
  "dict_path": "dict",
  "build": {
    "count": 5,
    "format": "csv",
    "name": "demo2",
    "path": "out"
  },
  "fields": [
    {
      "name": "order_id",
      "value": "po-{uuid}"
    },
    {
      "name": "email",
      "value": "{username}@{email}"
    },
    {
      "name": "creat_dt",
      "value": "{datetime}"
    }
  ]
}
```

- dict_path 指定一个存放字典文件的目录
- build 编译命令
- fields 设置需要输出哪些字段（名称、类型、字典等）
- 使用大括号，自定义输出变量。变量来自数据字典和内置类型。

### 通过 -c 参数，指定运行的配置文件

```shell
data-worker build -c ./config/demo.json
```

## 内置类型

| 类型     |      说明      |
| -------- | :------------: |
| string   |     字符串     |
| uuid     |  唯一识别 ID   |
| mobile   |    手机号码    |
| idno     |    身份证号    |
| datetime | 完整的日期时间 |

## 计划

- [ ] 自定义变量，增加过滤条件
- [ ] 支持更多的内置类型
