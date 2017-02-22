---
title: "如何：啟用 ClickOnce 安全性設定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
  - "ClickOnce 部署, 安全性設定"
  - "安全性 [Visual Studio], ClickOnce 應用程式"
  - "安全性設定, ClickOnce 部署"
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：啟用 ClickOnce 安全性設定
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

必須啟用 ClickOnce 應用程式的程式碼存取安全性，才能發行應用程式。  當您使用 \[發行精靈\] 發行應用程式時，會自動完成這個動作。  
  
 在某些情況下，建置或偵錯應用程式時，啟用程式碼存取安全性可能會影響效能；在這些情況下，您可能要暫時停用安全性設定。  
  
 在 \[**專案設計工具**\] 的 \[**安全性**\] 頁面中，可以啟用或停用 ClickOnce 安全性設定。  
  
### 若要啟用 ClickOnce 安全性設定  
  
1.  在 \[**方案總管**\] 中選取專案之後，請在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
2.  按一下 \[**安全性**\] 索引標籤。  
  
3.  選取 \[**啟用 ClickOnce 安全性設定**\] 核取方塊。  
  
     在 \[安全性\] 頁面中，您現在可以自訂應用程式的安全性設定。  
  
    > [!NOTE]
    >  每次使用 \[**發行精靈**\] 發行應用程式時，都會自動選取這個核取方塊。  
  
### 若要停用 ClickOnce 安全性設定  
  
1.  在 \[**方案總管**\] 中選取專案之後，請在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
2.  按一下 \[**安全性**\] 索引標籤。  
  
3.  清除 \[**啟用 ClickOnce 安全性設定**\] 核取方塊。  
  
     將會以完全信任的安全性設定，執行應用程式；將忽略 \[**安全性**\] 頁面中的任何設定。  
  
    > [!NOTE]
    >  每當使用 \[發行精靈\] 發行應用程式時，便會選取此核取方塊；您必須在每次成功發行之後再次清除它。  
  
## 請參閱  
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)