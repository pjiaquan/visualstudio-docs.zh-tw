---
title: "如何：利用 WPF 應用程式建立查閱資料表 | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "資料 [WPF], 顯示"
  - "資料繫結, WPF"
  - "顯示資料, WPF"
  - "WPF [WPF], 資料"
  - "WPF 資料繫結 [Visual Studio]"
  - "WPF Designer, 資料繫結"
  - "WPF, Visual Studio 中的資料繫結"
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：利用 WPF 應用程式建立查閱資料表
您可以建立查閱資料表，方法是從 \[**資料來源**\] 視窗將父資料表或物件的主節點拖曳至已繫結至相關子資料表之資料行或屬性的控制項。  「*查閱資料表*」\(Lookup Table\) 一詞 \(有時候稱為「*查閱繫結*」\(Lookup Binding\)\) 描述根據某個資料表中的外部索引鍵欄位值，顯示另一個資料表之資訊的控制項。  
  
 例如，請考慮銷售資料庫中的 `Orders` 資料表。  `Orders` 資料表中的每筆記錄都包含 `CustomerID`，表示下訂單的客戶。  `CustomerID` 是外部索引鍵，它會指向 `Customers` 資料表中的客戶記錄。  從 `Orders` 資料表顯示訂單清單時，您可能要顯示的是實際客戶名稱，而不是 `CustomerID`。  因為客戶名稱是在 `Customers` 資料表中，您必須建立查閱資料表，才能顯示客戶名稱。  查閱資料表使用 `Orders` 記錄中的 `CustomerID` 值，以巡覽關聯性並傳回使用者易記的客戶名稱。  
  
### 若要建立查閱資料表  
  
1.  將下列其中一種具有相關資料的資料來源加入專案中：  
  
    -   資料集或實體資料模型。  如需詳細資訊，請參閱 [如何：連接至資料庫中的資料](../data-tools/how-to-connect-to-data-in-a-database.md)。  
  
    -   WCF 資料服務、WCF 服務或 Web 服務。  如需詳細資訊，請參閱 [如何：連接至服務中的資料](../data-tools/how-to-connect-to-data-in-a-service.md)。  
  
    -   物件。  如需詳細資訊，請參閱 [如何：連接至物件中的資料](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)。  
  
    > [!NOTE]
    >  在建立查閱資料表之前，兩個相關資料表或物件必須存在，當做專案的資料來源。  
  
2.  開啟 \[**WPF 設計工具**\]，並確定設計工具包含的容器是 \[**資料來源**\] 視窗中項目的有效置放目標。  
  
     如需有效置放目標的詳細資訊，請參閱[將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
3.  在 \[**資料**\] 功能表上按一下 \[**顯示資料來源**\]，以開啟 \[**資料來源**\] 視窗。  
  
4.  展開 \[**資料來源**\] 視窗中的節點，直到您看見父資料表或物件和其相關子資料表或物件為止。  
  
    > [!NOTE]
    >  相關子資料表或物件是指在父資料表或物件底下顯示為可展開子節點的節點。  
  
5.  按一下子節點的下拉式功能表，然後選取 \[**詳細資料**\]。  
  
6.  展開子節點。  
  
7.  在子節點底下，按一下將子資料和父資料產生關聯之項目的下拉式功能表 \(在上述範例中，這是 \[**CustomerID**\] 節點\)。  選取下列其中一種支援查閱繫結的控制項：  
  
    -   **ComboBox**  
  
    -   **ListBox**  
  
    -   **ListView**  
  
        > [!NOTE]
        >  如果 \[**ListBox**\] 或 \[**ListView**\] 控制項並未出現在清單中，您可以將這些控制項加入至清單。  如需詳細資訊，請參閱 [設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)。  
  
    -   任何衍生自 <xref:System.Windows.Controls.Primitives.Selector> 的自訂控制項。  
  
        > [!NOTE]
        >  如需如何將自訂控制項加入至可供選取做為 \[**資料來源**\] 視窗中項目的控制項清單的詳細資訊，請參閱 [將自訂控制項加入 \[資料來源\] 視窗](../Topic/Add%20custom%20controls%20to%20the%20Data%20Sources%20window.md)。  
  
8.  從 \[**資料來源**\] 視窗將子節點拖曳至 WPF 設計工具中的容器 \(在上述範例中，子節點是 \[**Orders**\] 節點\)。  
  
     Visual Studio 會針對您拖曳的每個項目產生建立新資料繫結控制項的 XAML。  XAML 也會將子資料表或物件的新 <xref:System.Windows.Data.CollectionViewSource> 加入置放目標的資源中。  對於某些資料來源，Visual Studio 也會產生可將資料載入資料表或物件中的程式碼。  如需詳細資訊，請參閱[將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
9. 從 \[**資料來源**\] 視窗將父節點拖曳至您先前建立的查閱繫結控制項 \(在上述範例中，父節點是 \[**Customers**\] 節點\)。  
  
     Visual Studio 會設定此控制項上的一些屬性，以設定查閱繫結。  下表列出 Visual Studio 修改的屬性。  必要時，您可以在 XAML 或 \[**屬性**\] 視窗中變更這些屬性。  
  
    |屬性|設定說明|  
    |--------|----------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|這個屬性指定用來取得控制項中顯示之資料的集合或繫結。  Visual Studio 會將這個屬性設定為您拖曳至控制項之父資料的 <xref:System.Windows.Data.CollectionViewSource>。|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|這個屬性指定控制項中顯示之資料項目的路徑。  Visual Studio 會將這個屬性設定為主索引鍵之後，第一個擁有字串資料型別的資料行或屬性。<br /><br /> 如果您想要在父資料中顯示不同的資料行或屬性，請將這個屬性變更為不同屬性的路徑。|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio 會將這個屬性繫結至您拖曳至設計工具中子資料的資料行或屬性。  這是父資料的外部索引鍵。|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio 會將這個屬性設定為子資料中做為父資料外部索引鍵之資料行或屬性的路徑。|  
  
## 請參閱  
 [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [如何：將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [如何：在 WPF 應用程式中顯示相關的資料](../data-tools/display-related-data-in-wpf-applications.md)   
 [逐步解說：顯示 WPF 應用程式中的相關資料](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)