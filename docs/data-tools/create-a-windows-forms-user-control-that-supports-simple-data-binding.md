---
title: "逐步解說：建立支援簡單資料繫結的 Windows Form 使用者控制項 | Microsoft Docs"
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
  - "自訂控制項 [Visual Studio], 資料來源視窗"
  - "資料來源視窗, 控制項"
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：建立支援簡單資料繫結的 Windows Form 使用者控制項
在 Windows 應用程式中於表單上顯示資料時，您可以從 \[工具箱\] 中選擇現有控制項，或者，如果您的應用程式需要標準控制項中未提供的功能，也可以編寫自訂控制項。  這個逐步解說顯示如何建立可實作 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> 的控制項。  可實作 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> 的控制項可以包含一個可繫結至資料的屬性。  這類控制項類似 <xref:System.Windows.Forms.TextBox> 或 <xref:System.Windows.Forms.CheckBox>。  
  
 如需控制項製作的詳細資訊，請參閱[在設計階段開發 Windows Form 控制項](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md)。  
  
 製作控制項以用於資料繫結情節時，您需要實作下列其中一個資料繫結屬性：  
  
|資料繫結屬性使用方式|  
|----------------|  
|對顯示資料之單一資料行 \(或屬性\) 的簡單控制項 \(如 <xref:System.Windows.Forms.TextBox>\)，實作 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> \(這個逐步解說頁面會描述此流程\)。|  
|對顯示資料之清單 \(或資料表\) 的控制項 \(如 <xref:System.Windows.Forms.DataGridView>\)，實作 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> 如需詳細資訊，請參閱[逐步解說：建立支援複雜資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)。|  
|對顯示資料之清單 \(或資料表\) 但也需要呈現單一資料行或屬性的控制項 \(如 <xref:System.Windows.Forms.ComboBox>\)，實作 <xref:System.ComponentModel.LookupBindingPropertiesAttribute>。  如需詳細資訊，請參閱[逐步解說：建立支援查閱資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。|  
  
 這個逐步解說會建立簡單控制項，以顯示來自資料表中單一資料行的資料。  此範例使用 Northwind 範例資料庫中 `Customers` 資料表的 `Phone` 資料行。  透過使用 <xref:System.Windows.Forms.MaskedTextBox> 並設定電話號碼的遮罩，簡單使用者控制項將會以標準電話號碼格式顯示客戶的電話號碼。  
  
 在這個逐步解說期間，您將了解如何：  
  
-   建立新的 \[Windows 應用程式\]。  
  
-   將新的 \[使用者控制項\] 加入至專案。  
  
-   透過視覺化方式設計使用者控制項。  
  
-   實作 `DefaultBindingProperty` 屬性。  
  
-   使用[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)建立資料集。  
  
-   在 \[資料來源\] 視窗中設定 \[Phone\] 資料行，以使用新的控制項。  
  
-   建立表單以顯示新控制項中的資料。  
  
## 必要條件  
 若要完成這個逐步解說，您將需要：  
  
-   Northwind 範例資料庫的存取權。  如需詳細資訊，請參閱[如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## 建立 Windows 應用程式  
 第一個步驟是建立 \[Windows 應用程式\]。  
  
#### 建立新的 Windows 專案  
  
1.  在 Visual Studio 中，從 \[檔案\] 功能表中建立新的 \[專案\]。  
  
2.  將專案命名為 \[SimpleControlWalkthrough\]。  
  
3.  選取 \[Windows 應用程式\]，然後按一下 \[確定\]。  如需詳細資訊，請參閱[用戶端應用程式](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
     隨即建立 \[SimpleControlWalkthrough\] 專案，並將它加入至 \[方案總管\]。  
  
## 將使用者控制項加入至專案  
 這個逐步解說會從 \[使用者控制項\] 建立簡單資料可繫結控制項，進而將 \[使用者控制項\] 項目加入至 \[SimpleControlWalkthrough\] 專案。  
  
#### 將使用者控制項加入至專案  
  
1.  從 \[專案\] 功能表中，選擇 \[加入使用者控制項\]。  
  
2.  在 \[名稱\] 區域中輸入 `PhoneNumberBox`，然後按一下 \[加入\]。  
  
     \[PhoneNumberBox\] 控制項會加入至 \[方案總管\]，並且可在設計工具中開啟。  
  
## 設計 PhoneNumberBox 控制項  
 這個逐步解說會從現有 <xref:System.Windows.Forms.MaskedTextBox> 擴充，以建立 `PhoneNumberBox` 控制項。  
  
#### 設計 PhoneNumberBox 控制項  
  
1.  將 <xref:System.Windows.Forms.MaskedTextBox> 從 \[工具箱\] 拖曳至使用者控制項的設計介面。  
  
2.  在 <xref:System.Windows.Forms.MaskedTextBox> 上選取您剛剛拖曳的智慧標籤，並選擇 \[設定遮罩\]。  
  
3.  在 \[輸入遮罩\] 對話方塊中，選取 \[電話號碼\]，然後按一下 \[確定\] 設定遮罩。  
  
## 加入必要的資料繫結屬性  
 針對支援資料繫結的簡單控制項，實作 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>。  
  
#### 實作 DefaultBindingProperty 屬性  
  
1.  將 `PhoneNumberBox` 控制項切換至程式碼檢視   \(在 \[檢視\] 功能表上，選擇 \[程式碼\]\)。  
  
2.  將 `PhoneNumberBox` 中的程式碼取代為下列內容：  
  
     [!code-cs[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]  
  
3.  從 \[**建置**\] 功能表中，選擇 \[**建置方案**\]。  
  
## 從資料庫建立資料來源  
 此步驟使用 \[資料來源組態精靈\]，根據 Northwind 範例資料庫中的 `Customers` 資料表建立資料來源。  您必須具有 Northwind 範例資料庫的存取權，才能建立連接。  如需設定 Northwind 範例資料庫的詳細資訊，請參閱[如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
#### 若要建立資料來源  
  
1.  按一下 \[**資料**\] 功能表上的 \[**顯示資料來源**\]。  
  
2.  在 \[資料來源\] 視窗中，選取 \[加入新資料來源\] 啟動 \[資料來源組態精靈\]。  
  
3.  請選取 \[**選擇資料來源類型**\] 頁面上的 \[**資料庫**\]，再按 \[**下一步**\]。  
  
4.  在 \[選擇資料連接\] 頁面上，執行下列其中一項：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
         或  
  
    -   選取 \[**新增連接**\]，啟動 \[**新增\/修改連接**\] 對話方塊。  
  
5.  如果資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下 \[**下一步**\]。  
  
6.  在 \[將連接字串儲存到應用程式組態檔\] 頁面上，按 \[下一步\]。  
  
7.  在 \[**選擇您的資料庫物件**\] 頁面上，展開 \[**資料表**\] 節點。  
  
8.  選取 `Customers` 資料表，然後按一下 \[完成\]。  
  
     \[NorthwindDataSet\] 會加入專案中，且 `Customers` 資料表會出現在 \[資料來源\] 視窗中。  
  
## 設定 Phone 資料行使用 PhoneNumberBox 控制項  
 在 \[資料來源\] 視窗內，您可以設定在將項目拖曳至表單之前建立控制項。  
  
#### 設定要繫結至 PhoneNumberBox 控制項的 Phone 資料行  
  
1.  在設計工具中，開啟 \[Form1\]。  
  
2.  在 \[資料來源\] 視窗中，展開 \[Customers\] 節點。  
  
3.  按一下 \[Customers\] 節點上的下拉箭號，並從控制項清單中選擇 \[詳細資料\]。  
  
4.  按一下 \[Phone\] 資料行上的下拉箭號，並選擇 \[自訂\]。  
  
5.  在 \[自訂資料欄位 UI 選項\] 對話方塊中，從 \[關聯的控制項\] 清單中選取 \[PhoneNumberBox\]。  
  
6.  按一下 \[Phone\] 資料行上的下拉箭號，並選擇 \[PhoneNumberBox\]。  
  
## 將控制項加入至表單  
 將項目從 \[資料來源\] 視窗拖曳至表單，以建立資料繫結控制項。  
  
#### 在表單上建立資料繫結控制項  
  
-   將 \[Customers\] 主節點從 \[資料來源\] 視窗拖曳至表單，並確認使用 `PhoneNumberBox` 控制項來顯示 `Phone` 資料行中的資料。  
  
     會在表單上顯示具有描述性標籤的資料繫結控制項，以及巡覽記錄的工具區域 \(<xref:System.Windows.Forms.BindingNavigator>\)。  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator> 則會出現在元件匣中。  
  
## 執行應用程式  
  
#### 若要執行應用程式  
  
-   按 F5 執行應用程式。  
  
## 後續步驟  
 根據應用程式的需求，在建立支援資料繫結的控制項之後，可能會有幾個想要執行的步驟。  一些一般後續步驟包括：  
  
-   將自訂控制項放入控制項程式庫，讓您可以在其他應用程式中重複予以使用。  
  
-   建立支援更複雜資料繫結情節的控制項。  如需詳細資訊，請參閱[逐步解說：建立支援複雜資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)與[逐步解說：建立支援查閱資料繫結的 Windows Form 使用者控制項](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)。  
  
## 請參閱  
 [設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio 資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)