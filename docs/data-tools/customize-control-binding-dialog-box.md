---
title: "自訂控制項繫結對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.datauicustomization"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "自訂控制項繫結對話方塊"
ms.assetid: abcc0be3-a18e-4f47-b354-d6b0c618e087
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 自訂控制項繫結對話方塊
使用 \[**自訂控制繫結**\] 對話方塊，可以指定哪些控制項可用於[資料來源視窗](../Topic/Data%20Sources%20Window.md)中的項目。  
  
 在 \[**資料來源**\] 視窗中，每個項目都有可繫結的關聯控制項清單。  每個項目可用的控制項由項目的資料型別判斷。  在這個對話方塊中，每個資料型別都已定義了一份有效的關聯控制項的清單，包括預設控制項在內。  
  
 將項目拖曳至設計介面以建立資料繫結控制項之前，您可以選取要建立哪個控制項。  如果您將 \[**資料來源**\] 視窗中的項目拖曳至設計介面上但是未選取控制項，則會將所選取項目之資料型別的預設控制項加入至設計介面。  
  
 如需如何使用這個對話方塊自訂 \[**資料來源**\] 視窗中項目的控制項清單的詳細資訊，請參閱 [將自訂控制項加入 \[資料來源\] 視窗](../Topic/Add%20custom%20controls%20to%20the%20Data%20Sources%20window.md)。  
  
## UIElement 清單  
 **資料型別**  
 顯示可以與控制項產生關聯的型別清單：  
  
-   資料表、實體和物件會表示為 \[**清單**\] 型別。  
  
-   實體和物件的資料行或公用屬性會表示為基礎資料存放區中資料行或屬性的實際資料型別。  
  
-   具有使用者定義之圖案的物件會表示為 \[**其他**\]。  例如，如果應用程式有自訂控制項，而這個控制項顯示某個物件中一個以上的屬性資料時，請針對控制項選取 \[**其他**\] 資料型別。  
  
 **關聯的控制項**  
 顯示可以與特定資料型別產生關聯的控制項清單。  如果您想要將特定控制項與 \[**資料型別**\] 清單中選取的資料型別產生關聯，請選取對應的核取方塊。  清除核取方塊可移除關聯。  選取的控制項會出現在關聯資料型別之項目的 \[**資料來源**\] 視窗所顯示的捷徑功能表中。  
  
 如果要將控制項加入至清單，可以將有數個資料繫結屬性之一的控制項加入至 \[**工具箱**\]。  如需詳細資訊，請參閱 [將自訂控制項加入 \[資料來源\] 視窗](../Topic/Add%20custom%20controls%20to%20the%20Data%20Sources%20window.md)。  
  
 **設定預設值**  
 指派選取控制項類型做為選取資料型別之項目的預設值。  預設控制項會在項目的 \[**資料來源**\] 視窗所顯示的捷徑功能表中，顯示為第一個選取項目。  資料型別只可以指派一種控制項類型做為預設值。  
  
 **清除預設值**  
 移除指派給選取資料型別的預設控制項。  如果選取的資料型別沒有預設值，則會顯示 \[**無**\]，做為關聯型別之項目的 \[**資料來源**\] 視窗所顯示的捷徑功能表中第一個選取項目。  
  
## 請參閱  
 [資料來源視窗](../Topic/Data%20Sources%20Window.md)   
 [資料來源概觀](../data-tools/add-new-data-sources.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [將自訂控制項加入 \[資料來源\] 視窗](../Topic/Add%20custom%20controls%20to%20the%20Data%20Sources%20window.md)   
 [設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)