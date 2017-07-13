---
title: "EditorConfig 的 .NET 程式碼樣式設定 | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 01
author: kaseyu
ms.author: kaseyu
manager: davidcsa
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 288595f50555bd8314d0ad60cd2e1ce8121a8ab0
ms.contentlocale: zh-tw
ms.lasthandoff: 06/23/2017

---

# EditorConfig 的 .NET 程式碼樣式設定
<a id="net-code-style-settings-for-editorconfig" class="xliff"></a>

## 可能的值
<a id="possible-values" class="xliff"></a>

`options_name = false|true : none|suggestion|warning|error`

對於程式碼樣式選項您必須指定 **true** (建議您使用此選項) 或 **false** (不建議您使用此選項)、冒號 (`:`)，和嚴重性 (`none`、`suggestion`、`warning` 或 `error`)。 嚴重性表示要在程式碼基底中為該樣式強制的層級。

嚴重性 | effect
------------ | -------------
無 | 當未遵循此樣式時不要顯示任何項目給使用者，不過程式碼產生功能將會以此樣式產生。 
建議 | 當未遵循此樣式時，向使用者顯示為建議 (前兩個字元上的基礎點)。
warning | 當未遵循此樣式時，顯示編譯器警告。
個錯誤 | 當未遵循此樣式時，顯示編譯器錯誤。

## .NET 程式碼樣式選項
<a id="net-code-style-options" class="xliff"></a>

