---
title: "如何：在混合模式偵錯 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "偵錯 [Visual Studio], 混合模式"
  - "偵錯 DLL"
  - "混合模式偵錯"
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：在混合模式偵錯
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

下列程序描述如何同時偵錯 Managed 和原生程式碼，這也稱為混合模式偵錯。  依照 DLL 或應用程式是否以機器碼撰寫而定，會有下列兩種情況：  
  
-   呼叫 DLL 的呼叫應用程式是以機器碼撰寫。  在這個情況中，您的 DLL 是 Managed，而且 Managed 和原生偵錯工具都必須啟用，才能為兩種程式碼偵錯。  您可以在 \[**\<專案\> 屬性頁**\] 對話方塊中檢查這一點。  不同的做法是取決於您是由 DLL 專案啟動偵錯，或者由呼叫應用程式專案啟動偵錯。  
  
-   呼叫 DLL 的呼叫應用程式是以 Managed 程式碼撰寫，而您的 DLL 是以機器碼撰寫。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選取 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要啟用混合模式偵錯  
  
1.  在 \[**方案總管**\] 中選取專案。  
  
2.  在 \[**檢視**\] 功能表上按一下 \[**屬性頁**\]。  
  
3.  在 \[**\<專案\> 屬性頁**\] 對話方塊中，展開 \[**組態屬性**\] 節點，然後選取 \[**偵錯**\]。  
  
4.  將 \[**偵錯工具類型**\] 設定為 \[**混合**\] 或 \[**自動**\]。  
  
## 請參閱  
 [如何：從 DLL 專案偵錯](../debugger/how-to-debug-from-a-dll-project.md)