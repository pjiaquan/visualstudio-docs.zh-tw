---
title: "XML 結構描述對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# XML 結構描述對話方塊
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**\[XML 結構描述\]** 對話方塊用於要選取哪個 XML 結構描述定義語言 \(XSD\) 結構描述與 XML 文件產生關聯。您可以從結構描述快取中選取結構描述，或指定快取中沒有的結構描述。選取的結構描述會被視為結構描述集的一部分。結構描述集用於 IntelliSense 以及 XML 文件驗證。  
  
 您可以按一下文件屬性視窗上的 **\[結構描述\]** 按鈕，或從 **\[XML\]** 功能表選取 **\[結構描述\]**，來存取 **\[XML 結構描述\]** 對話方塊。  
  
## UIElement 清單  
 **使用**  
 選取如何使用 XML 結構描述。  
  
-   **自動**：目前的文件沒有使用這個結構描述，但是可用於自動關聯。如果 XML 文件宣告符合此結構描述之 `targetNamespace` 的命名空間，將會自動關聯該結構描述，而且會包含在結構描述集中。  
  
-   **使用此結構描述**：此結構描述正由目前的文件所使用。使用者已經明確要求藉由按一下此結構描述來使用該結構描述，或者讓結構描述根據相符的 `targetNamespace` 自動關聯。  
  
-   **不要使用選取的結構描述**：即使結構描述擁有相符的 `targetNamespace`，目前的文件也不會使用此結構描述。在結構描述快取或方案中有一個以上相同結構描述的版本時，這個設定對於解決衝突可能很實用。  
  
 **目標命名空間**  
 顯示與 XML 結構描述相關聯的目標命名空間。  
  
 **檔案名稱**  
 顯示 XML 結構描述檔案名稱。  
  
 **加入**  
 開啟 **\[開啟 XSD 結構描述\]** 對話方塊，可讓您選取其他結構描述以便加入到結構描述集中。將結構描述加入到結構描述集中時，**\[使用\]** 資料行值會設定為 **\[使用此結構描述\]**。  
  
 **移除**  
 從結構描述集移除目前選取的結構描述。這樣會從記憶體中的結構描述快取 \(但不會從檔案系統\) 移除結構描述。  
  
## 請參閱  
 [XML 編輯器元件](../xml-tools/xml-editor-components.md)   
 [HOW TO：選取要使用的 XML 結構描述](../xml-tools/how-to-select-the-xml-schemas-to-use.md)   
 [結構描述快取](../xml-tools/schema-cache.md)