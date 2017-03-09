---
title: "區域資料概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "Access, Visual Studio 中的 .mdb 檔案"
  - "資料 [Visual Studio], 本機"
  - "資料存取 [Visual Studio], 疑難排解"
  - "區域資料"
  - "LocalDB"
  - "SQL Express"
  - "SQL Server Compact"
  - "SQL Server Express"
  - "SQL Server LocalDB"
  - "SQL Server, 區域資料"
  - "SQLEXPRESS"
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
caps.handback.revision: 66
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 區域資料概觀
當您使用本機資料時，您是將應用程式連接至本機電腦上的資料庫檔案，而不是連接至不同伺服器上的資料庫。  例如，您可以將要在 Visual Studio 中開發的應用程式連接到下列本機資料庫檔案：  
  
-   SQL Server Express LocalDB 資料庫檔案 \(.mdf\)  
  
-   SQL Server Express 資料庫檔案 \(.mdf\)  
  
-   Microsoft Access 資料庫檔案 \(.mdb\)  
  
 下表將提供說明如何將應用程式連接至本機資料的主題連結：  
  
|主題|描述|  
|--------|--------|  
|[逐步解說：在 Visual Studio 中建立本機資料庫檔案](../data-tools/create-a-sql-database-by-using-a-designer.md)|提供逐步指示，說明如何建置可用來測試資料功能和建立應用程式的本機資料庫檔案。|  
|[逐步解說：連接至本機資料庫檔案中的資料 \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)|針對如何在建立簡單 Windows 應用程式時連接至 SQL Server Express LocalDB 資料庫，提供逐步指示。|  
|[逐步解說：連接至 Access 資料庫中的資料 \(Windows Form\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|提供如何連接至 Microsoft Access 資料庫的逐步指示。|  
|[如何：連接到 Northwind 資料庫](../data-tools/how-to-connect-to-the-northwind-database.md)|提供如何連接到 [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]、SQL Server Compact、SQL Server Express 和 Access 中的 Northwind 範例資料庫的指示。|  
  
 在您建立資料來源並將其設定為存取本機資料檔之後，處理這項資料所使用的技術和物件，與您處理任何其他來源的資料時所用的相同。  如需詳細資訊，請參閱[建立資料應用程式](../data-tools/creating-data-applications.md)。  
  
## 將資料庫整合到應用程式中  
 如果您連接至本機資料，則不僅能連接至資料庫檔案，還可以將它整合至您的應用程式中。  例如，您可以開啟 \[**專案**\] 功能表，瀏覽至現有的 .sdf、.mdf 或 .mdb 檔案，然後將檔案加入至專案。  
  
 如果您加入本機資料檔，則會建立具類型資料集以及指向應用程式中資料庫檔的動態連接字串。  當您將資料庫檔案加入至專案後，您可以使用 \[**資料來源組態精靈**\] 來指定要包含的物件。  
  
> [!NOTE]
>  您可以將 .sdf、.mdf 或 .mdb 檔案從 \[檔案總管\] 拖曳至 \[**方案總管**\]，以自動設定連接並啟動 \[**資料來源組態精靈**\]。  然後您可以指定要在應用程式中使用的物件。  
  
 如果您使用 \[**資料來源組態精靈**\] 建立本機資料檔的資料來源，系統就會詢問您是否要將該檔案包含在專案中。  如果您不想加入該檔案，應用程式就只會包含硬式編碼路徑所指向的連接字串，而非實際的資料檔。  如需詳細資訊，請參閱 [如何：管理專案中的本機資料檔](../data-tools/how-to-manage-local-data-files-in-your-project.md)。  
  
 完成精靈之後，資料庫檔案和資料集都會顯示在 \[**方案總管**\]\/\[**資料庫總管**\] 中，而您指定的資料庫物件會在 \[**資料來源**\] 視窗中出現。  您可以從 \[**資料來源**\] 視窗將項目拖曳至表單上，藉以建立會繫結至基礎資料的控制項。  若要開啟 \[**資料來源**\] 視窗，請開啟 \[**資料**\] 功能表，然後選擇 \[**顯示資料來源**\]。  如需詳細資訊，請參閱[將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
## 使用資料庫檔案  
 您可能必須先將檔案轉換成 [!INCLUDE[sql_Denali_short](../data-tools/includes/sql_denali_short_md.md)] 資料庫檔案，才能在 Visual Studio 中使用現有的資料庫檔案 \(.mdf\)。  當您連接到現有的資料庫檔案時，訊息方塊會詢問您是否要升級。  
  
> [!IMPORTANT]
>  如果您升級資料庫檔案 \(.mdf\)，就無法在舊版 SQL Server 中將它開啟。  
  
 如果 \[**SQL Server 執行個體名稱**\] 是設定為 SQLEXPRESS，而且已安裝 SQL Server 2008 Express，您就不需要轉換資料庫檔案 \(.mdf\)。  如果已安裝 Visual Studio 2010，則表示已安裝 SQL Server 2008 Express。  若要變更此資料庫檔案的執行個體名稱，請開啟 Visual Studio，開啟 \[**加入連接**\] 對話方塊，指定 `.\SQLEXPRESS` 做為伺服器名稱，然後指定資料庫或資料庫檔案名稱。  
  
## SQL Server Express LocalDB 和 SQL Server Express  
 您可以將服務架構資料庫檔案 \(.mdf\) 加入至 Visual Studio 中的任何專案。  您可以使用 Visual Studio 中的設計工具來設計資料表和其他資料庫物件，也可以執行查詢。  
  
 當您在 Visual Studio 中建立服務架構資料庫時，會使用 SQL Server Express LocalDB 引擎來存取資料庫檔案 \(.mdf\)，舊版 Visual Studio 則使用 SQL Server Express 引擎。  
  
 SQL Server Express LocalDB 是輕量版的 SQL Server，其程式設計方式與 SQL Server 資料庫有許多相同之處。  SQL Server Express LocalDB 會在使用者模式中執行，您可以使用較少必要條件，在沒有組態的情況下更快速地進行安裝。  
  
> [!NOTE]
>  如需 SQL Server Express LocalDB 的詳細資訊，請參閱 Microsoft 網站上的 [LocalDB 簡介 \- 增強的 SQL Express](http://go.microsoft.com/fwlink/?LinkId=234375) 以及 [LocalDB：我的資料庫在哪裡？](http://go.microsoft.com/fwlink/?LinkId=234376)。  
  
 在 Visual Studio 中，您可以依預設使用 SQL Server Express，而不使用 SQL Server Express LocalDB。  在功能表列上選擇 \[**工具**\]、\[**選項**\]。  在 \[**資料庫工具**\] 節點下，選取 \[**資料連接**\]。  在 \[**SQL Server 執行個體名稱**\] 文字方塊中，輸入 `SQLExpress`。  或者，您可以輸入其他值做為 SQL Server 執行個體的名稱 \(例如 `SQL2008`\)。  
  
 下表說明 SQL Server Express LocalDB 與 SQL Server Express 引擎之間的差異。  
  
||SQL Server Express LocalDB|SQL Server Express|  
|-|--------------------------------|------------------------|  
|建立服務架構資料庫時的資料庫類型|在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 和 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 中，是 SQL Server Express LocalDB|在 Visual Studio 2010 \(含\) 以前版本中，是 SQL Server Express|  
|在 \[工具\] \/ \[選項\] 中的 SQL Server 執行個體名稱|\(LocalDB\)\\v11.0|SQLEXPRESS|  
|連接字串中資料來源的值|\(LocalDB\)\\v11.0|.\\SQLEXPRESS|  
|連接字串中 AttachDbFilename 的值|file path|file path|  
|需要使用者執行個體 \(連接字串中 "User Instance\=True"\)|否|是|  
|資料庫檔案的副檔名|.mdf|.mdf|  
  
## SQL Server Express LocalDB 的優點  
  
-   在 SQL Server Express LocalDB 啟用的功能方面，SQL Server Express LocalDB 與服務架構的 SQL Server 版本相容。  在 SQL Server 中，您可以將來自 SQL Server Express LocalDB 的任何資料庫或 Transact\-SQL 程式碼移至 SQL Server 或 SQL Azure，而不需要任何升級步驟。  因此，您可以使用 SQL Server Express LocalDB 來開發以所有 SQL Server 版本為目標的應用程式。  
  
-   SQL Server Express LocalDB 和 SQL Server 的更高階版本支援相同的查詢最佳化工具和查詢處理器。  
  
## 每個專案都包含兩個資料庫複本  
 當您建置專案時，可能會將資料庫檔從根專案資料夾複製到輸出 \(\[**bin**\]\) 資料夾。  這個行為取決於檔案的 \[**複製到輸出目錄**\] 屬性，而該屬性的預設值取決於您所使用的資料庫檔類型。  
  
 若要在 \[**方案總管**\] 中檢視 \[**bin**\] 資料夾，請選擇工具列上的 \[**顯示所有檔案**\] 按鈕。  
  
> [!NOTE]
>  \[**複製到輸出目錄**\] 屬性不會套用到 Web 或 C\+\+ 專案。  
  
 只有當您使用 \[**伺服器總管**\]\/\[**資料庫總管**\] 或其他 [Visual Database Tools](http://msdn.microsoft.com/zh-tw/6b145922-2f00-47db-befc-bf351b4809a1) 編輯資料庫結構描述 \(Database Schema\) 或資料時，才會變更專案根資料夾中的資料庫檔案。  
  
 當您在應用程式開發期間變更資料時，是對 \[**bin**\] 資料夾中的資料庫進行變更。  例如，當您選擇 F5 鍵偵錯應用程式時，便會連接至該資料夾中的資料庫。  
  
|\[**複製到輸出目錄**\] 屬性的值|行為|  
|--------------------------|--------|  
|**有更新時才複製** \(.sdf 檔的預設值\)|在您首次建置專案時，資料庫檔案會從專案目錄複製到 \[**bin**\] 目錄中。  每次您再次建置專案時，都會比較檔案的 \[**修改日期**\] 屬性。  如果專案資料夾中的檔案比較新，它就會複製到 \[**bin**\] 資料夾，取代較舊的檔案。  否則不會複製任何檔案。 **Caution:**  這個值不建議使用於 .mdb 或 .mdf 檔案。  即使資料沒有變更，資料庫檔案也可能會變更。  就算您只是開啟連接而已 \(例如，在 \[**伺服器總管**\] 中展開 \[**資料表**\] 節點\)，檔案就可能會標記為較新的檔案。|  
|**永遠複製** \(.mdf 和 .mdb 檔案的預設值\)|在每次建置應用程式時，都會將資料庫檔案從專案目錄複製到 \[**bin**\] 目錄中。  對輸出資料夾中的資料檔案所做的任何變更，都會在下次執行應用程式時加以覆寫。|  
|**不要複製**|系統絕不會覆寫 \[**bin**\] 目錄中的檔案。  您的應用程式會建立一個動態連接字串，以指向輸出目錄中的資料庫檔案。  因此，如果您要讓輸出目錄中的資料符合專案目錄中的資料，就必須手動將檔案複製到輸出目錄。|  
  
## 本機資料的常見問題  
 下表說明您在使用本機資料檔案時可能會遇到的常見問題。  
  
|問題|說明|  
|--------|--------|  
|每次當我測試應用程式並修改資料後，這些變更在下次執行應用程式時就會消失|\[**複製到輸出目錄**\] 屬性的值是 \[**有更新時才複製**\] 或 \[**永遠複製**\]。  在您每次建置專案時，都會覆寫輸出資料夾中的資料庫 \(測試應用程式時所修改的資料庫\)。  如需詳細資訊，請參閱 [如何：管理專案中的本機資料檔](../data-tools/how-to-manage-local-data-files-in-your-project.md)。|  
|出現一則訊息，表示資料檔已鎖定。|Access \(.mdb 檔\)：確定檔案沒有在其他應用程式中開啟，例如 Access。<br /><br /> SQL Server Express \(.mdf 檔\)：如果您嘗試在 Visual Studio IDE 外部複製、移動或重新命名資料檔，SQL Express 就會將它鎖定。|  
|當一位以上的使用者同時嘗試存取同一個資料庫時，存取遭拒。|Visual Studio 會利用「*使用者執行個體*」\(User Instance\)，這是 SQL Server Express 的一項功能，可為每位使用者建立個別的 SQL Server 執行個體。  在某位使用者存取檔案之後，任何後續的使用者皆無法連接。  例如，如果您嘗試同時在 ASP.NET 程式開發伺服器和 Internet Information Services \(IIS\) 中執行 Web 應用程式，就可能會發生這個問題，因為 IIS 通常是在不同的帳戶下執行。|  
  
## 請參閱  
 [逐步解說：連接至本機資料庫檔案中的資料 \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)   
 [逐步解說：連接至 Access 資料庫中的資料 \(Windows Form\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)