---
title: "HOW TO：搭配使用 XML 結構描述設計工具和 XML 常值 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# HOW TO：搭配使用 XML 結構描述設計工具和 XML 常值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題描述如何在 Visual Studio 專案中檢視與 XML 常值相關的結構描述。  
  
### 建立新的 Visual Basic 主控台應用程式專案  
  
1.  啟動 Visual Studio 2010。  
  
2.  從 \[檔案\] 功能表中選取 \[新增\]，再選取 \[專案\]。\[**新增專案**\] 對話方塊隨即出現。在 \[**專案類型**\] 中選取 \[**其他語言**\]，然後選取 \[**Visual Basic**\]。在 \[**專案**\] 中選取 \[主控台應用程式\]。然後在 \[**名稱**\] 欄位中輸入 `XMLLiterals`，並在 \[**位置**\] 欄位中輸入專案位置。按一下 \[**確定**\]。  
  
     隨即會建立新專案。XMLLiterals 專案包含一個 Visual Basic 原始程式檔：Module1.vb。  
  
### 將現有 XSD 檔案加入至專案  
  
1.  在 \[記事本\] 中開啟新的文字檔。複製[採購單結構描述](../xml-tools/sample-xsd-file-simple-schema.md)中的 XML 結構描述範例程式碼，並貼至檔案中。  
  
2.  將檔案儲存至某個位置並命名為 PurchaseOrderSchema.xsd。  
  
3.  在方案總管中，以滑鼠右鍵按一下專案的名稱，然後依序選取 \[**加入**\] 和 \[**現有項目**\]。\[**加入現有項目**\] 對話方塊隨即出現。瀏覽並選取 PurchaseOrderSchema.xsd 檔案，然後按一下 \[**加入**\]。  
  
     XMLLiterals 專案現在會包含兩個檔案：Module1.vb 和 PurchaseOrderSchema.xsd。  
  
### 根據專案中包含的 XSD 檔案，加入含有 XML 常值的 Visual Basic 程式碼  
  
1.  以下列程式碼取代 Module1.vb 檔中的程式碼：  
  
    ```  
    Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">  
  
    Module Module1  
        Sub Main()  
  
            Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">  
                                 <ns:ShipTo country="US">  
                                     <ns:name>name1</ns:name>  
                                     <ns:street>street1</ns:street>  
                                     <ns:city>city1</ns:city>  
                                     <ns:state>state1</ns:state>  
                                     <ns:zip>1</ns:zip>  
                                 </ns:ShipTo>  
                                 <ns:BillTo country="US">  
                                     <ns:name>name1</ns:name>  
                                     <ns:street>street1</ns:street>  
                                     <ns:city>city1</ns:city>  
                                     <ns:state>state1</ns:state>  
                                     <ns:zip>1</ns:zip>  
                                 </ns:BillTo>  
                             </ns:PurchaseOrder>  
  
        End Sub  
    End Module  
    ```  
  
2.  以滑鼠右鍵按一下 XML 常值或 XML 命名空間匯入中的任何 XML 節點，並選取 \[**在結構描述總管中顯示**\]。  
  
     XML 結構描述總管會與一個 Visual Basic 檔案並排顯示，此檔案具有與 XML 結構描述集相關的 XML 常值。