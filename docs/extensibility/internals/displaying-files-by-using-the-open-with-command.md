---
title: "顯示命令中使用 [開啟檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案類型中，開啟命令的支援"
  - "開啟命令"
  - "持續性，支援開啟命令"
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 顯示命令中使用 [開啟檔案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

專案可以要求顯示 IDE **開啟**對話方塊。  這項要求會提示使用者開啟有一系列標準編輯器的檔案。  下列步驟將說明這個程序。  
  
1.  專案呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>，指定的值為 OSE\_UseOpenWithDialog 的`OSEOpenDocEditor`參數。  
  
2.  根據文件的檔案名稱副檔名，IDE 判斷哪一個登錄可以所述的編輯器開啟指定的文件，並顯示資訊儲存在這個**開啟**對話方塊。  
  
    > [!NOTE]
    >  專案具有內建的編輯器，必須包含在**開啟**對話方塊必須登錄編輯程式每個這種編輯器。  僅運作中的內建的編輯器，與特定類型的實作會強制執行的專案一起<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。  IDE 會有內建的編輯器工廠的核心的文字編輯器\] 和 \[二進位編輯器。  IDE 也會建立每個已註冊的 Windows 檔案關聯的身份編輯器工廠的執行個體。  這類檔案的範例是 Microsoft Word。  
  
3.  當使用者選取的項目，從**開啟** \] 對話方塊中的 IDE，然後開啟文件，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法。  如需詳細資訊，請參閱 [如何: 開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)。  
  
## 請參閱  
 [開啟並儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)   
 [使用 \[開啟檔案\] 命令顯示檔案](../Topic/Displaying%20Files%20By%20Using%20the%20Open%20File%20Command.md)   
 [如何: 開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)