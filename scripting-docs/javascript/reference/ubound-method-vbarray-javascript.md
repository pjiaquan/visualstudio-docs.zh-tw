---
title: "ubound 方法 (VBArray) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "ubound"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ubound 方法"
ms.assetid: 761811c5-9a3d-4cb3-bfe0-0a8749f34496
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# ubound 方法 (VBArray) (JavaScript)
傳回在指定之 VBArray 維度中使用的最高索引值。  
  
## 語法  
  
```  
  
safeArray.ubound(dimension)  
```  
  
## 參數  
 *safeArray*  
 必要項。 VBArray 物件。  
  
 `dimension`  
 選擇項。 需要較高索引上限的 VBArray 維度。 如果省略，`ubound` 的行為就如同傳遞 1 一般。  
  
## 備註  
 如果 VBArray 是空的，`ubound` 方法會傳回 undefined。 如果 `dim` 大於 VBArray 中的維度數目或為負值，則此方法會產生「陣列索引超出範圍」的錯誤。  
  
## 範例  
 下列範例由三個部分組成。 第一個部分是 VBScript 程式碼，用以建立 Visual Basic 安全陣列。 第二個部分的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 程式碼是用來決定安全陣列中的維度數目以及每個維度的上限。 這兩個部分都會放在 HTML 網頁的 \<HEAD\> 區段中。 第三個部分是 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 程式碼，則是放在 \<BODY\> 區段以執行其他兩個部分。  
  
```javascript  
<head>  
<script type="text/vbscript">  
<!--  
Function CreateVBArray()  
   Dim i, j, k  
   Dim a(2, 2)  
   k = 1  
   For i = 0 To 2  
      For j = 0 To 2  
         a(j, i) = k  
         k = k + 1  
      Next  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vba)  
{  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The upper bound of dimension ";  
      s += i + " is ";  
      s += a.ubound(i);  
      s += ".<br />";  
   }  
   return (s);  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
   document.write(VBArrayTest(CreateVBArray()));  
</script>  
</body>  
```  
  
## 需求  
 受下列文件模式支援：Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準和 Internet Explorer 10 標準。[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]應用程式不支援。 請參閱＜[版本資訊](../../javascript/reference/javascript-version-information.md)＞。  
  
 **適用於**：[VBArray 物件](../../javascript/reference/vbarray-object-javascript.md)  
  
## 請參閱  
 [dimensions 方法 \(VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem 方法 \(VBArray\)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [lbound 方法 \(VBArray\)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray 方法 \(VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)