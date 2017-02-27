---
title: "其他檔案專案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "將現有的檔案加入至方案的檔案"
  - "其他檔案專案"
  - "方案項目資料夾"
  - "使用其他檔案專案開啟的檔案"
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 其他檔案專案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

當使用者開啟的專案項目時，IDE 指派至其他檔案專案不是成員的方案中的任何專案的任何項目。  
  
 專案中扮演相當重要的角色，決定當使用者開啟的專案項目使用的編輯器。  在設計專案時，可以使用專案專用編輯器 」 或 「 標準編輯器開啟某些檔案。  
  
 專案專用編輯器通常都會要求使用者具有特殊知識，或使用特殊的介面，從專案。  如需詳細資訊，請參閱 [如何: 開啟專案的特定編輯器](../../extensibility/how-to-open-project-specific-editors.md)。  
  
 標準編輯器可以開啟任何專案中的任何特定的副檔名的檔案。  使用者可以自訂一些標準的編輯器，例如[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案的文字編輯器，但仍保留其公用的字元。  藉由建立標準編輯器<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法。  
  
 如果方案中的任何專案不回應它可以開啟專案項目，則 IDE 會提供特別的專案，稱為其他檔案專案可開啟任何檔案。  
  
 此特殊專案提供內容以外的專案檔的開頭。  在處理<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>方法中，其他檔案專案永遠會以非常低的優先順序。  因此，其他檔案專案永遠會產生較高優先權的任何專案只能開啟檔案。  
  
 其他檔案專案不需要使用者明確地建立它與**新的專案**對話方塊。  此外，其他檔案專案不會永久管理專案成員的清單。  若要錄製的每一位使用者最近使用過檔案清單，它就會使用選擇性功能。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [如何: 開啟專案的特定編輯器](../../extensibility/how-to-open-project-specific-editors.md)   
 [如何: 開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)   
 [加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)