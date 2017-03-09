---
title: "Visual Studio 中的物件繫結 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "繫結, 至物件"
  - "資料 [Visual Studio], 繫結至物件"
  - "資料 [Visual Studio], 物件繫結"
  - "物件繫結"
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Visual Studio 中的物件繫結
Visual Studio 提供了一些設計階段工具，可將自訂物件 \(而非其他資料來源如實體、資料集和服務\) 當做應用程式中的資料來源使用。  
  
## 物件需求  
 要讓自訂物件與 Visual Studio 中的資料設計工具搭配使用，唯一的要求就是物件至少需要有一個公用屬性。  
  
 自訂物件通常並不需要特定的介面、建構函式或屬性，即可做為應用程式的資料來源。  不過，如果您要從 \[**資料來源**\] 視窗將物件拖曳至設計介面以建立資料繫結控制項，而且如果此物件實作 <xref:System.ComponentModel.ITypedList> 或 <xref:System.ComponentModel.IListSource> 介面，物件必須有預設建構函式 \(即無參數的建構函式\)。  否則，Visual Studio 無法執行個體化資料來源物件，而且當您將項目拖曳至設計介面時會顯示錯誤。  
  
## 使用自訂物件做為資料來源的範例  
 雖然將物件當做資料來源使用時，有不計其數的方式可實作應用程式邏輯，但是只有少數標準作業可藉由使用 Visual Studio 產生的 [TableAdapter](../data-tools/tableadapter-overview.md) 物件加以簡化。  這個頁面將會說明如何使用 TableAdapter 實作這些標準處理序。不過，這並不是要做為建立自訂物件的指引。  例如，您通常會執行下列標準作業，而不論物件或應用程式邏輯的特定實作為何：  
  
-   將資料載入物件中 \(通常是從資料庫\)。  
  
-   建立物件的具型別集合。  
  
-   將物件加入至集合或從集合移除物件。  
  
-   將表單上的物件資料顯示給使用者。  
  
-   變更\/編輯物件中的資料。  
  
-   將物件的資料儲存回資料庫中。  
  
> [!NOTE]
>  為了深入瞭解並提供這個頁面上範例的內容，我們建議您完成下列[逐步解說：連接至物件中的資料 \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)。  該逐步解說會建立這個說明網頁上討論的物件。  
  
### 將資料載入物件中  
 在這個範例中，您會使用 TableAdapter 將資料載入物件中。  根據預設，TableAdapter 是透過從資料庫擷取資料和填入資料表的兩種方法所建立。  
  
-   `TableAdapter.Fill` 方法會以傳回的資料填入現有的資料表。  
  
-   `TableAdapter.GetData` 方法會傳回以資料填入的新資料表。  
  
 將資料載入自訂物件最簡單的方式，就是呼叫 `TableAdapter.GetData` 方法、在傳回資料表的資料列集合中執行迴圈 \(Loop\)，然後使用每個資料列中的值填入每個物件。  您可以針對加入 TableAdapter 的任何查詢，建立 `GetData` 方法，以便傳回已填入的資料表。  
  
