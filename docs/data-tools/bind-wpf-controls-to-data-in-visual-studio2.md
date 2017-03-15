---
title: "如何：將 WPF 控制項繫結至 Visual Studio 中的資料 | Microsoft Docs"
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
  - "資料 [WPF], 顯示"
  - "資料繫結, WPF"
  - "顯示資料, WPF"
  - "WPF [WPF], 資料"
  - "WPF 資料繫結 [Visual Studio]"
  - "WPF Designer, 資料繫結"
  - "WPF, Visual Studio 中的資料繫結"
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 26
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：將 WPF 控制項繫結至 Visual Studio 中的資料
您可以使用 \[資料來源\] 視窗，建立資料繫結 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] 控制項。  首先，將資料來源加入至 \[資料來源\] 視窗。  然後將項目從 \[資料來源\] 視窗拖曳至 **WPF 設計工具**。  
  
##  <a name="adding"></a> 將資料來源加入至資料來源視窗  
 建立資料繫結控制項之前，您必須先將資料來源加入至 \[資料來源\] 視窗。  
  
#### 將資料來源加入至資料來源視窗  
  
1.  指向 \[檢視\] 功能表中的 \[其他視窗\]，然後按一下 \[資料來源\]。  
  
2.  按一下 \[加入新資料來源\]，並完成 \[資料來源組態精靈\]。  
  
