---
title: "如何：使用異動儲存資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "資料 [Visual Studio], 儲存"
  - "儲存資料, 使用異動"
  - "System.Transactions 命名空間"
  - "異動, 儲存資料"
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用異動儲存資料
您可以使用 <xref:System.Transactions> 命名空間 \(Namespace\)，在交易中儲存資料。  請使用 <xref:System.Transactions.TransactionScope> 物件，加入自動為您管理的交易。  
  
 由於專案建立時並沒有 System.Transactions 組件的參考，所以您必須在使用交易的專案中手動加入參考。  
  
> [!NOTE]
>  Windows 2000 \(含\) 以後版本才支援 <xref:System.Transactions> 命名空間。  
  
 實作交易最簡單的方式就是在 `using` 陳述式中具現化 <xref:System.Transactions.TransactionScope> 物件   \(如需詳細資訊，請參閱 [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement) 和 [Using 陳述式](/dotnet/csharp/language-reference/keywords/using-statement)\)。 在 `using` 陳述式中執行的程式碼將會加入交易。  
  
 若要認可交易，請呼叫 <xref:System.Transactions.TransactionScope.Complete%2A> 方法，做為 using 區塊中的最後一項陳述式。  
  
 若要復原交易，請在呼叫 <xref:System.Transactions.TransactionScope.Complete%2A> 方法以前，擲回例外狀況。  
  
 如需詳細資訊，請參閱 [逐步解說：在異動中儲存資料](../data-tools/save-data-in-a-transaction.md)。  
  
### 若要加入 System.Transactions dll 的參考  
  
1.  在 \[**專案**\] 功能表中選擇 \[**加入參考**\]。  
  
2.  選取 \[**.NET**\] 索引標籤中的 \[**System.Transactions**\] \(SQL Server 專案則為 \[**SQL Server**\] 索引標籤\)，然後按一下 \[**確定**\]。  
  
     System.Transactions.dll 的參考就會加入專案中。  
  
### 若要在交易中儲存資料  
  
-   加入程式碼，以便在含有交易的 using 陳述式中儲存資料。  下列程式碼將示範如何在 using 陳述式中，建立並具現化 <xref:System.Transactions.TransactionScope> 物件：  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## 請參閱  
 [逐步解說：在異動中儲存資料](../data-tools/save-data-in-a-transaction.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio 資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)