---
title: "HOW TO：選取要使用的 XML 結構描述 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# HOW TO：選取要使用的 XML 結構描述
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML 編輯器提供位於 %InstallDir%\\Xml\\Schemas 目錄的結構描述快取。結構描述快取包括用於 IntelliSense 及 XML 文件驗證的常見 XML 結構描述。  
  
 **Schemas** 文件屬性可用於選取要使用的一或多個 XML 結構描述定義語言 \(XSD\) 結構描述。它可讓您從結構描述快取中選取結構描述，或指定快取中沒有的結構描述。  
  
 您所指定的結構描述與其他所有 XML 文件屬性，會一起儲存在隱藏的解決方案使用者選項檔 \(.suo\) 中。因此，在下次開啟解決方案時無需重新輸入這些值。  
  
> [!NOTE]
>  編輯器可使用內嵌結構描述，或由 `xsd:schemaLocation` 屬性參考的結構描述進行驗證。如需詳細資訊，請參閱 [XML 文件驗證](../xml-tools/xml-document-validation.md)。  
  
### 若要從結構描述快取選取 XML 結構描述  
  
1.  在 XML 編輯器中開啟檔案。  
  
2.  在文件屬性視窗中，按一下 \[結構描述\] 欄位上的按鈕。  
  
     會顯示 \[XML 結構描述\] 對話方塊。該對話方塊會列出結構描述快取中具 .xsd 副檔名的所有結構描述 \(包括 catalog.xml 檔案所參考的結構描述\)，以及任何存在於目前解決方案中、已於 Visual Studio 中開啟、`xsd:schemaLocation` 屬性所參考或 **Schemas** 屬性所參考的結構描述。  
  
3.  請進行下列任一操作，以選取用於驗證的結構描述：  
  
    -   選取列在 **\[XML 結構描述\]** 對話方塊中的結構描述，按一下 **\[使用\]** 資料行，然後選取 **\[使用此結構描述\]**。  
  
     \- 或 \-  
  
    -   選取列在 **\[XML 結構描述\]** 對話方塊中的多個結構描述，按一下滑鼠右鍵，然後選取 **\[使用此結構描述\]**。  
  
4.  按一下 \[確定\]。  
  
     將所選結構描述的清單複製回 \[結構描述\] 文件屬性中。  
  
### 若要將 XML 結構描述加入結構描述快取中  
  
1.  在文件屬性視窗中，按一下 **\[結構描述\]** 欄位上的按鈕。  
  
2.  按一下 \[加入\]。  
  
     這會開啟 **\[開啟 XSD 結構描述\]** 對話方塊。  
  
3.  瀏覽並選取要加入到結構描述快取中的結構描述。  
  
4.  按一下 **\[開啟\]**。  
  
     結構描述會加入到結構描述快取中，而且 **\[使用\]** 資料行值會設定為 **\[使用此結構描述\]**。  
  
### 若要從結構描述快取刪除 XML 結構描述  
  
1.  在文件屬性視窗中，按一下 **\[結構描述\]** 欄位上的按鈕。  
  
2.  選取要移除的結構描述，然後按一下 **\[移除\]**。  
  
     結構描述會從記憶體中的結構描述快取移除，但不會從檔案系統中移除。  
  
    > [!NOTE]
    >  如果您仍然透過 `schemaLocation` 屬性擁有結構描述的參考或符合的 `targetNamespace`，在這種情況下，自動關聯會導致 \[**移除**\] 無法運作。在這個情況下，建議您在 **\[使用\]** 資料行中，將結構描述標示為 **\[不要使用選取的結構描述\]**。  
  
## 請參閱  
 [結構描述快取](../xml-tools/schema-cache.md)   
 [XML 結構描述對話方塊](../xml-tools/xml-schemas-dialog-box.md)   
 [XML 編輯器](../xml-tools/xml-editor.md)