3.  執行下列工作之一，以建立資料繫結控制項：  
  
    -   [建立繫結至資料的單一欄位的控制項](#simple)。  
  
    -   [建立繫結至資料的多個欄位的控制項](#complex)。  
  
    -   [建立一組繫結至資料的多個欄位的控制項](#details)。  
  
    -   [將資料繫結至設計工具中的現有控制項](#existing)。  
  
##  <a name="simple"></a> 建立繫結至資料的單一欄位的控制項  
 您可以在將資料來源加入至 \[資料來源\] 視窗之後，建立新的資料繫結控制項，例如 <xref:System.Windows.Controls.ComboBox> 或 <xref:System.Windows.Controls.TextBox>，以顯示資料的單一欄位。  
  
#### 建立繫結至資料的單一欄位的控制項  
  
1.  在 \[資料來源\] 視窗中，展開代表資料表或物件的項目。  找出代表您想要與之繫結的資料行或屬性的子項目。  如需圖示範例，請參閱 [資料來源視窗](../Topic/Data%20Sources%20Window.md)將  
  
2.  或者，選取要建立的控制項。  將項目拖曳到設計工具時，\[資料來源\] 視窗中的每個項目都會有一個建立的預設控制項。  預設控制項會根據項目的基礎資料類型而有所不同。  
  
     若要選擇不同的控制項，請按一下項目旁邊的下拉式箭頭，並選取控制項。  如需詳細資訊，請參閱[設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)。  
  
3.  將項目拖曳至設計工具中的有效容器中，例如 <xref:System.Windows.Controls.Grid>。  如需有效容器的詳細資訊，請參閱 [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會在容器中建立新的資料繫結控制項，以及適當標題的 <xref:System.Windows.Controls.Label>。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 也會產生 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 及程式碼，以將控制項繫結至資料。  如需詳細資訊，請參閱[將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
##  <a name="complex"></a> 建立繫結至資料的多個欄位的控制項  
 您可以在將資料來源加入至 \[資料來源\] 視窗之後，建立新的資料繫結控制項，例如 <xref:System.Windows.Controls.DataGrid> 或 <xref:System.Windows.Controls.ListView>，以顯示資料的多個欄位。  
  
#### 建立繫結至資料的多個欄位的控制項  
  
1.  在 \[資料來源\] 視窗中，選取代表資料表或物件的項目。  如需圖示範例，請參閱 [資料來源視窗](../Topic/Data%20Sources%20Window.md)將  
  
2.  或者，選取要建立的控制項。  根據預設，\[資料來源\] 視窗中代表資料表或物件的每個項目會設為建立 <xref:System.Windows.Controls.DataGrid> \(若您的專案目標是 .NET Framework 4\) 或 <xref:System.Windows.Controls.ListView> \(針對較舊版本的 .NET Framework\)。  
  
     若要選取不同的控制項，請按一下項目旁邊的下拉式箭頭，並選取控制項。  如需詳細資訊，請參閱[設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)。  
  
    > [!NOTE]
    >  若您不想要顯示特定資料行或屬性，請展開項目以顯示其子項。  在您不想要顯示的資料行或屬性旁邊按下拉式箭頭，然後按一下 \[無\]。  
  
3.  將項目拖曳至設計工具中的有效容器中，例如 <xref:System.Windows.Controls.Grid>。  如需有效容器的詳細資訊，請參閱 [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會在容器中建立新的資料繫結控制項。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 也會產生 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 及程式碼，以將控制項繫結至資料。  如需詳細資訊，請參閱[將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
##  <a name="details"></a> 建立一組繫結至資料的多個欄位的控制項  
 您可以在將資料來源加入至 \[資料來源\] 視窗之後，將資料表或物件繫結至一組控制項。  會針對資料表或物件中的每個資料行或屬性建立不同的控制項。  
  
#### 建立一組繫結至資料的多個欄位的控制項  
  
1.  在 \[資料來源\] 視窗中，選取代表資料表或物件的項目。  如需圖示範例，請參閱 [資料來源視窗](../Topic/Data%20Sources%20Window.md)將  
  
2.  按一下項目旁邊的下拉式箭頭，並選取 \[詳細資料\]。  
  
    > [!NOTE]
    >  若您不想要顯示特定資料行或屬性，請展開項目以顯示其子項。  在您不想要顯示的資料行或屬性旁邊按下拉式箭頭，然後按一下 \[無\]。  
  
3.  將項目拖曳至設計工具中的有效容器中，例如 <xref:System.Windows.Controls.Grid>。  如需有效容器的詳細資訊，請參閱 [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)將  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會在容器中建立新的資料繫結控制項。  每個控制項都會繫結至不同的資料行或屬性，且每個控制項都會伴隨一個適當標題的 <xref:System.Windows.Controls.Label> 控制項，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 也會產生 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 及程式碼，以將控制項繫結至資料。  如需詳細資訊，請參閱[將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
##  <a name="existing"></a> 將資料繫結至設計工具中的現有控制項  
 您可以在將資料來源加入至 \[資料來源\] 視窗之後，將資料繫結加入至設計工具中的現有控制項。  
  
#### 將資料繫結至設計工具中的現有控制項  
  
1.  在 \[資料來源\] 視窗中，使用下列程序之一：  
  
    -   若要將資料繫結加入至顯示資料的多個欄位的現有控制項，例如 <xref:System.Windows.Controls.DataGrid> 或 <xref:System.Windows.Controls.ListView>，請選取代表您想要繫結至控制項之資料表或物件的項目。  
  
    -   若要將資料繫結加入至顯示資料的單一欄位的現有控制項，例如 <xref:System.Windows.Controls.ComboBox> 或 <xref:System.Windows.Controls.TextBox>，請展開代表資料表或物件 \(其中包含該資料\) 的項目，然後選取代表您想要繫結至控制項之資料的項目。  
  
2.  從 \[資料來源\] 視窗，將選取的項目拖曳至設計工具中的現有控制項。  控制項必須是能夠有效拖放的目標。  如需詳細資訊，請參閱[將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會產生 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 及程式碼，以將控制項繫結至資料。  如需詳細資訊，請參閱[將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
    > [!NOTE]
    >  若控制項已繫結至資料，則會將控制項的資料繫結重設為已在最近拖曳至控制項的項目。  
  
## 請參閱  
 [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [如何：利用 WPF 應用程式建立查閱資料表](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [如何：在 WPF 應用程式中顯示相關的資料](../data-tools/display-related-data-in-wpf-applications.md)   
 [逐步解說：將 WPF 控制項繫結到資料集](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [逐步解說：將 WPF 控制項繫結至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [逐步解說：顯示 WPF 應用程式中的相關資料](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)