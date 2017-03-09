---
title: "如何：連接至資料庫中的資料 | Microsoft Docs"
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
  - "資料 [Visual Studio], 連接至資料庫"
  - "資料來源, 建立"
  - "資料來源, 資料庫"
  - "資料庫連接"
  - "資料庫, 連接至"
ms.assetid: 6c56e54e-8834-4297-85aa-cc1a443ba556
caps.latest.revision: 55
caps.handback.revision: 55
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：連接至資料庫中的資料
您可以使用 Visual Studio 將應用程式連接至資料庫。  在建立資料連線之後，Visual Studio 會產生由應用程式用來與資料庫資料進行互動的資料模型。  資料模型中的物件會出現在[資料來源視窗](../Topic/Data%20Sources%20Window.md)。  然後您可以從 \[**資料來源**\] 視窗將項目拖曳至設計介面上，藉以建立資料繫結控制項。  如需詳細資訊，請參閱[將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
 本主題提供有關連接至資料庫以及建立下列資料模型類型的指示：  
  
-   資料集  
  
-   實體資料模型 \(EDM\)  
  
> [!NOTE]
>  您也可以使用 Visual Studio，從資料庫建立 LINQ to SQL 類別。  不過，LINQ to SQL 類別不會出現在 \[**資料來源**\] 視窗中，因此無法直接拖曳至設計工具建立資料繫結控制項。  如需從資料庫建立 LINQ to SQL 類別的詳細資訊，請參閱 [HOW TO：建立對應到資料表和檢視的 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md)。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
##  <a name="dataset"></a> 連接至資料庫和建立資料集  
 當您根據資料庫建立資料集時，Visual Studio 會建立一組表示可程式資料檢視的類別。  主要類別稱為「*具類型資料集*」\(Typed Dataset\)。  具類型資料集包含表示資料庫資料表的資料表物件。  如需具類型資料集的詳細資訊，請參閱 [使用 Visual Studio 中的資料集](../data-tools/dataset-tools-in-visual-studio.md)。  
  
 在建立資料集之後，只要將資料集物件從 \[資料來源\] 視窗拖曳至 WPF 或 Windows Form 設計工具，就可以建立資料繫結 WPF 或 Windows Form 控制項。  
  
#### 若要將應用程式連接至資料庫和建立資料集  
  
1.  在 Visual Studio 中開啟現有專案，或建立新的專案。  
  
2.  在 \[**資料**\] 功能表上，請按一下 \[**加入新資料來源**\]。  
  
     \[**資料來源組態精靈**\] 隨即開啟。  
  
3.  在 \[**選擇資料來源類型**\] 頁面上，選取 \[**資料庫**\]，再按 \[**下一步**\]。  
  
4.  在 \[**選擇資料庫模型**\] 頁面上，選取 \[**資料集**\]，再按 \[**下一步**\]。  
  
5.  從 \[**選擇資料連線**\] 頁面上的可用連接清單中，選取資料連線，再按 \[**下一步**\]。  
  
     如果沒有您要的資料連線，請依照[建立新的資料庫連接](#CreatingDataConnection)中的步驟，建立新的連接。  
  
6.  在 \[**將連接字串儲存至應用程式組態檔**\] 頁面上，如果您要將連接字串直接儲存至編譯的應用程式，請選擇性清除 \[**是，將連接儲存為**\] 核取方塊。  根據預設，此連接會儲存在應用程式組態檔中。  如需詳細資訊，請參閱[如何：儲存和編輯連接字串](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md)。  
  
7.  從 \[**選擇您的資料庫物件**\] 頁面上，選取將用於應用程式的資料庫物件。  您也可以選擇取代預設的 \[**資料集名稱**\]。  
  
8.  按一下 \[**完成**\]。  剛才建立的資料集，現在可以在 \[**資料來源**\] 視窗中使用了。  
  
    > [!NOTE]
    >  如果 \[**資料來源**\] 視窗未開啟，請按一下 \[**資料**\] 功能表上的 \[**顯示資料來源**\]，開啟此視窗。  
  
9. 您現在可以從 \[**資料來源**\] 視窗將項目拖曳至 WPF 設計工具、Windows Form 設計工具或[Component Designer](../Topic/Component%20Designer.md)中，以建立資料繫結控制項。  如需詳細資訊，請參閱[將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
##  <a name="edm"></a> 連接至資料庫和建立實體資料模型  
 當您根據資料庫建立實體資料模型時，Visual Studio 會建立一組表示可程式資料檢視的類別。  如需實體資料模型與 ADO.NET Entity Framework 的詳細資訊，請參閱[Entity Framework 概觀](../Topic/Entity%20Framework%20Overview.md)。  
  
 在建立實體資料模型之後，您可以從 \[資料來源\] 視窗將實體物件拖曳至 WPF 設計工具中，以建立資料繫結 WPF 控制項。  
  
#### 若要將應用程式連接至資料庫和建立實體資料模型  
  
1.  在 Visual Studio 中開啟現有專案，或建立新的專案。  
  
2.  依照 \[**實體資料模型精靈**\] 中的步驟，連接至資料庫並指定模型內容。  如需詳細資訊，請參閱[How to: Create a New .edmx File](http://msdn.microsoft.com/zh-tw/beb8189e-e51c-4051-839c-9902c224abf2)。  
  
3.  在完成 \[**實體資料模型精靈**\] 之後，您所建立的實體資料模型會在 \[實體資料模型設計工具\] 中開啟，而且資料物件現在可在 \[**資料來源**\] 視窗中使用。  
  
    > [!NOTE]
    >  如果 \[**資料來源**\] 視窗未開啟，請按一下 \[**資料**\] 功能表上的 \[**顯示資料來源**\]，開啟此視窗。  
  
4.  如果 WPF 設計工具已開啟，您現在可以從 \[**資料來源**\] 視窗將項目拖曳至設計工具中，以建立繫結至實體資料模型的控制項。  如需詳細資訊，請參閱[如何：將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)。  
  
     如果 Windows Form 設計工具已開啟，您無法從 \[**資料來源**\] 將項目拖曳至設計工具。  若要建立繫結至實體資料模型的控制項，您必須建置專案，根據實體資料模型加入新的物件資料來源，然後將這些物件拖曳至設計工具。  
  
##  <a name="CreatingDataConnection"></a> 建立新的資料庫連接  
 當您使用 \[**資料來源組態精靈**\] 或 \[**實體資料模型精靈**\] 時，必須指定要使用的資料庫連接。  如果您尚未有可用的資料庫連接，請執行下列步驟建立連接。  
  
 下列指示假設您已經依照[連接至資料庫和建立資料集](#dataset)和[連接至資料庫和建立實體資料模型](#edm)所述，啟動 \[**資料來源組態精靈**\] 或 \[**實體資料模型精靈**\]。  
  
#### 若要建立新的資料庫連接  
  
1.  在 \[**資料來源組態精靈**\] 或 \[**實體資料模型精靈**\] 的 \[**選擇資料來源類型**\] 頁面中，按一下 \[**新增連接**\]。  
  
     發生下列其中一項動作：  
  
    -   如果您已經在 Visual Studio 中建立資料連線，\[**加入連接**\] 對話方塊隨即開啟。  
  
    -   如果這是您在 Visual Studio 中建立的第一個資料連線，\[**選擇資料來源**\] 對話方塊隨即顯示。  選取您想要連接的資料庫類型，然後按一下 \[**確定**\] 以顯示 \[**加入連接**\] 對話方塊。  
  
2.  在 \[**加入連接**\] 對話方塊中，輸入要求的資訊。  每種資料提供者類型的 \[**加入連接**\] 對話方塊不同。  
  
    > [!NOTE]
    >  如果 \[**加入連接**\] 對話方塊中選取的 \[**資料來源**\] 不是您要連接的資料來源，請按一下 \[**變更**\]，開啟 \[**變更資料來源**\] 對話方塊，然後選擇不同的資料來源。  
  
3.  在 \[**加入連接**\] 對話方塊中，按一下 \[**確定**\]。  
  
     隨即回到 \[**資料來源組態精靈**\] 或 \[**實體資料模型精靈**\] 的 \[**選擇資料來源類型**\] 頁面。  
  
4.  在 \[**選擇資料連線**\] 頁面中，確定已選取新資料連線，然後按 \[**下一步**\]。  
  
5.  完成 \[**資料來源組態精靈**\] 或 \[**實體資料模型精靈**\] 中的其餘步驟。  
  
## .NET Framework 安全性  
 儲存敏感資料 \(如密碼\) 會影響應用程式的安全性。  使用 Windows 驗證 \(也稱為整合式安全性\) 是控制資料庫存取的更安全方式。  如需詳細資訊，請參閱[保護連接資訊](../Topic/Protecting%20Connection%20Information.md)。  
  
## 請參閱  
 [資料來源概觀](../data-tools/add-new-data-sources.md)   
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [連接資料來源](../Topic/Connecting%20to%20a%20Data%20Source%20in%20ADO.NET.md)