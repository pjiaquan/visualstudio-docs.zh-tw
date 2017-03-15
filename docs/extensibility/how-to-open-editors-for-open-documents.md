---
title: "如何: 開啟編輯器開啟的文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，開啟的文件開啟"
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 如何: 開啟編輯器開啟的文件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

開啟文件視窗的專案之前，專案第一次必須判斷檔案是否已開啟在另一個編輯器之文件視窗中。  檔案可能會在 \[專案專用編輯器開啟，或是其中一個標準編輯器註冊與[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## 開啟專案專用編輯器  
 若要開啟已經開啟的檔案之專案專用編輯器，請使用下列程序。  
  
#### 若要開啟 \[開啟檔案之專案專用編輯器  
  
1.  呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 方法。  
  
     這個呼叫返回指標文件的階層架構、 階層架構的項目和視窗外框，如果適當的話。  
  
2.  如果文件開啟時，專案必須檢查是否只有文件資料的物件存在，或如果文件檢視物件也會出現。  
  
    -   如果文件檢視物件，且此檢視是不同的階層架構或階層項目時，專案會使用檢視表的視窗框架的指標 resurface 現有視窗。  
  
    -   如果文件檢視物件，且此檢視是相同的階層架構和階層架構項目時，專案可以開啟第二個檢視，如果它可以將它附加到基礎的文件資料物件。  否則，專案應該使用檢視\] 視窗框架的指標，resurface 現有視窗。  
  
    -   如果只有文件的資料物件的話，專案應該判斷是否它可用於文件的資料物件的檢視。  如果文件的資料物件是相容的完成這些步驟中所討論[開啟專案專用編輯器](../extensibility/how-to-open-project-specific-editors.md)。  
  
     如果文件的資料物件不相容，錯誤應該會顯示給使用者，表示檔案正在使用中。  這項錯誤應該只會顯示在暫時性的情況下，例如與使用者時一次編譯檔案時嘗試開啟檔案，而非使用編輯器[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心文字編輯器。  核心文字編輯器可以使用編譯器共用文件資料物件。  
  
3.  如果文件尚未開啟，因為沒有文件資料物件或文件檢視物件，請完成步驟中的[開啟專案專用編輯器](../extensibility/how-to-open-project-specific-editors.md)。  
  
## 開啟標準編輯器  
 使用下列程序，以開啟檔案已存在的標準編輯器開啟。  
  
#### 若要開啟 \[開啟檔案的標準編輯器  
  
1.  請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>。  
  
     這個方法會先驗證文件是否已開啟藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>。  如果已開啟的文件，則其 \[編輯器\] 視窗被 resurfaced。  
  
2.  如果尚未開啟文件，則完成步驟[如何: 開啟標準編輯器](../extensibility/how-to-open-standard-editors.md)。  
  
## 請參閱  
 [開啟並儲存專案項目](../extensibility/internals/opening-and-saving-project-items.md)   
 [如何: 開啟專案的特定編輯器](../extensibility/how-to-open-project-specific-editors.md)   
 [如何: 開啟標準編輯器](../extensibility/how-to-open-standard-editors.md)