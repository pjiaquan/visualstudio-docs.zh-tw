---
title: "HOW TO：編輯 XML 檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# HOW TO：編輯 XML 檔案
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML 編輯器是 XML 檔案的新編輯器。它可用於獨立 XML 檔案或與 Visual Studio 專案相關的檔案上。XML 編輯器與下列副檔名相關：.config、.dtd、.xml、.xsd、.xdr、.xsl、.xslt 和 .vssettings。XML 編輯器也與未登錄特定編輯器，且包含 XML 或 DTD 內容的任何其他檔案類型相關聯。  
  
> [!NOTE]
>  HTML 編輯器可處理 XHTML 文件。  
  
### 編輯 XML 檔案  
  
1.  按兩下要編輯的檔案。  
  
### 將新的 XML 檔案加入至專案  
  
1.  從 \[專案\] 功能表中，選取 \[加入新項目\]。  
  
2.  從 \[範本\] 窗格中，選取 \[XML 檔案\]。  
  
3.  在 \[名稱\] 欄位中輸入檔案名稱，並按 \[加入\]。  
  
     將 XML 檔案加入至專案，並在 XML 編輯器中開啟它。檔案包含預設的 XML 宣告，`<?xml version="1.0" encoding="utf-8" ?>`。  
  
### 將現有 XML 檔案加入至專案  
  
1.  從 \[專案\] 功能表中，選取 \[加入現有項目\]。  
  
     會出現 \[加入現有項目\] 對話方塊。  
  
2.  選取 XML 檔，並按 \[加入\]。  
  
### 建立新的 XML 或 XSLT 檔  
  
1.  從 \[檔案\] 功能表中，選取 \[新增\]。  
  
     會出現 \[新增檔案\] 對話方塊。  
  
2.  選取 \[XML 檔案\] 以建立新的 XML 檔案，或者選取 \[XSLT 檔案\] 以建立新的 XSLT 樣式表。  
  
3.  按一下 \[開啟\]。  
  
### 建立 XML 檔案的專案  
  
1.  從 \[檔案\] 功能表中選取 \[新增\]，再選取 \[專案\]。  
  
     會出現 \[新增專案\] 對話方塊。  
  
2.  選取您選擇的程式碼語言，並選取 \[空專案\] 後，再按一下 \[確定\]。  
  
3.  將 XML 檔案加入至專案。  
  
     XML 編輯器會找到加入至此專案的結構描述，並在此專案開啟時編輯的任何 XML、結構描述或 XSLT 檔案中使用它們進行驗證及 IntelliSense。  
  
## 請參閱  
 [XML 編輯器](../xml-tools/xml-editor.md)   
 [XML 文件屬性 \(屬性視窗\)](../xml-tools/xml-document-properties-properties-window.md)   
 [HOW TO：從 XML 文件建立 XML 結構描述](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)