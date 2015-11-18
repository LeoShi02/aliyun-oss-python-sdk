# Aliyun OSS SDK for Python

## 概述
阿里云对象存储Python SDK。

## 运行环境
Python 2.6，2.7，3.3，3.4，3.5

## 安装方法
通过pip安装官方发布的版本：
```bash
$ pip install oss
```
也可以直接安装解压后的安装包：
```bash
$ sudo python setup.py install
```
## 快速使用
```python
# -*- coding: utf-8 -*-

import oss

endpoint = 'oss-cn-hangzhou.aliyuncs.com' # 假设你的Bucket处于杭州区域

auth = oss.Auth('<你的AccessKeyId>', '<你的AccessKeySecret>')
bucket = oss.Bucket(auth, endpoint, '<你的Bucket名>')

object_name = 'story.txt'

# 上传
bucket.put_object(object_name, 'Ali Baba is a happy youth.')

# 下载
bucket.get_object(object_name).read()

# 删除
bucket.delete_object(object_name)

# 遍历所有对象
for object_info in oss.iterators.ObjectIterator(bucket):
    print(object_info.name)
```
## 测试
首先通过环境变量来设置测试所需的AccessKeyID、AccessKeySecret、Endpoint以及Bucket信息：
```bash
$ export OSS_TEST_ACCESS_KEY_ID=<AccessKeyID>
$ export OSS_TEST_ACCESS_KEY_SECRET=<AccessKeySecret>
$ export OSS_TEST_ENDPOINT=<endpoint>
$ export OSS_TEST_BUCKET=<bucket>
```
然后可以通过以下方式之一运行测试：
```bash
$ python -m unitest discover tests  # 如果Python版本 >= 2.7
$ nosetests                         # 如果安装了nose
$ py.test                           # 如果安装了py.test
```
## 更多使用

## 注意事项
* 不要使用Python 3.3.0、3.3.1，参考[Python Issue 16658](https://bugs.python.org/issue16658)

## 联系我们

## 代码许可
MIT许可证，参见LICENSE文件。