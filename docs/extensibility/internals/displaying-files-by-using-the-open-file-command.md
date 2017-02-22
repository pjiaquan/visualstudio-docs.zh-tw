---
title: "使用 [開啟檔案] 命令顯示檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案類型，支援開啟檔案命令"
  - "開啟檔案命令"
  - "持續性，支援開啟檔案命令"
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 使用 [開啟檔案] 命令顯示檔案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下列步驟描述在 IDE 的處理方式**開啟的檔案**命令，可使用**檔案**在功能表[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  步驟也說明了呼叫來自這項指令，專案應該如何回應。  
  
 當使用者按一下**開啟的檔案** 命令 **檔案** 功能表中，並選取 \[來自檔案 **開啟的檔案**對話方塊中，下列程序。  
  
1.  使用執行文件表格，IDE 就會判斷檔案是否已開啟的專案中。  
  
    -   如果開啟檔案時，IDE 就會 resurfaces 視窗。  
  
    -   如果未開啟檔案時，IDE 便會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>來查詢每個專案，以判斷哪一個專案可以開啟檔案。  
  
        > [!NOTE]
        >  在您的專案實作的<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>，提供優先權值，指出專案隨即開啟該檔案的層級。  優先權值會提供<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列舉型別。  
  
2.  每個專案會回應表示重要性的優先等級也會將放在所要開啟該檔案的專案。  
  
3.  IDE 會使用下列準則來判斷哪一個專案開啟的檔案：  
  
    -   會以最高的優先順序 \(DP\_Intrinsic\) 回應的專案開啟的檔案。  如果具有此優先順序，回應多個專案，以回應第一個專案便會開啟檔案。  
  
    -   如果沒有專案會回應，具有最高的優先順序 \(DP\_Intrinsic\)，但擁有相同的、 較低優先順序的所有專案回應，使用中的專案就會開啟檔案。  如果沒有任何專案已啟用，以回應第一個專案便會開啟檔案。  
  
    -   如果沒有任何專案所宣稱擁有權的檔案 \(DP\_Unsupported\)，其他檔案專案就會開啟檔案。  
  
         如果其他檔案專案的執行個體建立時，專案永遠會回應以 DP\_CanAddAsExternal 的值。  這個值表示專案可以開啟檔案。  這個專案用來儲存開啟的檔案未在任何其他的專案。  在此專案中的項目清單並不會保留。 在這個專案中會顯示**方案總管\] 中**只有當它用來開啟檔案。  
  
         其他檔案專案，並不表示它可以開啟檔案，如果尚未建立專案的執行個體。  在此情況下，IDE 會建立其他檔案專案的執行個體，並告知專案\] 以開啟該檔案。  
  
4.  IDE 會決定哪一個專案開啟的檔案，因為它會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>該專案的方法。  
  
5.  專案則不會有使用專案專用編輯器\] 或 \[標準編輯器開啟檔案的選項。  如需詳細資訊，請分別參閱 [如何: 開啟專案的特定編輯器](../../extensibility/how-to-open-project-specific-editors.md)和 [如何: 開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)。  
  
## 請參閱  
 [顯示命令中使用 \[開啟檔案](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [開啟並儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)   
 [如何: 開啟專案的特定編輯器](../../extensibility/how-to-open-project-specific-editors.md)   
 [如何: 開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)