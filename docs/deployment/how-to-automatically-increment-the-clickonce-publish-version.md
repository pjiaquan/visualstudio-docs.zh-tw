---
title: "如何：自動累加 ClickOnce 的發行版本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 部署, 自動遞增發行版本"
  - "部署應用程式 [ClickOnce], 自動遞增發行版本"
  - "發行版本屬性, 遞增"
  - "發行, ClickOnce"
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：自動累加 ClickOnce 的發行版本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

發行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，變更 `Publish Version` 屬性會造成應用程式發行為更新版本。  每次您發行應用程式時，Visual Studio 預設會自動累加 `Publish Version` 的 `Revision` 號碼。  
  
 在 \[**專案設計工具**\] 的 \[**發行**\] 頁上，可以停用這個行為。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要停用自動累加發行版本  
  
1.  在 \[**方案總管**\] 中選取專案之後，請在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
2.  按一下 \[**發行**\] 索引標籤。  
  
3.  在 \[**發行版本**\] 區段中，清除 \[**隨著每次發行自動遞增修訂**\] 核取方塊。  
  
## 請參閱  
 [如何：設定 ClickOnce 發行版本](../Topic/How%20to:%20Set%20the%20ClickOnce%20Publish%20Version.md)   
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)