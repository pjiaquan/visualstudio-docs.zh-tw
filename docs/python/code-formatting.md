---
title: "在 Visual Studio 中格式化 Python 程式碼 | Microsoft Docs"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0f1631-360b-45d4-a0cb-01c3c10d25f2
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: b9e1c2b6be671adb99a13e4a0eb4357fbba477b2
ms.lasthandoff: 04/10/2017

---

# <a name="formatting-python-code"></a>格式化 Python 程式碼

Visual Studio 可讓您快速重新格式化程式碼，以符合預先設定的格式化選項。

- 若要格式化選取範圍︰選取 [編輯] > [進階] > [格式化選取範圍] 或按 Ctrl+E、F。
- 若要格式化整個檔案︰選取 [編輯] > [進階] > [格式化文件] 或按 Ctrl+E、D。

透過 [工具] > [選項] > [文字編輯器] > [Python] > [格式化] 和其子索引標籤可設定選項，且依預設會設為符合 [PEP 8 樣式指南 (英文)](http://www.python.org/dev/peps/pep-0008/) 的超集。 [一般] 索引標籤決定何時套用格式；其他三個子頁面會在後續小節中定義。

此外，Visual Studio 中的 Python 支援也將實用的[填滿註解段落](#fill-comment-paragraph-command)命令新增到 [編輯] > [進階] 功能表，如下所述。

## <a name="spacing"></a>間距

**間距**控制在各種語言建構前後插入或移除空格的位置。 每個選項有三個可能的值︰

- 已核取︰確保間距已套用。
- 已清除︰移除任何間距。
- 不定︰保留原始格式。

下表提供各種選項的範例。

| 類別定義選項 | 已核取 | 已清除 |
| --- | --- | --- | 
| 在類別宣告的名稱與基底清單之間插入空格 | `class X (object): pass` | `class X(object): pass` | 
| 在基底清單括號內插入空格 | `class X( object ): pass` | `class X(object): pass` |
| 在空白基底清單括號內插入空格 | `class X( ): pass` | `class X(): pass` |

<br/>

| 函式定義選項 | 已核取 | 已清除 |
| --- | --- | --- |
| 在函式宣告的名稱和參數清單之間插入空格 | `def X (): pass` | `def X(): pass` | 
| 在參數清單括號內插入空格 | `def X( a, b ): pass` | `def X(a, b): pass` |
| 在空白的參數清單括號內插入空格 | `def X( ): pass` | `def X(): pass` |
| 在預設參數值的 '=' 前後插入空格 | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| 在傳回註解運算子前後插入空格 | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| 運算子選項 | 已核取 | 已清除 |
| --- | --- | --- |
| 在二元運算子前後插入空格 | `a + b` | `a+b` |
| 在指派前後插入空格 | `a = b` | `a=b` |

<br/>

| 運算式間距選項 | 已核取 | 已清除 |
| --- | --- | --- |
| 在函式呼叫的名稱和引數清單之間插入空格 | `X ()` | `X()` |
| 在空的引數清單括號內插入空格 | `X( )` | `X()` |
| 在引數清單括號內插入空格 | `X( a, b )` | `X(a, b)` |
| 在運算式的括號內插入空格 | `( a )` | `(a)` |
| 在空白元組括號內插入空格 | `( )` | `()` |
| 在元組括號內插入空格 | `( a, b )` | `(a, b)` |
| 在空的方括號中插入空格 | `[ ]` | `[]` |
| 在清單的方括號內插入空格 | `[ a, b ]` | `[a, b]` |
| 在左方括號前面插入空格 | `x [i]` | `x[i]` |
| 在方括號中插入空格 | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>陳述式

**陳述式**控制自動將各種陳述式重新撰寫成更多 Pythonic 格式。

| 選項 | 格式之前 | 格式之後 |
| --- | --- | --- |
| 將匯入的模組放在新行 | `import sys, pickle` | `import sys`<br/>`import pickle` |
| 移除不必要的分號 | `x = 42;` | `x = 42` |
| 將多個陳述式放在新行 | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |


## <a name="wrapping"></a>換行

您可在 [換行] 中設定 [最大註解寬度] (預設為 80)；如果您已設定 [將太寬的註解換行] 選項，Visual Studio 會將註解重新格式化為不超過該寬度。

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```



## <a name="fill-comment-paragraph-command"></a>填滿註解段落命令

[編輯] > [進階] > [填滿註解段落] (Ctrl+E、Ctrl+P) 會自動重排和格式化註解文字、結合較短的行和拆解較長的行。

例如: 

```python
# foo 
# bar
# baz
```

變更為：

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

變更為：

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```
