---
title: "原始檔控制執行階段詳細資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原始檔控制 [Visual Studio SDK]，執行階段詳細資料"
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 原始檔控制執行階段詳細資料
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

專案會加入至原始檔控制中，當使用者會加入專案中的檔案加入原始檔控制，或是透過自動化控制站，例如精靈。  在專案並未指定為其本身代表這已受到原始檔控制。 它支援原始檔控制，但是必須以手動方式新增至它。  
  
## 註冊與原始檔控制套件  
 當您的專案中的檔案加入至原始檔控制時，環境就會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> ，提供您四個用作 cookie 的原始檔控制系統的不透明字串。  將這些字串儲存在您的專案檔中。  這些字串應該傳遞至原始檔控制虛設常式 \(管理原始檔控制套件的 Visual Studio 元件\) 啟動專案類型時藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>。  這又會載入適當的原始檔控制套件，並傳送呼叫至它的實作的`IVsSccManager2::RegisterSccProject`。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [支援的原始檔控制](../../extensibility/internals/supporting-source-control.md)