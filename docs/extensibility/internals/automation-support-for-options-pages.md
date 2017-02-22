---
title: "在選項頁面的自動化支援 | Microsoft Docs"
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
  - "工具選項頁 [Visual Studio SDK]，自動化支援"
  - "自動化 [Visual Studio SDK]，建立工具選項頁"
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# 在選項頁面的自動化支援
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackages 可以提供自訂 **選項** 對話方塊來 **工具** 功能表 \(工具選項頁面\) 中的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，可以讓它們可自動化模型。  
  
## 工具選項頁  
 若要建立 **工具選項** \] 頁面上，VSPackage 必須提供傳回透過 VSPackage 實作的環境的使用者控制項實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 方法 \(或 managed 程式碼 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 方法\)。  
  
 它是選擇性的但強烈建議，以允許存取此自動化模型的新頁面。 您可以透過下列步驟:  
  
1.  擴充 <xref:EnvDTE._DTE.Properties%2A> 物件，用來實作 IDispatch 衍生的物件。  
  
2.  傳回的實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 方法 \(或 managed 程式碼的 <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> 方法\) 至 IDispatch 衍生物件。  
  
3.  當 automation 取用者呼叫 <xref:EnvDTE._DTE.Properties%2A> 方法在自訂 **選項** 屬性頁的環境使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 方法來取得自訂 **工具選項** 網頁的自動化實作。  
  
4.  VSPackage 的 automation 物件則用來提供每個 <xref:EnvDTE.Property> 傳回 <xref:EnvDTE._DTE.Properties%2A>。  
  
 如需實作自訂的工具選項\] 頁面的範例，請參閱 [VSSDK 範例](../../misc/vssdk-samples.md)。  
  
## 請參閱  
 [公開專案物件](../../extensibility/internals/exposing-project-objects.md)