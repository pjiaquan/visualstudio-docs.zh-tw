---
title: "逐步解說：使用 XML 編輯器功能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 逐步解說：使用 XML 編輯器功能
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此逐步教學中的步驟顯示如何建立新的 XML 文件。逐步教學還會使用 XML 編輯器的部分功能，使其在 XML 撰寫上具有價值。  
  
> [!NOTE]
>  開始逐步教學之前，請先將 hireDate.xsd 檔 \(本主題下方所包含的檔案\) 儲存到本機電腦上。  
  
### 建立新的 XML 檔案，並將其與 XML 結構描述相關聯  
  
1.  在 \[檔案\] 功能表上，指向 \[新增\] 並按一下 \[檔案\]。  
  
2.  在 \[範本\] 窗格中選取 \[XML 檔案\]，並按一下 \[開啟\]。  
  
     編輯器中會開啟新的檔案。檔案包含預設的 XML 宣告，`<?xml version="1.0" encoding="utf-8">`。  
  
3.  在文件屬性視窗中，按一下 \[結構描述\] 欄位上的瀏覽按鈕 \(**...**\)。  
  
     會顯示 \[XSD 結構描述\] 對話方塊。  
  
4.  按一下 \[加入\]。  
  
     會顯示 \[開啟 XSD 結構描述\] 對話方塊。  
  
5.  選取 hireDate.xsd 檔案，並按一下 \[開啟\]。  
  
6.  按一下 \[確定\]。  
  
     XML 結構描述現在已與 XML 文件相關聯。XML 結構描述用於驗證文件。它也由 IntelliSense 用於填入有效項目的成員清單。  
  
### 加入資料  
  
1.  在編輯器窗格中鍵入 `<`。  
  
     成員清單會顯示可能的項目：  
  
    -   **\!\-\-** \- 加入註解。  
  
    -   **\!DOCTYPE** \- 加入文件型別。  
  
    -   **?** \- 加入處理指示。  
  
    -   **employee** \- 加入根項目。  
  
2.  選取 **\<\!\-\-** 來加入註解節點，並按 ENTER 鍵。  
  
     編輯器會插入註解結束標記，並將游標置於開始與結束註解標記之間。  
  
3.  鍵入測試 XML 檔案。  
  
4.  在新的一行上，鍵入 `<`，並從成員清單中選取 \[employee\]。  
  
     編輯器會加入 XML 項目的開始部分，`<employee`。此時您可以將屬性加入項目，或藉由鍵入 `>` 來關閉開始標記。  
  
5.  鍵入 `>` 以關閉標記。  
  
6.  編輯器會加入結束標記。加入的結束標記會帶有波浪底線，表示驗證錯誤。工具提示會顯示訊息：項目「employee」的內容不完整。預期的是 'ID'。  
  
7.  鍵入 `<` 並自成員清單中選擇 **ID**。然後鍵入 `>`。  
  
     編輯器會加入 XML 項目 `<ID></ID>`，並將游標置於 ID 開始標記之後。  
  
8.  鍵入 abc。  
  
     abc 文字帶有波浪底線。工具提示會顯示訊息：根據其資料型別，「ID」項目有無效的值。  
  
9. 在 ID 項目上按一下滑鼠右鍵，並選取 \[移至定義\]。  
  
     編輯器會在新的文件視窗中開啟 hireDate.xsd 檔案，並將游標置於 ID 結構描述項目定義上。  
  
10. 返回至 XML 檔案，以 123 取代 abc 文字。  
  
     會清除 ID 項目值之下的波浪底線及工具提示。此時 employee 結束標記的工具提示會顯示訊息：項目「employee」的內容不完整。預期的 hire\-date。  
  
11. 將游標置於 ID 結束標記的後面，鍵入 `<`，並自成員清單中選取 hire\-date，然後鍵入 `>`。  
  
     編輯器會加入 XML 項目 `<hire-date></hire-date>`，並將游標置於 hire\-date 開始標記之後。  
  
12. 鍵入 2003\-01\-10 做為 hire\-date 值。  
  
### 格式化 XML 文件  
  
1.  從 XML 編輯器工具列中選取 \[格式化文件\] 按鈕。  
  
     會重新格式化 XML 文件。  
  
### 儲存 XML 文件  
  
1.  從 \[檔案\] 功能表中選取 \[另存新檔\]。  
  
     會顯示 \[存檔類型\] 對話方塊。預設的檔案名稱是 XMLFile1。  
  
2.  輸入 XML 文件的檔案名稱及位置，並按一下 \[儲存\]。  
  
## hireDate.xsd 檔案  
 下列結構描述檔案由逐步教學使用。  
  
```  
<?xml version="1.0"?>  
<xs:schema attributeFormDefault="unqualified"  
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"  
     xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="employee">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="ID" type="xs:unsignedShort" />  
        <xs:element name="hire-date" type="xs:date" />  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## 請參閱  
 [XML 編輯器](../xml-tools/xml-editor.md)