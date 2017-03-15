---
title: "如何：連接到 Northwind 資料庫 | Microsoft Docs"
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
  - "連接 [Visual Studio], Northwind 資料庫"
  - "Northwind 範例資料庫"
ms.assetid: cc6cb79f-d035-41f8-b398-8d4a45922bfb
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：連接到 Northwind 資料庫
由於您學習如何使用 Visual Studio 建立資料庫應用程式，所以需要連接 Northwind 資料庫以遵循該產品文件中的許多範例進行。  根據所遵循的範例，您將連接至 SQL Server 或資料庫檔案 \(例如 Microsoft Access 或 SQL Server 的資料庫檔案\) 中的資料庫。  
  
## 建立與 Northwind 資料庫的資料連接  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### 建立與 Northwind 資料庫的資料連接 \(SQL Server\)  
  
1.  在 \[檢視\] 功能表上，選擇 \[伺服器總管\]\/\[資料庫總管\]。  
  
2.  在 \[伺服器總管\]\/\[資料庫總管\] 中，開啟 \[資料連接\] 的捷徑功能表，然後選擇 \[加入連接\]。  
  
     在您選擇 \[加入連接\] 之後，將會出現 \[選擇資料來源\] 對話方塊或 \[加入連接\] 對話方塊。  
  
3.  如果出現 \[選擇資料來源\] 對話方塊，請選取 \[Microsoft SQL Server\]，然後選擇 \[確定\]。  
  
     如果出現 \[加入連接\] 對話方塊，而且 \[資料來源\] 不是 \[Microsoft SQL Server \(SqlClient\)\]，則請選擇 \[變更\] 按鈕開啟 \[變更資料來源\] 對話方塊，並選取 \[Microsoft SQL Server\]，然後選擇 \[確定\] 按鈕。  
  
4.  在 \[伺服器名稱\] 清單中，指定 Northwind 資料庫所在的伺服器名稱。  
  
5.  根據 SQL Server 和 Northwind 資料庫版本的需求，選擇 \[使用 Windows 驗證\]，或是選擇 \[使用 SQL Server 驗證\]，並輸入使用者名稱和密碼以登入執行 SQL Server 的電腦。  
  
6.  在 \[選取或輸入資料庫名稱\] 清單中，選擇 Northwind 資料庫。  
  
7.  選擇 \[測試連接\]，確認與 Northwind 資料庫的連接性。  
  
8.  選擇 \[**確定**\]。  
  
     與 Northwind 資料庫的資料連接會加入至 \[伺服器總管\]\/\[資料庫總管\]。  
  
 除了連接至 SQL Server 資料庫的遠端執行個體之外，您也可以直接連接至含有資料庫的實際檔案。  這可讓您將資料庫檔案直接加入至可將它們部署為應用程式一部分的專案。  下列是目前支援的本機資料庫檔案：SQL Server Compact 資料庫檔案 \(.sdf\)、[!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 和 SQL Server Express 資料庫檔案 \(.mdf\)，以及 Microsoft Access 資料庫檔案 \(.mdb 或 .accdb\)。  
  
#### 建立與 Northwind 資料庫的資料連接 \(SQL Server 資料庫檔案 \(.mdf\)\)  
  
1.  在 \[檢視\] 功能表上，選擇 \[伺服器總管\]\/\[資料庫總管\]。  
  
2.  在 \[伺服器總管\]\/\[資料庫總管\] 中，開啟 \[資料連接\] 的捷徑功能表，然後選擇 \[加入連接\]。  
  
     在您選擇 \[加入連接\] 之後，將會出現 \[加入連接\] 對話方塊或 \[選擇資料來源\] 對話方塊。  
  
3.  如果出現 \[選擇資料來源\] 對話方塊，請選取 \[Microsoft SQL Server 資料庫檔案\]，然後選取 \[確定\]。  
  
4.  如果出現 \[加入連接\] 對話方塊，請確認 \[資料來源\] 設定為 \[Microsoft SQL Server 資料庫檔案 \(SqlClient\)\]。  如果未設定為 \[Microsoft SQL Server 資料庫檔案 \(SqlClient\)\]，請選擇 \[變更\] 開啟 \[變更資料來源\] 對話方塊，並選擇 \[Microsoft SQL Server 資料庫檔案\]，然後選擇 \[確定\] 按鈕。  
  
5.  選擇 \[瀏覽\] 找到含有 Northwind 資料庫的 .mdf 檔案。  
  
6.  根據 Northwind 資料庫版本的需求，選擇 \[使用 Windows 驗證\]，或是選擇 \[SQL Server 驗證\]，並輸入使用者名稱和密碼以登入執行 SQL Server 的電腦。  
  
7.  選擇 \[**確定**\] 按鈕。  
  
     與 Northwind 資料庫的資料連接會加入至 \[伺服器總管\]\/\[資料庫總管\]。  
  
> [!NOTE]
>  [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 具有適用於 Northwind 資料庫檔案 \(.mdf\) 的變更。  如需詳細資訊，請參閱[如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
#### 若要建立資料連接至 Northwind 資料庫 \- Access 資料庫檔案 \(.mdb 或 .accdb\)  
  
1.  在 \[檢視\] 功能表上，選擇 \[伺服器總管\]\/\[資料庫總管\]。  
  
2.  在 \[伺服器總管\]\/\[資料庫總管\] 中，開啟 \[資料連接\] 的捷徑功能表，然後選擇 \[加入連接\]。  
  
     在您選擇 \[加入連接\] 之後，將會出現 \[加入連接\] 對話方塊或 \[選擇資料來源\] 對話方塊。  
  
3.  如果出現 \[選擇資料來源\] 對話方塊，請選取 \[Microsoft Access 資料庫檔案\]，然後選擇 \[確定\]。  
  
4.  如果出現 \[加入連接\] 對話方塊，請確認 \[資料來源\] 設定為 \[Microsoft Access 資料庫檔案\]。  如果未設定為 \[Microsoft Access 資料庫檔案\]，請選擇 \[變更\] 開啟 \[變更資料來源\] 對話方塊，並選擇 \[Microsoft Access 資料庫檔案\]，然後選擇 \[確定\] 按鈕。  
  
5.  選擇 \[瀏覽\] 找到含有 Northwind 資料庫的 .mdb 或 .accdb 檔案。  
  
6.  如果您的 Northwind 資料庫版本需要使用者名稱和密碼，則請予以輸入。  
  
7.  選擇 \[**確定**\]。  
  
     與 Northwind 資料庫的資料連接會加入至 \[伺服器總管\]\/\[資料庫總管\]。  
  
## 請參閱  
 [如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)   
 [Microsoft Access 2010 的資料程式設計](http://msdn.microsoft.com/library/office/ff965871.aspx)   
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)