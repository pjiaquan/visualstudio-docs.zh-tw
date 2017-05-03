---
title: "lbound 方法 (VBArray) (JavaScript) | Microsoft Docs"
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
  - "lbound"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lbound 方法"
ms.assetid: 30ff5e8a-8165-494b-bce8-0a562ec2eec3
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# lbound 方法 (VBArray) (JavaScript)
傳回使用在指定 VBArray 維度中的最低索引值。  
  
## 語法  
  
```  
  
safeArray.lbound(dimension)   
```  
  
## 參數  
 *safeArray*  
 必要項。  VBArray 物件。  
  
 `dimension`  
 選擇項。  需要較低索引上限的 VBArray 維度。  若予以省略，`lbound` 的行為就和傳遞 1 一樣。  
  
## 備註  
 如果 VBArray 是空的，`lbound` 方法會傳回 undefined。  若 `dimension` 大於 VBArray 中的維度數目或為負值的話，則此方法會產生「陣列索引超出範圍」的錯誤。  
  
## 範例  
 下列範例由三個部分構成。  第一個部分的 VBScript 程式碼是用來建立 Visual Basic 安全陣列。  第二個部分的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 程式碼是用來決定安全陣列中的維度數目以及每個維度的下限。  由於安全陣列是以 VBScript 而非 Visual Basic 建立的，因此下限一律為零。  這兩部分都會進入 HTML 網頁的 \<HEAD\> 區段。  第三個部分的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 程式碼則是放在 \<BODY\> 區段來執行其他兩個部分。  
  
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
function VBArrayTest(vba){  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The lower bound of dimension ";  
      s += i + " is ";  
      s += a.lbound(i);  
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
 下列文件模式有提供支援：Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準和 Internet Explorer 10 標準。  [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式不支援。  請參閱[版本資訊](../../javascript/reference/javascript-version-information.md)。  
  
 **適用於**：[VBArray 物件](../../javascript/reference/vbarray-object-javascript.md)  
  
## 請參閱  
 [dimensions 方法 \(VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem 方法 \(VBArray\)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [toArray 方法 \(VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound 方法 \(VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)