---
title: "使用多層式架構應用程式中的資料集 | Microsoft Docs"
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
  - "資料 [Visual Basic], N-Tier 應用程式"
  - "資料集專案 [VS N-Tier 應用程式]"
  - "資料集 [Visual Basic], N-Tier 應用程式"
  - "分散式應用程式 [VS N-Tier 應用程式]"
  - "多層應用程式"
  - "多層資料庫應用程式"
  - "N-Tier 應用程式"
  - "TableAdapter, N-Tier 應用程式"
  - "層, N-Tier 應用程式"
  - "具類型資料集, N-Tier 應用程式"
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用多層式架構應用程式中的資料集
*「多層式架構資料應用程式」*\(N\-tier data application\) 是以資料為主而且分成多個邏輯層 \(或*「層級」*\(tier\)\) 的應用程式。  換句話說，多層式架構資料應用程式是分成多個專案的應用程式，而其專屬專案中各有資料存取層、商務邏輯層和呈現層。  如需詳細資訊，請參閱[多層式架構資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)。  
  
 具類型資料集已獲增強，因此可將 TableAdapter 和資料集類別產生為離散專案。  這提供快速分隔應用程式層以及產生多層式架構資料應用程式的能力。  
  
 具類型資料集中的多層式架構支援會將應用程式架構的反覆開發啟用為多層式架構設計，並移除手動將程式碼分隔為多個專案的需求。  請使用[建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)開始設計資料層。  當您準備好採用應用程式架構進行多層式架構設計時，請設定資料集的 \[資料集專案\] 屬性，以將資料集類別產生為不同的專案。  
  
## 在本節中  
 [如何：將資料集和 TableAdapters 分成不同的專案](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 描述如何將產生的資料集類別移出含有產生的 TableAdapter 類別的專案，以及產生為新的專案。  
  
 [如何：將程式碼加入 N\-Tier 應用程式中的 TableAdapters](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 描述如何產生部分類別，而使用部分類別可以加入多層式架構 TableAdapter 的程式碼。  
  
 [如何：將程式碼加入 N\-Tier 應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 描述如何產生部分類別，而使用部分類別可以加入多層式架構資料集的程式碼。  
  
 [如何：將驗證加入 N\-Tier 資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 描述在何處加入程式碼，以執行資料變更驗證。  
  
 [逐步解說：建立 N\-Tier 資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 提供用於建立具類型資料集以及將 TableAdapter 和資料集程式碼分成多個專案的逐步指示。  
  
 [逐步解說：將驗證加入至 N\-Tier 資料應用程式](../Topic/Walkthrough:%20Adding%20Validation%20to%20an%20N-Tier%20Data%20Application.md)  
 提供用於加入多層式架構資料應用程式逐步解說中所建立應用程式的驗證的逐步指示。  
  
## 參考  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## 相關章節  
 [多層式架構資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)  
  
 [階層式更新](../data-tools/hierarchical-update.md)  
  
 [使用 Visual Studio 中的資料集](../data-tools/dataset-tools-in-visual-studio.md)  
  
 [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)  
  
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)  
  
 [使用 LINQ to SQL 的 N\-Tier 和遠端應用程式](../Topic/N-Tier%20and%20Remote%20Applications%20with%20LINQ%20to%20SQL.md)