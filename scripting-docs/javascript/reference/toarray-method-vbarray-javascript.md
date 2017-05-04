---
title: "toArray 方法 (VBArray) (JavaScript) | Microsoft Docs"
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
  - "toArray"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toArray 方法"
ms.assetid: 664de44c-2039-4289-82f6-948e9d744d80
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# toArray 方法 (VBArray) (JavaScript)
傳回從 VBArray 轉換的標準 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 陣列。  
  
## 語法  
  
```  
  
safeArray.toArray( )  
```  
  
## 備註  
 必要的 *safeArray* 參考是 VBArray 物件。  
  
 此轉換會將多維 VBArray 翻譯成一維 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 陣列。 每個後續的維度都會附加至前一個維度的結尾。 例如，具有三個維度且每個維度包含三個元素的 VBArray 會轉換成如下所示的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 陣列：  
  
 假設 VBArray 包含：\(1, 2, 3\), \(4, 5, 6\), \(7, 8, 9\)。 翻譯後，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 陣列會包含：1, 2, 3, 4, 5, 6, 7, 8, 9。  
  
 目前沒有任何方法可以將 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 陣列轉換成 VBArray。  
  
## 範例  
 下列範例由三個部分組成。 第一個部分是 VBScript 程式碼，用以建立 Visual Basic 安全陣列。 第二個部分是 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 程式碼，用以將 Visual Basic 安全陣列轉換成 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 陣列。 這兩個部分都會放在 HTML 網頁的 \<HEAD\> 區段中。 第三個部分是 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 程式碼，則是放在 \<BODY\> 區段以執行其他兩個部分。  
  
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
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<BR>")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vbarray)  
{  
   var a = new VBArray(vbarray);  
   var b = a.toArray();  
   var i;  
   for (i = 0; i < 9; i++)   
   {  
      document.writeln(b[i]);  
   }  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
<!--  
   VBArrayTest(CreateVBArray());  
-->  
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
 [ubound 方法 \(VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)