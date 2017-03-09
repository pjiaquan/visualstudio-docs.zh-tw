---
title: "將 WPF 控制項繫結至 Visual Studio 中的資料 | Microsoft Docs"
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
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 36
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將 WPF 控制項繫結至 Visual Studio 中的資料
您可以透過將資料繫結至 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] 控制項，對應用程式的使用者顯示資料。  若要建立這些資料繫結控制項，您可以從 \[**資料來源**\] 視窗將項目拖曳至 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] 中的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  本主題描述可用來建立資料繫結 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] 應用程式的一些最常用工作、工具和類別。  
  
 如需如何在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中建立資料繫結控制項的一般資訊，請參閱[將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。 如需 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] 資料繫結的詳細資訊，請參閱[資料繫結概觀](../Topic/Data%20Binding%20Overview.md)。  
  
## 將 WPF 控制項繫結至資料的相關工作  
 下表列出可透過從 \[**資料來源**\] 視窗將項目拖曳至 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]所完成的工作。  
  
|工作|詳細資訊|  
|--------|----------|  
|建立新的資料繫結控制項。<br /><br /> 將現有控制項繫結至資料。|[如何：將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)|  
|建立可顯示父子關係中相關資料的控制項：當使用者選取某個控制項中的父資料記錄時，另一個控制項會顯示選取之記錄的相關子資料。|[如何：在 WPF 應用程式中顯示相關的資料](../data-tools/display-related-data-in-wpf-applications.md)|  
|建立「*查閱資料表*」\(Lookup Table\)，其根據某個資料表中的外部索引鍵欄位值，顯示另一個資料表的資訊。|[如何：利用 WPF 應用程式建立查閱資料表](../data-tools/create-lookup-tables-in-wpf-applications.md)|  
|將控制項繫結至資料庫中的圖片。|[如何：從資料庫將控制項繫結至圖片](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
  
## 有效置放目標  
 \[**資料來源**\] 視窗中的項目只能拖曳至 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]中的有效置放目標。  有效置放目標有兩種：容器和控制項。  容器是通常會包含控制項的使用者介面項目。  例如，格線是容器，視窗也是容器。  
  
## 產生的 XAML 和程式碼  
 當您從 \[**資料來源**\] 視窗將項目拖曳至 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會產生定義新資料繫結控制項 \(或將現有控制項繫結至資料來源\) 的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]。  對於某些資料來源，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 也會在程式碼後置檔案中產生可將資料填入資料來源的程式碼。  
  
 下表列出 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 針對 \[[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]資料來源\] 視窗中的每種資料來源類型所產生的  **和程式碼。**  
  
|資料來源|產生可將控制項繫結至資料來源的 XAML|產生可將資料填入資料來源的程式碼|  
|----------|--------------------------|----------------------|  
|資料集|是|是|  
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|是|是|  
|服務|是|否|  
|物件|是|否|  
  
### 資料集  
 當您從 \[**資料來源**\] 視窗將資料表或資料行拖曳至設計工具時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會產生完成下列工作的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]：  
  
-   將資料集或新 <xref:System.Windows.Data.CollectionViewSource> 加入至拖曳目標容器的資源。  <xref:System.Windows.Data.CollectionViewSource> 物件可用來巡覽及顯示資料集中的資料。  
  
-   建立控制項的資料繫結。  如果您將項目拖曳至設計工具中的現有控制項，XAML 會將控制項繫結至項目。  如果您將項目拖曳至容器，XAML 會針對拖曳的項目建立所選取的控制項，並將控制項繫結至項目。  控制項是在新的 <xref:System.Windows.Controls.Grid> 內建立。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 也會對程式碼後置檔案進行下列變更：  
  
-   針對包含控制項的 <xref:System.Windows.FrameworkElement.Loaded> 項目，建立 [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] 事件處理常式。  事件處理常式會將資料填入資料表，從容器的資源擷取 <xref:System.Windows.Data.CollectionViewSource>，然後讓第一個資料項目成為目前的項目。  如果 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式已經存在，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 便會將此程式碼加入至現有的事件處理常式。  
  
### 實體資料模型  
 當您從 \[**資料來源**\] 視窗將實體或實體屬性拖曳至設計工具時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會產生完成下列工作的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]：  
  
