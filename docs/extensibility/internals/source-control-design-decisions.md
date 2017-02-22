---
title: "原始檔控制的設計決策 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原始檔控制 [Visual Studio SDK]，設計決策"
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 原始檔控制的設計決策
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

實作原始檔控制時，應該考慮下列的設計決策的專案。  
  
## 資訊會共用或私用吗？  
 您可以將最重要的設計決策是何種資訊可共用以及私用。  比方說，共用的專案檔案的清單，但在此清單內的檔案，某些使用者可能會希望自己能夠私用的檔案。  編譯器設定被共用，但通常私用啟動專案。  設定是純綷共用、 共用與覆寫，或純粹只是私用。  根據設計，私用的項目，例如方案使用者選項 \(.suo\) 檔案，不會檢查到[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]。  請務必將任何私人資訊儲存在私用的檔案，例如.suo 檔案中或特定的私人檔案，您建立時，比方說，。 csproj.user 檔案中的視覺 C\# \(含\)。 Visual Basic 的 vbproj.user 檔案。  
  
 這項決策不全面，而且可以由項目由項目為基礎。  
  
## 將專案包含特殊的檔案嗎?  
 另一個重要的設計決策就是您的專案結構是否使用特殊的檔案。  特殊的檔案是隱藏的檔案為基礎的檔案，會顯示在方案總管中，然後在 \[簽入及簽出對話方塊。  如果您使用特殊的檔案，請遵循以下方針：  
  
1.  不會與專案的根節點關聯很特殊的檔案 — 也就是與專案檔案本身。  您的專案檔必須是單一檔案。  
  
2.  當特殊的檔案會加入、 移除或重新命名專案中的適當<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>必須引發事件，設定旗標，表示檔案是特殊的檔案。  這些事件由呼叫適當的專案來回應環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>方法。  
  
3.  當您的專案或編輯器呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>檔案，該檔案相關聯的特殊檔案不會自動簽出。  在特殊的檔案一起傳遞的父檔案。  環境將會偵測到傳入的所有檔案之間的關係，並適當地隱藏 \[簽出使用者介面中特殊的檔案。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [支援的原始檔控制](../../extensibility/internals/supporting-source-control.md)