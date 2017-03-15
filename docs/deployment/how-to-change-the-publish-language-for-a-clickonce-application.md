---
title: "如何：變更 ClickOnce 應用程式的發行語言 | Microsoft Docs"
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
  - "ClickOnce 部署, 變更發行語言"
  - "發行語言屬性"
  - "發行, ClickOnce"
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：變更 ClickOnce 應用程式的發行語言
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

發行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，在安裝期間顯示的使用者介面預設為開發電腦的語言和文化特性 \(Culture\)。  如果您要發行當地語系化的應用程式，您需要指定與當地語系化版本相符的語言和文化特性。  這是由專案的 `Publish language` 屬性決定的。  
  
 在 \[**發行選項**\] 對話方塊中可以設定 `Publish language` 屬性 \(從 \[**專案設計工具**\] 的 \[**發行**\] 頁存取\)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要變更發行語言  
  
1.  在 \[**方案總管**\] 中選取專案之後，請在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
2.  按一下 \[**發行**\] 索引標籤。  
  
3.  按一下 \[**選項**\] 按鈕，開啟 \[**發行選項**\] 對話方塊。  
  
4.  按一下 \[**描述**\]。  
  
5.  在 \[**發行選項**\] 對話方塊中，從 \[**發行語言**\] 下拉式清單中選取語言和文化特性，再按 \[**確定**\]。  
  
## 請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)