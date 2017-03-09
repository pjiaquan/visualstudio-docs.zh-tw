---
title: "如何：安裝範例資料庫 | Microsoft Docs"
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
  - "Adventure Works 範例資料庫"
  - "資料 [Visual Studio], 範例資料庫"
  - "Northwind 範例資料庫"
  - "範例資料庫, Adventure Works"
  - "範例資料庫, Northwind"
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
caps.handback.revision: 56
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：安裝範例資料庫
許多資料範例都必須能夠連接到 Northwind、Pubs 和 AdventureWorks 範例資料庫。  您可以使用下列程序來安裝及連接至這些資料庫。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 安裝資料庫  
 許多資料範例都必須使用可從網站下載的範例資料庫。  這些範例資料庫包括 AdventureWorks、Northwind 和 Pubs 資料庫。  
  
#### 若要安裝 SQL Server 適用的 Northwind 和 Pubs 範例資料庫  
  
1.  請移至 [Northwind 和 Pubs 範例資料庫](http://go.microsoft.com/fwlink?linkid=64296)網站。  
  
2.  下載並執行安裝程式。  
  
     安裝程式會在電腦的根資料夾中新增 \[**SQL Server 2000 Sample Databases**\] 資料夾   \(例如：**C:\\SQL Server 2000 Sample Databases**\)。  
  
3.  找出您要的資料庫 \(Northwind 或 Pubs\) 的 SQL 指令碼。  
  
    > [!WARNING]
    >  .MDF 資料庫檔案無法輕易地轉換成您在目前 SQL Server 版本中可以使用的格式，因此，最好是使用指令碼來建立資料庫。  
  
4.  在 \[**伺服器總管**\] 中，建立與您要安裝資料庫的 SQL Server 執行個體的連接。  如果您沒有想要使用的特定 SQL Server，您可以使用自動與 Visual Studio 一起安裝的資料庫。  若要這樣做，請指定 `(localdb)\v11.0` 做為伺服器名稱。  
  
     依照下列步驟來建立連接。  
  
    ###### 若要建立與 SQL Server 執行個體的連接  
  
    1.  在 \[**伺服器總管**\] 中，開啟 \[**資料連線**\] 節點的捷徑功能表，然後選擇 \[**加入連接**\]。  
  
         \[**加入連接**\] 對話方塊隨即出現。  
  
    2.  輸入您要在其中建立 Northwind 或 Pubs 資料庫的 SQL Server 的名稱，或輸入 \(localdb\)\\v11.0。  
  
    3.  在 \[**選取或輸入資料庫名稱**\] 下方，從清單中選擇任何資料庫 \(例如，tempdb\)。  
  
    4.  選擇 \[**測試連接**\] 按鈕以確認一切運作正常，然後選擇 \[**確定**\] 按鈕。  
  
         新的連接節點隨即出現在 \[**伺服器總管**\] 中。  
  
5.  在您的伺服器連接節點的捷徑功能表上，選擇 \[**新增查詢**\] 按鈕。  
  
     編輯器視窗隨即開啟並顯示空的 .sql 指令碼檔。  
  
6.  將 instnwnd.sql 或 instpubs.sql 的內容貼到編輯器視窗中。  
  
7.  選擇 \[執行查詢\] 按鈕 \(查詢視窗右上方的開啟綠色三角形圖示\)。  
  
     如果查詢成功，則會出現 \[已成功完成命令\] 訊息。  這表示已建立 Northwind 或 pubs 資料庫。  
  
     您還是需要新增連線至範例資料庫。  在 \[伺服器總管\] 中，開啟 \[資料連線\] 節點的捷徑功能表，然後選擇 \[新增連線\]。  
  
8.  選擇您先前選擇的相同資料庫伺服器，但是，這次請在 \[選取或輸入資料庫名稱\] 下選擇 Northwind 或 pubs 資料庫，然後選擇 \[確定\] 按鈕。  
  
     在 \[資料連線\] 下，會出現範例資料庫的新節點。  
  
9. 關閉編輯器視窗，並確認您不要儲存查詢檔案。  建立資料庫之後，並不需要儲存資料庫建立指令碼。  
  
#### 若要安裝 AdventureWorks 範例資料庫  
  
-   您可以從 [CodePlex 網站](http://go.microsoft.com/fwlink/?linkid=87843)下載 AdventureWorks 範例資料庫。  
  
#### 若要安裝 Microsoft Access 適用的 Northwind 範例資料庫  
  
1.  在 Microsoft Access 2010 或更新版本中，於線上範本中搜尋 Northwind，然後選擇 \[Desktop Northwind 2007 範例資料庫\]。  
  
2.  在 Microsoft Access 中，將資料庫檔案儲存為 Northwind.accdb。  
  
 新的 Access 資料庫副檔名為 .accdb。  請參閱[使用 Access 2010 進行資料程式設計](http://msdn.microsoft.com/library/office/ff965871.aspx)。  若要使用 Access 連接到 Northwind 資料庫，請參閱[如何：連接到 Northwind 資料庫](../data-tools/how-to-connect-to-the-northwind-database.md)。  
  
## .NET Framework 安全性  
 範例資料庫是僅供說明使用，不一定會示範最佳安全性作法。  
  
## 請參閱  
 [如何判斷 SQL Server 的版本及其元件](http://support.microsoft.com/kb/321185)   
 [逐步解說：在 Visual Studio 中建立本機資料庫檔案](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [如何：連接到 Northwind 資料庫](../data-tools/how-to-connect-to-the-northwind-database.md)