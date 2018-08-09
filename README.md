Simple Dictionary
==================

### 一个简单快速的词库工具

### 特点：


> - **简单**：纯 PHP 实现，无需安装扩展。
> - **快速**：查找耗时跟词库大小关系不大，不会一次性加载整个词库，使用时内存占用小（生成词库比较耗费内存）。

### 使用方法

#### 1.准备文本格式的词库

首先准备一个文本文件，每个词占一行。格式：

```
词语<tab>值
词语<tab>值
词语<tab>值
词语<tab>值

词语<tab>值
词语<tab>值
```

#### 2.使用SimpleDictionary生成词库

```

composer require wangningkai\simple-dictionary dev-master

```



```php
<?php

require 'vendow/autoload.php'

use WangNingkai\SimpleDictionary\SimpleDictionary;

SimpleDictionary::make("text_file_path", "output_dict_path");


```

#### 搜索

```php
<?php
require 'vendow/autoload.php'

use WangNingkai\SimpleDictionary\SimpleDictionary;

$dict = new SimpleDictionary("dict_path");
$result = $dict->search("some text here...");

# 返回结果
# $result = [
#  'word1' => ['value' => 'value1', 'count' => 'count1'],
#  ...
# ]
#

```

#### 替换

```php
<?php
require 'vendow/autoload.php'

use WangNingkai\SimpleDictionary\SimpleDictionary;

$dict = new SimpleDictionary("dict_path");
# 简单替换
$replaced = $dict->replace("some text here...", "**");

#高级替换
$replaced = $dict->replace("some text here...", function($word, $value) {
  return "[$word -> $value]";
});

```
