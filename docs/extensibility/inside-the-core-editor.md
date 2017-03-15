---
title: "核心編輯器內 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版的核心編輯器"
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# 核心編輯器內
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器是一組的數個元件可讓您修改與查詢文字資訊。  如果您將使用舊版 API 自訂核心編輯器，您可以繼續使用這些自訂功能將被路由到編輯器介面卡。  建議，不過，您適應您的自訂設定至新的編輯器 API。  
  
 下列的區域是核心編輯器的一些重要特性：  
  
-   文字緩衝區  
  
-   文字檢視  
  
-   程式碼\] 視窗  
  
-   文字標記  
  
-   文字管理員  
  
-   與語言服務整合  
  
## 在本節中  
 [使用舊版 API 執行個體化核心編輯器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 提供逐步告訴您如何使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>若要建立執行個體的核心編輯器。  
  
 [使用舊版 API 存取文字緩衝區](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 討論核心編輯器\] 中的文字緩衝區的角色，說明用來存取緩衝區，並提供一份文字緩衝區物件所實作的介面的相關的系統<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>。  
  
 [在舊版 API 中的文字緩衝區事件](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 提供一份使用文字緩衝區事件的告知介面。  
  
 [如何: 使用舊版 API 文字緩衝區事件註冊](../Topic/How%20to:%20Register%20for%20Text%20Buffer%20Events%20with%20the%20Legacy%20API.md)  
 說明如何將文字緩衝區事件的通知。  
  
 [使用文字管理員監控全域設定](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 討論文字管理員使用的核心編輯器元件與共用通用的喜好設定資訊的方式，以及如何接收文字管理員事件的告知。  
  
 [使用舊版 API 存取 Text 檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 描述核心編輯器\] 中的 \[文字\] 檢視的角色，並列出所實作的介面<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>物件。  
  
 [使用舊版 API 的自訂程式碼視窗](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 提供程式碼\] 視窗用來括住文字檢視、 將告訴您如何在程式碼視窗管理員用來提供裝飾的程式碼\] 視窗中，並提供新檢視的通知的方式的相關資訊。  
  
 [使用舊版 API 來變更檢視設定](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 提供有關如何強制檢視設定，以及如何移除強制的設定的逐步指示。  
  
 [語言服務及核心編輯器](../extensibility/language-services-and-the-core-editor.md)  
 描述控制項的程式碼裝飾語言服務的執行個體化。  
  
## 相關章節  
 [逐步解說: 建立核心編輯器和登錄編輯器的檔案類型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 提供關於如何啟動核心編輯器從 managed 程式碼的逐步指示。  
  
 [下拉式清單列](../extensibility/drop-down-bar.md)  
 討論如何在程式碼\] 視窗中使用下拉式選單\] 列，並告訴您，當您實作下拉式列時所使用的介面。  
  
 [使用舊版 API 中的文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)  
 說明文字的標記以及它們在核心編輯器的使用方式的概念，並列出用來存取和管理文字標記的介面。  
  
 [如何: 新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)  
 提供有關如何建立文字標記，以及如何將自訂命令新增到快顯功能表的逐步指示。  
  
 [如何: 建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)  
 提供有關如何建立自訂的文字標記，以及如何提供標記型別，以服務的逐步指示。