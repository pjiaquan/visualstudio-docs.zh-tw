---
title: "XML 編輯器 IntelliSense 功能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# XML 編輯器 IntelliSense 功能
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML 編輯器提供完整的 IntelliSense 功能，其相當於 Visual Studio 中提供的其他語言編輯器。本節說明如何使用 IntelliSense \(XSLT\) 搭配 XML 結構定義語言 \(XSD\) 與 XSLT 文件。  
  
## XSD 文件中的 IntelliSense  
 結構描述與文件相關聯後，只要您輸入 `"<"` 或按一下 XML 編輯器工具列上的 \[**顯示物件的成員清單**\] 按鈕，就會出現預期項目的下拉式清單。如需如何使結構描述與 XML 文件相關聯的詳細資訊，請參閱 [XML 文件驗證](../xml-tools/xml-document-validation.md)。  
  
 從開始標記內鍵入 SPACE 時，您也會取得一個下拉式清單，顯示可加入到目前項目的全部屬性。  
  
 針對屬性值鍵入 `"="`，或鍵入值的開頭引號時，也會取得該屬性的可能值清單。只有透過 `xsd:enumeration` Facet 提供列舉值，或者屬性是 `Boolean` 型別時，才會提供值。還會為 `xml:lang` 或衍生自 `xsd:language` 的任何 `simpleType`，提供已知語言代碼的 IntelliSense 清單。會為命名空間宣告提供已知 `targetNamespace` 值的 IntelliSense 清單。  
  
 如果項目是 `simpleType`，則當您鍵入 `">"` 以關閉開始標記時，還會提供可能值的 IntelliSense 清單。項目的行為與前一段中說明的屬性行為相類似。  
  
 根據在相關結構描述中找到的 `xsd:annotation` 及 `xsd:documentation` 資訊，這些 IntelliSense 清單上還會出現工具提示。  
  
## XSLT 文件中的 IntelliSense  
 在您將具名範本或屬性加入至 XSLT 文件後，即可使用 IntelliSense 插入下列內容：  
  
-   屬性集名稱。  
  
-   範本模式。  
  
-   範本名稱。  
  
-   指定模式的參數名稱。‏  
  
-   指定具名範本的參數名稱。‏  
  
 如需詳細資訊，請參閱[逐步解說：使用 XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md)主題。  
  
## 自動完成  
 XML 編輯器還可藉由填入必要的 XML 語法，使編輯 XML 變得更容易。例如，如果您鍵入下列開始標記：  
  
 `<book>`  
  
 XML 編輯器會填入結束標記，並將游標置於開啟標記後面。下列是此情況的範例 \(其中 &#124; 表示游標位置\)：  
  
 `<book>`&#124;`</book>`  
  
 因為屬性值必須永遠帶有引號，所以 XML 編輯器會填入引號。例如，如果您鍵入下列內容：  
  
 `<book title=`  
  
 XML 編輯器會加入引號，並將游標置於引號之間：  
  
 `<book title="`&#124;`"`  
  
 同樣地，XML 編輯器還會自動插入下列 XML 語法：  
  
-   結束處理指示：`?>`  
  
-   結束 CDATA 區塊：`]]>`  
  
-   結束註解：`-->`  
  
-   結束 DTD 宣告：`>`  
  
 如果您從 IntelliSense 清單選取命名空間限定的項目或屬性，且該項目或屬性的命名空間尚不在範圍內，則 XML 編輯器還具有插入命名空間宣告的功能。  
  
 例如，如果您從 IntelliSense 清單中選取 `e:Book` 項目，該清單中的前置詞繫結至尚未在文件中宣告的 `http://books` 命名空間，則 XML 編輯器會插入必要的命名空間宣告。下列是產生的 XML 文字：  
  
 `<e:Book xmlns:e="http://books"`  
  
## 括號對稱  
 XML 編輯器提供括號反白顯示，以將您剛剛關閉之項目的立即回應提供給您。您也可以使用鍵盤快速鍵 \(CTRL\+\]\)，從一個括號跳至對稱的括號。  
  
 XML 編輯器會針對下列項目執行此操作：  
  
-   對稱的開始與結束標記。  
  
-   任意一對 \< 或 \> 角括號。  
  
-   註解的開始與結束。  
  
-   處理指示的開始與結束。  
  
-   CDATA 區塊的開始與結束。  
  
-   DTD 宣告的開始與結束。  
  
-   屬性上的開頭及結束引號。  
  
## 修改 IntelliSense 選項  
 依預設會啟用 IntelliSense 及自動完成功能。但是，您可藉由修改 \[工具\] \- \[選項\] 設定來對其進行變更。  
  
 \[其他\] 頁面的 \[自動插入\] 區段控制下列行為：  
  
|名稱|說明|  
|--------|--------|  
|關閉標記|插入新項目的關閉標記。|  
|屬性引號|輸入新屬性名稱時，請插入屬性值引號。|  
|其他標記|完成註解、CDATA、DOCTYPE、處理指示及其他標記宣告。|  
  
#### 變更自動完成行為  
  
1.  從 \[工具\] 功能表中選取 \[選項\]。  
  
2.  依序展開 \[文字編輯器\] 及 \[XML\] 後，再選取 \[其他\]。  
  
3.  變更 \[自動插入\] 區段，再按一下 \[確定\]。  
  
## 請參閱  
 [XML 編輯器](../xml-tools/xml-editor.md)   
 [使用 IntelliSense](../ide/using-intellisense.md)   
 [逐步解說：使用 XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md)