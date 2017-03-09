---
title: "如何：在資料庫中插入新的資料錄 | Microsoft Docs"
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
  - "資料 [Visual Studio], 儲存"
  - "資料庫, 將新資料錄插入到"
  - "資料錄, 插入"
  - "儲存資料"
  - "TableAdapter, 將新資料錄插入到"
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在資料庫中插入新的資料錄
若要在資料庫中插入新的資料錄，您可以使用 `TableAdapter.Update` 方法，或其中一個 TableAdapter 的 DBDirect 方法 \(尤其是 `TableAdapter.Insert` 方法\)。  如需詳細資訊，請參閱 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)。  
  
 如果您的應用程式並未使用 TableAdapter，您就可以使用命令物件來進行互動並在資料庫中插入新的資料錄 \(例如，<xref:System.Data.SqlClient.SqlCommand>\)。  
  
 當您的應用程式使用資料集儲存資料時，請使用 `TableAdapter.Update` 方法。  `Update` 方法會將所有變更 \(更新、插入和刪除\) 傳送至資料庫中。  
  
 當您的應用程式使用物件儲存資料，或是您想要更精密地控制在資料庫中建立新資料錄的方式時，請使用 `TableAdapter.Insert` 方法。  
  
 如果 TableAdapter 並沒有任何 `Insert` 方法，就是表示此 TableAdapter 是設定成使用預存程序，或者其 `GenerateDBDirectMethods` 屬性設定為 `false`。  請嘗試從 [DataSet 設計工具](../data-tools/creating-and-editing-typed-datasets.md)之內，將 TableAdapter 的 `GenerateDBDirectMethods` 屬性設定為 `true`，然後儲存資料集以重新產生 TableAdapter。  如果 TableAdapter 仍然沒有 `Insert` 方法，則此資料表可能無法提供足夠的結構描述資訊，以區別個別的資料列 \(例如，資料表上沒有設定任何主索引鍵\)。  
  
## 使用 TableAdapter 插入新的資料錄  
 TableAdapter 會根據應用程式的需求，提供不同的方式來將新資料錄插入資料庫中。  
  
 如果您的應用程式使用資料集儲存資料，您就只要在資料集中將新資料錄加入至所需的 <xref:System.Data.DataTable>，然後呼叫 `TableAdapter.Update` 方法即可。  `TableAdapter.Update` 方法會採用 <xref:System.Data.DataTable> 中的任何變更，並將這些變更傳送至資料庫中 \(包括已修改和已刪除的資料錄\)。  
  
#### 若要使用 TableAdapter.Update 方法將新資料錄插入資料庫中  
  
1.  將新資料錄加入至所需的 <xref:System.Data.DataTable>，方法是建立新的 <xref:System.Data.DataRow> 並將它加入至 <xref:System.Data.DataTable.Rows%2A> 集合中。  如需詳細資訊，請參閱 [如何：將資料列加入至 DataTable](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md)。  
  
2.  將新資料列加入至 <xref:System.Data.DataTable> 之後，請呼叫 `TableAdapter.Update` 方法。  您可以傳入整個 <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow> 的陣列，或是單一 <xref:System.Data.DataRow>，藉以控制要更新的資料量。  
  
     下列程式碼將示範如何將新資料錄加入至 <xref:System.Data.DataTable>，然後呼叫 `TableAdapter.Update` 方法，將新資料列儲存至資料庫中   \(此範例會使用 Northwind 資料庫的 `Region` 資料表\)。  
  
     [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]  
  
 如果您的應用程式會使用物件在應用程式中儲存資料，您就可以使用 `TableAdapter.Insert` 方法，直接在資料庫中建立新的資料列。  `Insert` 方法會接受每個資料行的個別值做為參數。  當您呼叫此方法時，就會使用傳入的參數值，將新的資料錄插入資料庫中。  
  
 下列程序會使用 Northwind 資料庫的 `Region` 資料表做為範例。  
  
#### 若要使用 TableAdapter.Insert 方法將新資料錄插入資料庫中  
  
-   請呼叫 TableAdapter 的 `Insert` 方法，並傳入每個資料行的值做為參數。  
  
    > [!NOTE]
    >  如果您沒有可用的執行個體，請針對您想使用的 TableAdapter 執行個體化。  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]  
  
## 使用命令物件插入新資料錄  
 下列範例會使用命令物件，直接將資料錄插入資料庫中。  如需使用命令物件來執行命令和預存程序 \(Stored Procedure\) 的詳細資訊，請參閱[將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)。  
  
 下列程序會使用 Northwind 資料庫的 `Region` 資料表做為範例。  
  
#### 若要使用命令物件將新資料錄插入資料庫中  
  
-   建立新的命令物件，然後設定其 `Connection`、`CommandType` 和 `CommandText` 屬性。  
  
     [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]  
  
## .NET Framework 安全性  
 您必須擁有嘗試連接之資料庫的存取權，以及在所需資料表中執行插入的使用權限。  
  
## 請參閱  
 [如何：刪除資料庫中的資料錄](../Topic/How%20to:%20Delete%20Records%20in%20a%20Database.md)   
 [如何：更新資料庫中的資料錄](../data-tools/how-to-update-records-in-a-database.md)   
 [如何：從物件中將資料儲存至資料庫](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Visual Studio 資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)   
 [擷取 Identity 或 Autonumber 值](../Topic/Retrieving%20Identity%20or%20Autonumber%20Values.md)