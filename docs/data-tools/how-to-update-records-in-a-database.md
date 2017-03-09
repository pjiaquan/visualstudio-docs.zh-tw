---
title: "如何：更新資料庫中的資料錄 | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "資料庫, 更新"
  - "資料錄, 編輯"
  - "資料錄, 更新"
  - "TableAdapter.Update 方法"
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：更新資料庫中的資料錄
您可以使用 `TableAdapter.Update` 方法更新 \(編輯\) 資料庫中的資料錄。  `TableAdapter.Update` 方法會提供多項多載，以便根據傳入的參數執行不同的作業。  因此，請務必瞭解呼叫這些不同方法簽章的結果。  
  
> [!NOTE]
>  如果您的應用程式並未使用 TableAdapter，您就可以使用命令物件來更新資料庫中的資料錄 \(例如，<xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>\)。  如需使用命令物件更新資料的詳細資訊，請參閱下列「使用命令物件更新資料錄」。  
  
 下表將描述各種 `TableAdapter.Update` 方法的行為：  
  
|方法|描述|  
|--------|--------|  
|`TableAdapter.Update(DataTable)`|嘗試將 <xref:System.Data.DataTable> 中的所有變更儲存至資料庫中   \(這包括移除任何從資料表刪除的資料列、加入已插入資料表的資料列，以及更新資料表中已變更的任何資料列\)。|  
|`TableAdapter.Update(DataSet)`|雖然參數會採用資料集，不過 TableAdapter 會嘗試將 TableAdapter 之關聯 <xref:System.Data.DataTable> 中的所有變更儲存至資料庫中   \(這包括移除任何從資料表刪除的資料列、加入已插入資料表的資料列，以及更新資料表中已變更的任何資料列\)。 **Note:**  TableAdapter 的關聯 <xref:System.Data.DataTable> 就是原先設定 TableAdapter 時所建立的 <xref:System.Data.DataTable>。|  
|`TableAdapter.Update(DataRow)`|嘗試將指定之 <xref:System.Data.DataRow> 中的變更儲存至資料庫中。|  
|`TableAdapter.Update(DataRows())`|嘗試將 <xref:System.Data.DataRow> 陣列中任何資料列的變更儲存至資料庫中。|  
|`TableAdapter.Update("new column values", "original column values")`|嘗試儲存由原始資料行值所識別之單一資料列中的變更。|  
  
 當應用程式以獨佔方式使用資料集來儲存資料時，您通常會使用採用 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或 <xref:System.Data.DataRow> 的 `TableAdapter.Update` 方法。  
  
 當應用程式使用物件來儲存資料時，您通常會使用採用資料行值的 `TableAdapter.Update` 方法。  
  
 如果 TableAdapter 並沒有任何採用資料行值的 `Update` 方法，就是表示此 TableAdapter 是設定成使用預存程序，或者其 `GenerateDBDirectMethods` 屬性設定為 `false`。  請嘗試從 [DataSet 設計工具](../data-tools/creating-and-editing-typed-datasets.md)之內，將 TableAdapter 的 `GenerateDBDirectMethods` 屬性設定為 `true`，然後儲存資料集以重新產生 TableAdapter。  如果 TableAdapter 仍然沒有任何採用資料行值的 `Update` 方法，則此資料表可能無法提供足夠的結構描述資訊，以區別個別的資料列 \(例如，資料表上沒有設定任何主索引鍵\)。  
  
## 使用 TableAdapter 更新現有的資料錄  
 TableAdapter 會根據應用程式的需求，提供不同的方式來更新資料庫中的資料錄。  
  
 如果您的應用程式使用資料集儲存資料，您就只要更新所需 <xref:System.Data.DataTable> 中的資料錄，然後呼叫 `TableAdapter.Update` 方法並傳入 <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow> 或 <xref:System.Data.DataRow> 陣列。  上表說明不同的 `Update` 方法。  
  
#### 若要使用採用 DataSet、DataTable、DataRow 或 DataRows\(\) 的 TableAdapter.Update 方法更新資料庫中的資料錄  
  
1.  請直接在 <xref:System.Data.DataTable> 中編輯 <xref:System.Data.DataRow>，藉以編輯所需之 <xref:System.Data.DataTable> 中的資料錄。  如需詳細資訊，請參閱 [如何：編輯 DataTable 中的資料列](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md)。  
  
2.  在 <xref:System.Data.DataTable> 中編輯資料列之後，請呼叫 `TableAdapter.Update` 方法。  您可以傳入整個 <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow> 的陣列，或是單一 <xref:System.Data.DataRow>，藉以控制要更新的資料量。  
  
     下列程式碼將示範如何編輯 <xref:System.Data.DataTable> 中的資料錄，然後呼叫 `TableAdapter.Update` 方法，將變更儲存至資料庫中   \(此範例會使用 Northwind 資料庫的 Region 資料表\)。  
  
     [!code-vb[VbRaddataSaving#17](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#17](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_1.cs)]  
  
 如果您的應用程式會使用物件在應用程式中儲存資料，您就可以使用 TableAdapter 的 `DBDirect` 方法，直接將物件中的資料傳送至資料庫中。  這些方法可讓您傳遞每個資料行的個別值，做為方法參數。  呼叫這個方法時，就會使用傳入方法的資料行值，更新資料庫中的現有資料錄。  
  
 下列程序會使用 Northwind `Region` 資料表做為範例。  
  
#### 若要使用採用資料行值的 TableAdapter.Update 方法更新資料庫中的資料錄  
  
-   請呼叫 TableAdapter 的 `Update` 方法，並傳入每個資料行的新值和原始值做為參數。  
  
    > [!NOTE]
    >  如果您沒有可用的執行個體，請針對您想使用的 TableAdapter 執行個體化。  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_2.cs)]  
  
## 使用命令物件更新資料錄  
 下列範例會使用命令物件，直接更新資料庫中的現有資料錄。  如需使用命令物件來執行命令和預存程序 \(Stored Procedure\) 的詳細資訊，請參閱[將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)。  
  
 下列程序會使用 Northwind `Region` 資料表做為範例。  
  
#### 若要使用命令物件更新資料庫中的現有資料錄  
  
-   請建立新的命令物件、設定其 `Connection`、`CommandType` 和 `CommandText` 屬性，然後開啟連接並執行命令。  
  
     [!code-vb[VbRaddataSaving#19](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#19](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_3.cs)]  
  
## .NET Framework 安全性  
 您必須擁有嘗試連接之資料庫的存取權，以及在所需資料表中更新資料錄的使用權限。  
  
## 請參閱  
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [如何：刪除資料庫中的資料錄](../Topic/How%20to:%20Delete%20Records%20in%20a%20Database.md)   
 [如何：在資料庫中插入新的資料錄](../data-tools/insert-new-records-into-a-database.md)   
 [如何：從物件中將資料儲存至資料庫](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Visual Studio 資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)