---
title: "如何：指定 ClickOnce 應用程式的開始功能表名稱 | Microsoft Docs"
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
  - "ClickOnce 部署, 開始功能表名稱"
  - "開始功能表名稱"
  - "開始功能表資源名稱"
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：指定 ClickOnce 應用程式的開始功能表名稱
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式安裝成線上和離線使用時，會有項目加入至 \[**開始**\] 功能表和 \[**新增或移除程式**\] 清單。  依據預設，顯示名稱與應用程式組件名稱相同，但您可以在 \[**發行選項**\] 對話方塊中設定 \[**產品名稱**\]，藉此變更顯示名稱。  
  
 \[**產品名稱**\] 將顯示在 publish.htm 頁面上；如果是已安裝的離線應用程式，會顯示 \[**開始**\] 功能表中的項目名稱，而且該名稱也會是 \[**新增或移除程式**\] 中所顯示的名稱。  
  
 \[**發行者名稱**\] 將出現在 \[**產品名稱**\] 上方的 publish.htm 頁面上，如果是已安裝的離線應用程式，則也會顯示內含 \[**開始**\] 功能表中之應用程式圖示的資料夾名稱。  
  
 您可以在 \[**發行選項**\] 對話方塊中設定 \[**產品名稱**\] 和 \[**發行者名稱**\] 屬性，這些屬性也可以從 \[**專案設計工具**\] 的 \[**發行**\] 頁面上取得。  
  
### 若要指定開始功能表名稱  
  
1.  在 \[**方案總管**\] 中選取專案之後，請在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  
  
2.  按一下 \[**發行**\] 索引標籤。  
  
3.  按一下 \[**選項**\] 按鈕，開啟 \[**發行選項**\] 對話方塊。  
  
4.  按一下 \[**描述**\]。  
  
5.  在 \[**發行選項**\] 對話方塊中，輸入要顯示在 \[**產品名稱**\] 中的名稱。  
  
6.  您也可以選擇性地在 \[**發行者名稱**\] 中輸入發行者名稱。  
  
## 請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)