> [!NOTE]
>  根據預設，Visual Studio 會將 TableAdapter 查詢命名為 `Fill` 和 `GetData`，不過這些名稱可變更為任何有效的方法名稱。  
  
 下列範例將示範如何對資料表的資料列執行迴圈，並以資料填入物件：  
  
 如需完整的程式碼範例，請參閱[逐步解說：連接至物件中的資料 \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)。  
  
 [!code-cs[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]  
  
### 建立物件的具型別集合  
 您可以建立物件的集合類別 \(Collection Class\)，或是使用由 [BindingSource 元件](../Topic/BindingSource%20Component.md)自動提供的具型別集合。  
  
 當您正在建立物件的自訂集合類別時，我們建議您從 <xref:System.ComponentModel.BindingList%601> 繼承。  這個泛型類別會提供可管理集合的功能，以及引發事件的能力，以便傳送告知至 Windows Form 中的資料繫結基礎結構。  
  
 在 <xref:System.Windows.Forms.BindingSource> 中自動產生的集合會使用其具型別集合的 <xref:System.ComponentModel.BindingList%601>。  如果您的應用程式不需要其他功能，您就可以在 <xref:System.Windows.Forms.BindingSource> 內維護集合。  如需詳細資訊，請參閱 <xref:System.Windows.Forms.BindingSource> 類別的 <xref:System.Windows.Forms.BindingSource.List%2A> 屬性。  
  
> [!NOTE]
>  如果您的集合將會需要未由 <xref:System.ComponentModel.BindingList%601> 基底實作所提供的功能，則您應該建立自訂集合，以便可以在需要時加入至類別中。  
  
 下列程式碼將示範如何針對 `Order` 物件的強型別集合，建立類別：  
  
 [!code-cs[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]  
  
### 將物件加入至集合  
 您可以呼叫自訂集合類別或 <xref:System.Windows.Forms.BindingSource> 的 `Add` 方法，將物件加入至集合中。  
  
 如需使用 <xref:System.Windows.Forms.BindingSource> 加入至集合的範例，請參閱[逐步解說：連接至物件中的資料 \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)中的 `LoadCustomers` 方法。  
  
 如需將物件加入至自訂集合的範例，請參閱[逐步解說：連接至物件中的資料 \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)中的 `LoadOrders` 方法。  
  
> [!NOTE]
>  當您從 <xref:System.ComponentModel.BindingList%601> 繼承時，就會自動為您的自訂集合提供 `Add` 方法。  
  
 下列程式碼會示範如何將物件加入至 <xref:System.Windows.Forms.BindingSource> 中的具型別集合：  
  
 [!code-cs[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]  
  
 下列程式碼會示範如何將物件加入至繼承自 <xref:System.ComponentModel.BindingList%601> 的具型別集合：  
  
> [!NOTE]
>  在這個範例中，`Orders` 集合是 `Customer` 物件的屬性。  
  
 [!code-cs[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]  
  
### 從集合移除物件  
 您可以呼叫自訂集合類別或 <xref:System.Windows.Forms.BindingSource> 的 `Remove` 或 `RemoveAt` 方法，從集合移除物件。  
  
> [!NOTE]
>  當您從 <xref:System.ComponentModel.BindingList%601> 繼承時，就會自動為您的自訂集合提供 `Remove` 和 `RemoveAt` 方法。  
  
 下列程式碼將示範如何使用 <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> 方法，從 <xref:System.Windows.Forms.BindingSource> 的具型別集合中找出並移除物件：  
  
 [!code-cs[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]  
  
### 將物件資料顯示給使用者  
 若要將物件的資料顯示給使用者，您可以使用[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)建立物件資料來源，然後從 \[**資料來源**\] 視窗將整個物件或個別的屬性拖曳至表單上。  
  
 如需如何建立物件資料來源的詳細資訊，請參閱 [如何：連接至物件中的資料](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)。  
  
 如需如何在 Windows Form 上顯示物件資料的詳細資訊，請參閱[將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
### 修改物件中的資料  
 若要編輯資料繫結至 Windows Form 控制項之自訂物件中的資料，只要在繫結的控制項 \(或直接在物件的屬性\) 中編輯資料即可。  然後，資料繫結架構就會更新物件中的資料。  
  
 如果您的應用程式需要追蹤變更並將建議變更復原為原始值，您就必須在物件模型中實作這項功能。  如需資料表如何追蹤建議變更的範例，請參閱 <xref:System.Data.DataRowState>、<xref:System.Data.DataSet.HasChanges%2A> 和 <xref:System.Data.DataTable.GetChanges%2A>。  
  
### 將物件的資料儲存回資料庫中  
 您可以將資料儲存回資料庫中，方法是將物件的值傳遞至 TableAdapter 的 DBDirect 方法。  
  
 Visual Studio 會建立可直接對資料庫執行的 DBDirect 方法。  這些方法不需要 DataSet 或 DataTable 物件。  
  
|TableAdapter DBDirect 方法|描述|  
|------------------------------|--------|  
|`TableAdapter.Insert`|將新資料錄加入至資料庫，並讓您傳入個別的資料行值做為方法參數。|  
|`TableAdapter.Update`|更新資料庫中的現有資料錄。  此 Update 方法會採用原始和新的資料行值做為方法參數。  原始值是用來找出原始資料錄，而新值則是用來更新該資料錄。<br /><br /> 此外，`TableAdapter.Update` 方法也會用來將資料集的變更調整回資料庫中，方式是採用 <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow> 或 <xref:System.Data.DataRow> 的陣列做為方法參數。|  
|`TableAdapter.Delete`|根據傳入做為方法參數的原始資料行值，從資料庫刪除現有的資料錄。|  
  
 若要儲存物件集合的資料，請在物件的集合中執行迴圈 \(例如，使用 for\-next 迴圈\)，然後使用 TableAdapter 的 DBDirect 方法，將每個物件的值傳送至資料庫中。  
  
 下列範例將示範如何使用 `TableAdapter.Insert` DBDirect 方法，直接將新的客戶加入至資料庫中：  
  
 [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
 [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]  
  
## 請參閱  
 [如何：連接至物件中的資料](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)   
 [逐步解說：連接至物件中的資料 \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)   
 [如何：從物件中將資料儲存至資料庫](../data-tools/save-data-from-an-object-to-a-database.md)   
 [如何：以 TableAdapter 直接存取資料庫](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [逐步解說：使用 TableAdapter DBDirect 方法儲存資料](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [TableAdapter](../Topic/TableAdapters.md)   
 [儲存資料](../data-tools/saving-data.md)