-   將新 <xref:System.Windows.Data.CollectionViewSource> 加入至拖曳目標容器的資源。  <xref:System.Windows.Data.CollectionViewSource> 物件可用來巡覽及顯示實體中的資料。  
  
-   建立控制項的資料繫結。  如果您將項目拖曳至設計工具中的現有控制項，[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 會將控制項繫結至項目。  如果您將項目拖曳至容器，[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 會針對拖曳的項目建立所選取的控制項，並將控制項繫結至項目。  控制項是在新的 <xref:System.Windows.Controls.Grid> 內建立。  
  
 Visual Studio 也會對程式碼後置檔案進行下列變更：  
  
-   加入新方法，其針對您拖曳至設計工具的實體 \(或包含拖曳至設計工具之屬性的實體\)，傳回查詢。  新方法的名稱為 Get*EntityName*Query，其中 *EntityName* 是實體的名稱。  
  
-   針對包含控制項的 <xref:System.Windows.FrameworkElement.Loaded> 項目，建立 [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] 事件處理常式。  事件處理常式會呼叫 Get*EntityName*Query 方法將資料填入實體，從容器的資源擷取 <xref:System.Windows.Data.CollectionViewSource>，然後讓第一個資料項目成為目前的項目。  如果 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式已經存在，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 便會將此程式碼加入至現有的事件處理常式。  
  
### 服務  
 當您從 \[**資料來源**\] 視窗將服務物件或屬性拖曳至設計工具時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會產生建立資料繫結控制項 \(或將現有控制項繫結至物件或屬性\) 的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]。  不過，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 不會產生可將資料填入 Proxy 服務物件的程式碼。  您必須自行撰寫此程式碼。  如需示範如何執行這項操作的範例，請參閱[逐步解說：將 WPF 控制項繫結至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)。  
  
 Visual Studio 會產生執行下列工作的 XAML：  
  
-   將新 <xref:System.Windows.Data.CollectionViewSource> 加入至拖曳目標容器的資源。  <xref:System.Windows.Data.CollectionViewSource> 物件可用來巡覽及顯示服務所傳回之物件中的資料。  
  
-   建立控制項的資料繫結。  如果您將項目拖曳至設計工具中的現有控制項，[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 會將控制項繫結至項目。  如果您將項目拖曳至容器，[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 會針對拖曳的項目建立所選取的控制項，並將控制項繫結至項目。  控制項是在新的 <xref:System.Windows.Controls.Grid> 內建立。  
  
### 物件  
 當您從 \[**資料來源**\] 視窗將物件或屬性拖曳至設計工具時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會產生建立資料繫結控制項 \(或將現有控制項繫結至物件或屬性\) 的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]。  不過，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 不會產生可將資料填入物件的程式碼。  您必須自行撰寫此程式碼。  
  
> [!NOTE]
>  自訂類別必須是公用的，並具有預設的無參數建構函式。  這些類別不能是在語法中包含「點」的巢狀類別。  如需詳細資訊，請參閱 [WPF 的 XAML 和自訂類別](../Topic/XAML%20and%20Custom%20Classes%20for%20WPF.md)。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會產生執行下列工作的 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]：  
  
-   將新 <xref:System.Windows.Data.CollectionViewSource> 加入至拖曳目標容器的資源。  <xref:System.Windows.Data.CollectionViewSource> 物件可用來巡覽及顯示物件中的資料。  
  
-   建立控制項的資料繫結。  如果您將項目拖曳至設計工具中的現有控制項，XAML 會將控制項繫結至項目。  如果您將項目拖曳至容器，XAML 會針對拖曳的項目建立所選取的控制項，並將控制項繫結至項目。  控制項是在新的 <xref:System.Windows.Controls.Grid> 內建立。  
  
## 請參閱  
 [如何：將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [如何：利用 WPF 應用程式建立查閱資料表](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [如何：在 WPF 應用程式中顯示相關的資料](../data-tools/display-related-data-in-wpf-applications.md)   
 [將 WPF 控制項繫結至實體資料模型](http://msdn.microsoft.com/data/jj574514.aspx)   
 [逐步解說：將 WPF 控制項繫結到資料集](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [逐步解說：將 WPF 控制項繫結至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [逐步解說：顯示 WPF 應用程式中的相關資料](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)   
 [資料來源視窗](../Topic/Data%20Sources%20Window.md)   
 [資料來源概觀](../data-tools/add-new-data-sources.md)