- [Dotnet 程式碼樣式設定](#this_and_me)
    - ["This." 和 "Me."限定性條件](#this_and_me)
        - [欄位](#this_and_me_fields)
        - [屬性](#this_and_me_properties)
        - [方法](#this_and_me_methods)
        - [事件](#this_and_me_events)
    - [語言關鍵字 (int、string 等等) 與類型參考的 Framework 類型名稱](#language_keywords)
        - [區域變數、參數和成員](#language_keywords_variables)
        - [成員存取運算式](#language_keywords_member_access)
    - [運算式層級喜好設定](#expression_level)
        - [物件初始設定式](#expression_level_object_initializers)
        - [集合初始設定式](#expression_level_collection_initializers)
        - [明確的 Tuple 名稱](#expression_level_tuple_names)
        - ["Null" 檢查中的聯合運算式](#expression_level_null_checking)
        - ["Null" 檢查中的 Null 傳播](#expression_level_null_propogation)
- [CSharp 程式碼樣式設定](#csharp_codestyle)
    - ["var"](#var)
        - [內建類型的 "var"](#var_built_in)
        - [類型明顯時的 "var"](#var_apparent)
        - [他處的 "var"](#var_elsewhere)
    - [運算式主體成員](#expression_bodied_members)
        - [方法](#expression_bodied_members_methods)
        - [建構函式](#expression_bodied_members_constructors)
        - [運算子](#expression_bodied_members_operators)
        - [屬性](#expression_bodied_members_properties)
        - [索引子](#expression_bodied_members_indexers)
        - [存取子](#expression_bodied_members_accessors)
    - [模式比對](#pattern_matching)
        - ["is" 與 "cast" 檢查](#pattern_matching_is_cast)
        - ["as" 與 "null" 檢查](#pattern_matching_as_null)
    - [內嵌變數宣告](#inlined_variable_declarations)
    - ["Null" 檢查喜好設定](#null_checking)
        - [Throw 運算式](#null_checking_throw_expressions)
        - [條件式的委派呼叫](#null_checking_conditional_delegate_calls)

## <a name="this_and_me">"This." 和 "Me."限定性條件</a>

### <a name="this_and_me_fields">欄位</a>

|  選項名稱 | `dotnet_style_qualification_for_field` |
| ------------- |:-------------:|
| **適用的語言** | C# 和 Visual Basic

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 用於非靜態方法中的所有非靜態欄位，偏好在 C# 中開頭加上 `this.`，或在 Visual Basic 中開頭加上 `Me.`。 | **C#:** <br>`this.capacity = 0;` <br><br> **Visual Basic:**`Me.capacity = 0`
| False | 用於非靜態方法中的所有非靜態欄位，偏好在 C# 中開頭不要加上 `this.`，或在 Visual Basic 中開頭不要加上 `Me.`。 | **C#:** <br>`capacity = 0;` <br><br> **Visual Basic:**`capacity = 0`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="this_and_me_properties">屬性</a>

|  選項名稱 | `dotnet_style_qualification_for_property` |
| ------------- |:-------------:|
| **適用的語言** | C# 和 Visual Basic

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 用於非靜態方法中的所有非靜態屬性，偏好在 C# 中開頭加上 `this.`，或在 Visual Basic 中開頭加上 `Me.`。| **C#:** <br>`this.ID = 0;` <br><br> **Visual Basic:**`Me.ID = 0`
| False | 用於非靜態方法中的所有非靜態屬性，偏好在 C# 中開頭「不要」加上 `this.`，或在 Visual Basic 中開頭不要加上 `Me.`。 | **C#:** <br>`ID = 0;` <br><br> **Visual Basic:**`ID = 0`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```


### <a name="this_and_me_methods">方法</a>
|  選項名稱 | `dotnet_style_qualification_for_method` |
| ------------- |:-------------:|
| **適用的語言** | C# 和 Visual Basic

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 從非靜態方法內呼叫的所有非靜態方法，偏好在 C# 中開頭加上 `this.`，在 VB 中開頭加上 `Me.`。| **C#:** <br>`this.Display();` <br><br> **Visual Basic:**`Me.Display()`
| False | 從非靜態方法內呼叫的所有非靜態方法，偏好在 C# 中開頭「不要」加上 `this.`，在 VB 中開頭不要加上 `Me.`。 | **C#:** <br>`Display();` <br><br> **Visual Basic:**`Display()`


#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="this_and_me_events">事件</a>
|  選項名稱 | `dotnet_style_qualification_for_event` |
| ------------- |:-------------:|
| **適用的語言** | C# 和 Visual Basic

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 從非靜態方法內參考的所有非靜態事件，偏好在 C# 中開頭加上 `this.`，在 VB 中開頭加上 `Me.`。| **C#:** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic:**`AddHandler Me.Elapsed, AddressOf Handler`
| False | 從非靜態方法內參考的所有非靜態事件，偏好在 C# 中開頭「不要」加上 `this.`，在 VB 中開頭不要加上 `Me.`。 | **C#:** <br>`Elapsed += Handler;` <br><br> **Visual Basic:**`AddHandler Elapsed, AddressOf Handler`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">語言關鍵字 (int、string 等等) 與類型參考的 Framework 類型名稱</a>
### <a name="language_keywords_variables">區域變數、參數和成員</a>
|  選項名稱 | `dotnet_style_predefined_type_for_locals_parameters_members` |
| ------------- |:-------------:|
| **適用的語言** | C# 和 Visual Basic

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 針對區域變數、參數和類型成員，有語言關鍵字表示它們的類型 (`int`、`double`、`float`、`short`、`long`、`decimal`、`string`) 偏好使用關鍵字，而不是類型名稱 (`Int32`、`Int64` 等)。| **C#:** <br>`private int _member;` <br><br> **Visual Basic:**`Private _member As Integer`
| False | 針對區域變數、參數和類型成員，有語言關鍵字表示它們的類型 (`int`、`double`、`float`、`short`、`long`、`decimal`、`string`) 偏好使用類型名稱 (`Int32`、`Int64` 等) 而不是關鍵字。  | **C#:** <br>`private Int32 _member;` <br><br> **Visual Basic:**`Private _member As Int32`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="language_keywords_member_access">成員存取運算式</a>
|  選項名稱 | `dotnet_style_predefined_type_for_member_access` |
| ------------- |:-------------:|
| **適用的語言** | C# 和 Visual Basic

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 每當成員存取運算式用於有關鍵字表示的類型時 (`int`、`double`、`float`、`short`、`long`、`decimal`、`string`)，偏好使用關鍵字。| **C#:** <br>`var local = int.MaxValue;` <br><br> **Visual Basic:**`Dim local = Integer.MaxValue`
| False | 每當成員存取運算式用於有關鍵字表示的類型時 (`int`、`double`、`float`、`short`、`long`、`decimal`、`string`)，偏好使用類型名稱。 | **C#:** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic:**`Dim local = Int32.MaxValue`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="expression_level">運算式層級喜好設定</a>
### <a name="expression_level_object_initializers">物件初始設定式</a>
|  選項名稱 | `dotnet_style_object_initializer` |
| ------------- |:-------------:|
| **適用的語言** | C# 和 Visual Basic

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好盡可能使用物件初始設定式來初始化物件。| **C#:** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic:**`Dim c = New Customer() With { .Age = 21 }`
| False | 偏好「不」使用物件初始設定式來初始化物件。 | **C#:** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic:** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="expression_level_collection_initializers">集合初始設定式</a>
|  選項名稱 | `dotnet_style_collection_initializer` |
| ------------- |:-------------:|
| **適用的語言** | C# 和 Visual Basic

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好盡可能使用集合初始設定式來初始化集合。| **C#:** <br>`var list = new List<int>{ 1, 2, 3 };` <br><br> **Visual Basic:** <br> `Dim list = new List(Of Integer) From { 1, 2, 3}`
| False | 偏好「不」使用集合初始設定式來初始化物件。 | **C#:** <br>`var list = new List<int>();`<br>`list.Add(1);`<br>`list.Add(2);`<br>`list.Add(3);` <br><br> **Visual Basic:** <br>`Dim list = new List(Of Integer)`<br>`list.Add(1)`<br>`list.Add(2)`<br>`list.Add(3)`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_collection_initializer = true:suggestion
```

### <a name="expression_level_tuple_names">明確的 Tuple 名稱</a>
|  選項名稱 | `dotnet_style_explicit_tuple_names` |
| ------------- |:-------------:|
| **適用的語言** | C# 和 Visual Basic

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好 Tuple 名稱勝過 ItemX 屬性。| **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.name;` <br><br> **Visual Basic:** <br> `Dim customer As (name As String, age As Integer) = GetCustomer()`<br>`Dim name = customer.name`
| False | 偏好 ItemX 屬性勝過 Tuple 名稱。 | **C#:** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.Item1;` <br><br> **Visual Basic:** <br>`Dim customer As (name As String, age As Integer) = GetCustomer()`<br> `Dim name = customer.Item1`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_explicit_tuple_names = true:suggestion
``` 

### <a name="expression_level_null_checking">"Null" 檢查中的聯合運算式</a>
|  選項名稱 | `dotnet_style_coalesce_expression` |
| ------------- |:-------------:|
| **適用的語言** | C# 和 Visual Basic

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好 null 聯合運算式勝過三元運算子檢查。| **C#:** <br>`var v = x ?? y;` <br><br> **Visual Basic:** <br> `Dim v = If(x, y)`
| False | 偏好三元運算子檢查勝過 null 聯合運算式。 | **C#:** <br>`var v = x != null ? x : y; // or`<br>`var v = x == null ? y : x;` <br><br> **Visual Basic:** <br>`Dim v = If(x Is Nothing, y, x) ' or`<br> `Dim v = If(x IsNot Nothing, x, y)`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_coalesce_expression = true:suggestion
``` 

### <a name="expression_level_null_propogation">"Null" 檢查中的 Null 傳播</a>
|  選項名稱 | `dotnet_style_null_propagation` |
| ------------- |:-------------:|
| **適用的語言** | C# 和 Visual Basic

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好盡可能使用 null 條件運算子。| **C#:** <br>`var v = o?.ToString();` <br><br> **Visual Basic:** <br> `Dim v = o?.ToString()`
| False | 偏好盡可能使用三元 null 檢查。 | **C#:** <br>`var v = o == null ? null : o.ToString(); // or`<br>`var v = o != null ? o.String() : null;` <br><br> **Visual Basic:** <br>`Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or`<br> `Dim v = If(o IsNot Nothing, o.ToString(), Nothing)`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_null_propagation = true:suggestion
``` 

# <a name="csharp_codestyle">CSharp 程式碼樣式設定</a>
## <a name="var">"var"</a>
### <a name="var_built_in">內建類型的 "var"</a>
|  選項名稱 | `csharp_style_var_for_built_in_types` |
| ------------- |:-------------:|
| **適用的語言** | C#

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好針對內建系統類型，例如 `int` 使用 `var`。| **C#:** <br>`var x = 5;`
| False | 偏好不針對內建系統類型，例如 `int` 使用 `var`。 | **C#:** <br>`int x = 5;`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
``` 

### <a name="var_apparent">類型明顯時的 "var"</a>
|  選項名稱 | `csharp_style_var_when_type_is_apparent` |
| ------------- |:-------------:|
| **適用的語言** | C#

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 在宣告運算式右側已提到類型時偏好使用 `var`。| **C#:** <br>`var obj = new C();`
| False | 在宣告運算式右側已提到類型時偏好不使用 `var`。 | **C#:** <br>`C obj = new C();`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_var_when_type_is_apparent = true:suggestion
``` 

### <a name="var_elsewhere">他處的 "var"</a>
|  選項名稱 | `csharp_style_var_elsewhere` |
| ------------- |:-------------:|
| **適用的語言** | C#

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 在所有情況下，除非由另一個程式碼樣式規則覆寫，否則偏好使用 `var`。| **C#:** <br>`var f = this.Init();`
| False | 在所有情況下，除非由另一個程式碼樣式規則覆寫，否則偏好不使用 var。| **C#:** <br>`bool f = this.Init();`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_var_elsewhere = true:suggestion
``` 

### <a name="expression_bodied_members">方法</a>
|  選項名稱 | `csharp_style_expression_bodied_methods` |
| ------------- |:-------------:|
| **適用的語言** | C#

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好針對方法使用運算式主體的成員。| **C#:** <br>`public int GetAge() => this.Age;`
| False | 偏好針對方法不使用運算式主體的成員。| **C#:** <br>`public int GetAge() { return this.Age; }`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
``` 

### <a name="expression_bodied_members_constructors">建構函式</a>
|  選項名稱 | `csharp_style_expression_bodied_constructors` |
| ------------- |:-------------:|
| **適用的語言** | C#

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好針對建構函式使用運算式主體的成員。| **C#:** <br>`public Customer(int age) => Age = age;`
| False | 偏好針對建構函式不使用運算式主體的成員。| **C#:** <br>`public Customer(int age) { Age = age; }`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_constructors = false:none
``` 

### <a name="expression_bodied_members_operators">運算子</a>
|  選項名稱 | `csharp_style_expression_bodied_operators` |
| ------------- |:-------------:|
| **適用的語言** | C#

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好針對運算子使用運算式主體的成員。| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`=> new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);`
| False | 偏好針對運算子不使用運算式主體的成員。| **C#:** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_operators = false:none
``` 

### <a name="expression_bodied_members_properties">屬性</a>
|  選項名稱 | `csharp_style_expression_bodied_properties` |
| ------------- |:-------------:|
| **適用的語言** | C#

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好針對屬性使用運算式主體的成員。| **C#:** <br>`public int Age => _age;`
| False | 偏好針對屬性不使用運算式主體的成員。| **C#:** <br>`public int Age { get { return _age; }}`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_properties = false:none
``` 

### <a name="expression_bodied_members_indexers">索引子</a>
|  選項名稱 | `csharp_style_expression_bodied_indexers` |
| ------------- |:-------------:|
| **適用的語言** | C#

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好針對索引子使用運算式主體的成員。| **C#:** <br>`public T this[int i] => _value[i];`
| False | 偏好針對索引子不使用運算式主體的成員。| **C#:** <br>`public T this[int i] { get { return _values[i]; } }`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_indexers = false:none
``` 

### <a name="expression_bodied_members_accessors">存取子</a>
|  選項名稱 | `csharp_style_expression_bodied_accessors` |
| ------------- |:-------------:|
| **適用的語言** | C#

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好針對存取子使用運算式主體的成員。| **C#:** <br>`public int Age { get => _age; set => _age = value; }`
| False | 偏好針對存取子不使用運算式主體的成員。| **C#:** <br>`public int Age { get { return _age; } set { _age = value; } }`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_accessors = false:none
``` 

## <a name="pattern_matching">模式比對</a>
### <a name="pattern_matching_is_cast">"is" 與 "cast" 檢查</a>
|  選項名稱 | `csharp_style_pattern_matching_over_is_with_cast_check` |
| ------------- |:-------------:|
| **適用的語言** | C#

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好模式比對，而非具有類型轉換的 `is`運算式。| **C#:** <br>`if (o is int i) {...}`
| False | 偏好具有類型轉換的 `is` 運算式，而非模式比對。| **C#:** <br>`if (o is int) {var i = (int)o; ... }`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
```

### <a name="pattern_matching_as_null">"as" 與 "null" 檢查</a>
|  選項名稱 | `csharp_style_pattern_matching_over_as_with_null_check` |
| ------------- |:-------------:|
| **適用的語言** | C#

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好模式比對，而非具有 null 檢查的 `as` 運算式，以判斷是否為特定類型。| **C#:** <br>`if (o is string s) {...}`
| False | 偏好具有 null 檢查的 `as` 運算式，而非模式比對，以判斷是否為特定類型。| **C#:** <br>`var s = o as string; if (s != null) {...}`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

### <a name="inlined_variable_declarations">內嵌變數宣告</a>
|  選項名稱 | `csharp_style_inlined_variable_declaration` |
| ------------- |:-------------:|
| **適用的語言** | C#

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好盡可能內嵌宣告 `out` 變數。 | **C#:** <br>`if (int.TryParse(value, out int i) {...}`
| False | 偏好明確宣告 `out` 變數。| **C#:** <br>`int i; if (int.TryParse(value, out i) {...}`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

## <a name="null_checking">"Null" 檢查喜好設定</a>
### <a name="null_checking_throw_expressions">Throw 運算式</a>
|  選項名稱 | `csharp_style_throw_expression` |
| ------------- |:-------------:|
| **適用的語言** | C#

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 偏好使用 throw 運算式，而不是 throw 陳述式。 | **C#:** <br>`this.s = ss ?? throw new ArgumentNullException(nameof(s));`
| False | 偏好使用 throw 陳述式，而不是 throw 運算式。| **C#:** <br>`if (s==null) {throw new ArgumentNullException(nameof(s));} this.s = s;`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
```

### <a name="null_checking_conditional_delegate_calls">偏好條件式委派呼叫</a>
|  選項名稱 | `csharp_style_conditional_delegate_call` |
| ------------- |:-------------:|
| **適用的語言** | C#

| 值 | 描述 | 已套用 
| ------------- |:-------------|:-------------|
| True | 叫用 lambda 時偏好使用條件式聯合運算 (`?.`) 而不是執行 null 檢查。 | **C#:** <br>`func?.Invoke(args);`
| False | 偏好先執行 null 檢查，再叫用 Lambda，而不使用條件式聯合運算子 (`?.`)。| **C#:** <br>`if (func!=null) { func(args); }`

#### Editorconfig 檔案範例︰
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_conditional_delegate_call = false:suggestion
```

