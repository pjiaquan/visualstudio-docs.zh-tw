---
title: "使用編輯器項目範本建立擴充功能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，新的擴充功能"
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# 使用編輯器項目範本建立擴充功能
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用 Visual Studio SDK 來建立將加入編輯器的分類器、 裝飾和邊界的基本編輯器延伸模組中包含的項目範本。 編輯器項目範本是適用於 Visual C\# 或 Visual Basic VSIX 專案。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 建立分類器擴充功能  
 編輯器分類項目範本建立適當的文字的色彩編輯器分類器 \(在此情況下，所有項目\) 中的任何文字檔。  
  
1.  在 **新的專案** 對話方塊方塊中，展開 **Visual C\#** 或 **Visual Basic** 然後按一下 \[ **擴充性**。 在 **範本** 窗格中，選取 **VSIX 專案**。 在 **名稱** 方塊中，輸入 `TestClassifier`。 按一下 \[**確定**\]。  
  
2.  在 **方案總管\] 中**, ，以滑鼠右鍵按一下專案節點，然後選取 **加入 \/ 新的項目**。 移至 Visual C\# **擴充性** 節點，然後選取 **編輯器分類**。 保留預設的檔案名稱 \(EditorClassifier1.cs\)。  
  
3.  有三個程式碼檔案，如下:  
  
    -   包含 EditorClassifier1.cs `EditorClassifier1` 類別。  
  
    -   包含 EditorClassifier1ClassificationDefinition.cs `OEditorClassifier1ClassificationDefinition` 類別。  
  
    -   包含 EditorClassifier1Format.cs `EditorClassifier1Format`  類別。  
  
    -   包含 EditorClassifier1Provider.cs `EditorClassifier1Provider` 類別。  
  
4.  建置此專案並開始偵錯。 Visual Studio 的實驗執行個體隨即出現。  
  
     如果您開啟文字檔時，所有的文字會加上底線針對紫色的背景。  
  
## 建立文字相對於裝飾擴充功能  
 編輯器文字裝飾範本建立裝飾的文字字元的所有執行個體相對於文字裝飾 'a' 以使用具有紅色外框和藍色背景的方塊。 它是文字相對於因為方塊永遠覆疊 'a' 字元，即使它們是移動或重新格式化。  
  
1.  在 **新的專案** 對話方塊方塊中，展開 **Visual C\#** 或 **Visual Basic** 然後按一下 \[ **擴充性**。 在 **範本** 窗格中，選取 **VSIX 專案**。 在 **名稱** 方塊中，輸入 `TestAdornment`。 按一下 \[**確定**\]。  
  
2.  在 **方案總管\] 中**, ，以滑鼠右鍵按一下專案節點，然後選取 **加入 \/ 新的項目**。 移至 Visual C\# **擴充性** 節點，然後選取 **編輯器文字裝飾**。 保留預設的檔案名稱 \(TextAdornment1.cs\/vb\)。  
  
3.  有兩個程式碼檔案，如下:  
  
    -   包含 TextAdornment1.cs `TextAdornment1` 類別。  
  
    -   包含 extAdornment1TextViewCreationListener.cs `TextAdornment1TextViewCreationListener` 類別。  
  
4.  建置此專案並開始偵錯。 實驗執行個體隨即出現。 如果您開啟文字檔案，在文字中的所有 'a' 字元加上紅框以藍色背景。  
  
## 建立檢視區相對裝飾擴充功能  
 編輯器檢視區裝飾範本會建立會新增至檢視區的右上角的紅色外框紫色方塊相對於檢視區裝飾。  
  
> [!NOTE]
>  *檢視區* 是目前顯示的文字檢視的區域。  
  
#### 若要使用編輯器檢視區裝飾範本建立的檢視區裝飾延伸模組  
  
1.  在 **新的專案** 對話方塊方塊中，展開 **Visual C\#** 或 **Visual Basic** 然後按一下 \[ **擴充性**。 在 **範本** 窗格中，選取 **VSIX 專案**。 在 **名稱** 方塊中，輸入 `ViewportAdornment`。 按一下 \[**確定**\]。  
  
2.  在 **方案總管\] 中**, ，以滑鼠右鍵按一下專案節點，然後選取 **加入 \/ 新的項目**。 移至 Visual C\# **擴充性** 節點，然後選取 **編輯器檢視區裝飾**。 保留預設的檔案名稱 \(ViewportAdornment1.cs\/vb\)。  
  
3.  有兩個程式碼檔案，如下:  
  
    -   包含 ViewportAdornment1.cs `ViewportAdornment1` 類別。  
  
    -   包含 ViewportAdornment1TextViewCreationListener.cs `ViewportAdornment1TextViewCreationListener` 類別  
  
4.  建置此專案並開始偵錯。 實驗執行個體隨即出現。 如果您建立新的文字檔，都有紅色外框的紫色方塊會顯示在檢視區的右上角。  
  
## 建立邊界擴充功能  
 編輯器邊界範本會建立與文字"Hello world\!"會出現綠色邊界 水平捲軸下方。  
  
#### 若要使用編輯器邊界範本建立的邊界延伸模組  
  
1.  在 **新的專案** 對話方塊方塊中，展開 **Visual C\#** 或 **Visual Basic** 然後按一下 \[ **擴充性**。 在 **範本** 窗格中，選取 **VSIX 專案**。 在 **名稱** 方塊中，輸入 `MarginExtension`。 按一下 \[**確定**\]。  
  
2.  在 **方案總管\] 中**, ，以滑鼠右鍵按一下專案節點，然後選取 **加入 \/ 新的項目**。 移至 Visual C\# **擴充性** 節點，然後選取 **編輯器檢視區裝飾**。 保留預設的檔案名稱 \(EditorMargin1.cs\/vb\)。  
  
3.  有兩個程式碼檔案，如下:  
  
    -   包含 EditorMargin1.cs `EditorMargin1` 類別。  
  
    -   包含 EditorMargin1Factory.cs `EditorMargin1Factory` 類別。  
  
4.  建置此專案，並開始偵錯。 實驗執行個體隨即出現。 如果您開啟文字檔，水平捲軸下方顯示的文字"Hello EditorMargin1 」，綠色邊界。  
  
## 請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)