---
title: "如何：將 Windows Form 控制項繫結至資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "資料 [Windows Form], 顯示"
  - "資料來源, 顯示"
  - "顯示資料, Windows Form 控制項"
  - "Windows Form, 顯示資料"
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 28
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：將 Windows Form 控制項繫結至資料
從[資料來源視窗](../Topic/Data%20Sources%20Window.md)拖曳物件，將資料繫結至 Windows Form 控制項。  從 \[**資料來源**\] 視窗中拖曳項目之前，您可以針對個別控制項將資料表的控制項型別設為 **Details**，或針對 <xref:System.Windows.Forms.DataGridView> 將其設為 **DataGridView**。  如需詳細資訊，請參閱 [設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)。  
  
 如果應用程式需要的控制項無法從 \[**資料來源**\] 視窗內，您可以加入控制項。  如需詳細資訊，請參閱 [將自訂控制項加入 \[資料來源\] 視窗](../Topic/Add%20custom%20controls%20to%20the%20Data%20Sources%20window.md)。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 在個別控制項中顯示整個資料表  
 您可以從 \[**資料來源**\] 視窗將資料表 \(若使用物件資料來源，則為表示集合的節點\) 拖曳至 Windows 應用程式的表單中，在個別控制項中顯示整個資料表。  
  
#### 顯示整個資料表  
  
1.  開啟 \[**資料來源**\] 視窗。  如需詳細資訊，請參閱 [如何：開啟資料來源視窗](../data-tools/how-to-open-the-data-sources-window.md)。  
  
    > [!NOTE]
    >  如果 \[**資料來源**\] 視窗是空的，請加入資料來源。  如需詳細資訊，請參閱[資料來源概觀](../data-tools/add-new-data-sources.md)。  
  
2.  在 \[**Windows Form 設計工具**\] 中開啟表單。  
  
3.  在 \[**資料來源**\] 視窗中選取資料表、按下拉式箭號，然後選取 \[**詳細資料**\]。  
  
4.  從 \[**資料來源**\] 視窗將資料表拖曳至表單。  
  
     在表單上隨即建立各資料行 \(或屬性\) 的個別資料繫結控制項，隨附適當標題的標籤控制項。  
  
## 在個別控制項中顯示選取的資料行  
 從 \[**資料來源**\] 視窗將個別資料行 \(若使用物件資料來源，則為屬性\) 拖曳至 Windows 應用程式的表單中，在個別控制項中顯示個別資料行。  
  
#### 顯示選取的資料行  
  
1.  開啟 \[**資料來源**\] 視窗。  如需詳細資訊，請參閱 [如何：開啟資料來源視窗](../data-tools/how-to-open-the-data-sources-window.md)。  
  
    > [!NOTE]
    >  如果 \[**資料來源**\] 視窗是空的，請加入資料來源。  如需詳細資訊，請參閱[資料來源概觀](../data-tools/add-new-data-sources.md)。  
  
2.  展開資料表，顯示個別資料行。  
  
    > [!TIP]
    >  若要設定為各資料行建立的控制項，請在 \[**資料來源**\] 視窗中選取資料行、按下拉式箭號，然後從可用控制項清單中選取控制項。  如需詳細資訊，請參閱 [設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)。  
  
3.  在 \[**Windows Form 設計工具**\] 中開啟表單。  
  
4.  從 \[**資料來源**\] 視窗將所要的資料行拖曳至表單。  
  
     每拖曳一個資料行或屬性，表單上就會建立一個資料繫結控制項，並附上適當標題的標籤控制項。  
  
 您也可以從 \[**資料來源**\] 視窗拖曳項目至現有控制項 \(已經在表單上的控制項\)，將控制項繫結至資料。  已經繫結到資料的控制項會將其資料繫結重設為最新拖曳到其上的項目。  
  
> [!NOTE]
>  控制項必須能夠顯示從 \[**資料來源**\] 視窗拖曳項目到其上的基礎資料型別，才能成為有效的置放目標。  例如，將具有 <xref:System.DateTime> 資料型別的項目拖曳到 <xref:System.Windows.Forms.CheckBox> 上是無效的動作，因為 <xref:System.Windows.Forms.CheckBox> 無法顯示日期。  
  
#### 若要將現有控制項繫結至資料  
  
1.  開啟 \[**資料來源**\] 視窗。  如需詳細資訊，請參閱 [如何：開啟資料來源視窗](../data-tools/how-to-open-the-data-sources-window.md)。  
  
2.  在 [Windows Forms Designer](http://msdn.microsoft.com/zh-tw/3c3d61f8-f36c-4d41-b9c3-398376fabb15)中開啟表單。  
  
3.  在 \[**資料來源**\] 視窗中展開資料表或物件，以顯示其個別資料行或屬性。  
  
4.  從 \[**資料來源**\] 視窗將所要的項目拖曳至現有控制項。  
  
     控制項現在已經繫結至該選取的項目。  
  
## 在 DataGridView 控制項中顯示資料  
  
#### 若要在新的 Windows Form DataGridView 控制項中顯示資料  
  
1.  開啟 \[**資料來源**\] 視窗。  如需詳細資訊，請參閱 [如何：開啟資料來源視窗](../data-tools/how-to-open-the-data-sources-window.md)。  
  
    > [!NOTE]
    >  如果 \[**資料來源**\] 視窗是空的，請加入資料來源。  如需詳細資訊，請參閱[資料來源概觀](../data-tools/add-new-data-sources.md)。  
  
2.  在 \[**Windows Form 設計工具**\] 中開啟表單。  
  
3.  在 \[**資料來源**\] 視窗中選取資料表，並按一下下拉箭號，然後選取 \[**DataGridView**\]。  
  
4.  從 \[**資料來源**\] 視窗將資料表拖曳至表單。  
  
     <xref:System.Windows.Forms.DataGridView> 控制項以及用於巡覽資料錄的工具區域 \(<xref:System.Windows.Forms.BindingNavigator>\) 會出現在表單上。  [DataSet](../data-tools/dataset-tools-in-visual-studio.md)、[TableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator> 則會出現在元件匣中。  
  
#### 若要在現有的 Windows Form DataGridView 控制項中顯示資料  
  
1.  開啟 \[**資料來源**\] 視窗。  如需詳細資訊，請參閱 [如何：開啟資料來源視窗](../data-tools/how-to-open-the-data-sources-window.md)。  
  
    > [!NOTE]
    >  如果 \[**資料來源**\] 視窗是空的，請加入資料來源。  如需詳細資訊，請參閱[資料來源概觀](../data-tools/add-new-data-sources.md)。  
  
2.  在 \[**Windows Form 設計工具**\] 中開啟表單。  
  
3.  在 \[**資料來源**\] 視窗中選取資料表，並按一下下拉箭號，然後選取 \[**DataGridView**\]。  
  
4.  從 \[**資料來源**\] 視窗將資料表拖曳至表單上的 <xref:System.Windows.Forms.DataGridView>。  
  
     <xref:System.Windows.Forms.DataGridView> 控制項現在會繫結到您將它拖曳到其上的資料表。  [DataSet](../data-tools/dataset-tools-in-visual-studio.md)、[TableAdapter](../data-tools/tableadapter-overview.md) 和 <xref:System.Windows.Forms.BindingSource> 則會出現在元件匣中。  
  
## 請參閱  
 [逐步解說：顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)   
 [BindingSource 元件概觀](../Topic/BindingSource%20Component%20Overview.md)   
 [BindingNavigator 控制項概觀](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)   
 [用來在 Visual Studio 中使用資料來源的工具](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)