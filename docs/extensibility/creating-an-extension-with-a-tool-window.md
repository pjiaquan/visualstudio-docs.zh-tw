---
title: "建立擴充功能與工具視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# 建立擴充功能與工具視窗
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在此程序，您會了解如何使用 VSIX 專案範本和 **自訂工具視窗** 項目範本建立的擴充功能與工具視窗。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
### 建立工具視窗  
  
1.  建立 VSIX 專案，名為 **FirstWindow**。 您可以找到 VSIX 專案範本，在 **新的專案** 下的對話方塊 **Visual C\# \/ 擴充性**。  
  
2.  專案開啟時，加入名為工具視窗中的項目範本 **FirstWindow**。 在 **方案總管\] 中**, ，以滑鼠右鍵按一下專案節點，然後選取 **加入 \/ 新的項目**。 在 **加入新項目** \] 對話方塊中，移至 **Visual C\# \/ 擴充性** ，然後選取 **自訂工具視窗**。 在 **名稱** 欄位底部的 \[\] 視窗中，變更工具視窗中的檔案名稱，以 **FirstWindow.cs**。  
  
3.  建置此專案並開始偵錯。  
  
     Visual Studio 的實驗執行個體隨即出現。 如需詳細的實驗執行個體的詳細資訊，請參閱 [實驗執行個體](../extensibility/the-experimental-instance.md)。  
  
4.  在實驗執行個體中，移至 **檢視 \/ 其他視窗**。  
  
     您應該會看到的功能表項目 **FirstWindow**。 按一下此按鈕。  
  
     您應該會看到工具視窗的標題 **FirstWindow** 按鈕說 **Click Me\!。**