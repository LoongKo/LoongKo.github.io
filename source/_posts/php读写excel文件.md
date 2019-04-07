---
title: php读写excel文件
date: 2019-04-07 20:28:32
categories: php
tags: php
---
[PhpSpreadsheet](https://github.com/PHPOffice/PhpSpreadsheet)是PHP的一个类库，可以读写excel表格，可以替代[PHPExcel](https://github.com/PHPOffice/PHPExcel)。

# 安装PhpSpreadsheet
使用composer下载安装PhpSpreadsheet
`composer require phpoffice/phpspreadsheet`

# 读取excel
```php
require '新建文件夹\vendor\autoload.php';
use PhpOffice\PhpSpreadsheet\IOFactory;
$inputFileName = '新建 XLS Worksheet.xls';
$spreadsheet = IOFactory::load($inputFileName);
$sheetData = $spreadsheet->getActiveSheet()->toArray(null, true, true, true);
var_export($sheetData);
```
excel表格数据
{% asset_img 1.png %}

打印的结果
{% asset_img 2.png %}

当然还有各种读取的方法，详细见[官方文档](https://phpspreadsheet.readthedocs.io/en/latest/)或者{% asset_link phpspreadsheet.7z 下载的文件 %}里面也有样例以及文档说明。

# 写入excel
```php
require 'vendor/autoload.php';

use PhpOffice\PhpSpreadsheet\Spreadsheet;
use PhpOffice\PhpSpreadsheet\Writer\Xlsx;

$spreadsheet = new Spreadsheet();
$sheet = $spreadsheet->getActiveSheet();
$sheet->setCellValue('A1', 'Hello World !');

$writer = new Xlsx($spreadsheet);
$writer->save('hello world.xlsx');
```