---
title: "如何: 更新狀態 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版-更新狀態列"
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何: 更新狀態
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**狀態列**一項控制列位於包含一個或多個狀態文字行標記許多應用程式視窗的下方。  
  
### 若要更新狀態列  
  
1.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>上每個個別的 view 物件 \(DocView\)，它提供您的編輯器，例如表單檢視\] 和 \[程式碼\] 檢視。  
  
2.  當 IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>，更新中的資訊**狀態列**是呼叫的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>。  
  
    > [!NOTE]
    >  IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>只有當文件視窗一開始啟動。  接下來的過程的文件視窗為作用中的時間，您必須更新**狀態列**為編輯器變更後的狀態資訊。  
  
## 穩固程式設計  
 A **狀態列**包含四個不同的欄位:  
  
-   狀態文字  
  
-   Progress bar  
  
-   動畫的圖示  
  
-   編輯器的資訊  
  
 如需詳細資訊，請參閱 [狀態列](/visual-cpp/mfc/status-bars)。  
  
 IDE 會自動呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>方法的程式<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>時就會啟動您的文件視窗的實作。  
  
 VSPackage 實作器負責更新狀態文字會在狀態列上。  IDE 在如果狀態的 \[文字\] 欄位設定為 \[空的文字，會重設為 「 就緒 」 這個字串 \(""\) 在閒置的時間。  
  
## 請參閱  
 [狀態列](/visual-cpp/mfc/status-bars)