---
title: "CA2100：必須檢視 SQL 查詢中是否有安全性弱點 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Review SQL queries for security vulnerabilities"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
  - "CA2100"
helpviewer_keywords: 
  - "CA2100"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2100：必須檢視 SQL 查詢中是否有安全性弱點
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ReviewSqlQueriesForSecurityVulnerabilities|  
|CheckId|CA2100|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 方法會使用從方法之字串引數所建置的字串，設定 <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> 屬性。  
  
## 規則描述  
 這項規則假設字串引數包含使用者輸入。  從使用者輸入所建置的 SQL 命令字串很容易遭到 SQL 插入 \(SQL Injection\) 攻擊。  在 SQL 插入攻擊中，惡意使用者所提供的輸入會嘗試更改查詢設計，以損壞基礎資料庫或取得未經授權的基礎資料庫存取權限。  典型的技術包括插入一個單引號或所有格符號 \(這是 SQL 常值字串分隔符號\)、雙虛線 \(這表示 SQL 註解\)、分號 \(這表示緊接著新命令\)。  如果使用者輸入必須為查詢的一部分，請使用下列其中一項 \(依照效能的順序列出\) 來減少攻擊的風險。  
  
-   使用預存程序 \(Stored Procedure\)  
  
-   使用參數型命令 \(Parameterized Command\) 字串  
  
-   在建置命令字串之前，驗證使用者輸入的型別和內容。  
  
 下列 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 型別會實作 <xref:System.Data.IDbCommand.CommandText%2A> 屬性，或提供會使用字串引數設定屬性的建構函式。  
  
-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> 和 <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> 和 <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> 和 <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>  
  
-   [System.Data.SqlServerCe.SqlCeCommand](assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&autoUpgrade=True) 和 [System.Data.SqlServerCe.SqlCeDataAdapter](assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&autoUpgrade=True)  
  
-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> 和 <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>  
  
 請注意，當明確或隱含地使用型別的 ToString 方法建構查詢字串時，會違反這項規則。  以下是範例。  
  
```  
int x = 10;  
string query = "SELECT TOP " + x.ToString() + " FROM Table";  
```  
  
 違反此規則的原因是，惡意使用者可以覆寫 ToString\(\) 方法。  
  
 隱含地使用 ToString 時，也會違反此規則：  
  
```  
int x = 10;  
string query = String.Format("SELECT TOP {0} FROM Table", x);  
```  
  
## 如何修正違規  
 若要修正此規則的違規情形，請使用參數型查詢。  
  
## 隱藏警告的時機  
 如果命令文字不包含任何使用者輸入，則可以放心地隱藏這項規則的警告。  
  
## 範例  
 下列範例會顯示違反規則的方法 \(`UnsafeQuery`\)，以及藉由使用參數型命令字串符合規則的方法 \(`SaferQuery`\)。  
  
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-cs[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]  
  
## 請參閱  
 [安全性概觀](../Topic/Security%20Overview2.md)