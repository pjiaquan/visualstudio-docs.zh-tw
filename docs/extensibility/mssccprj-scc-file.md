---
title: "MSSCCPRJ。SCC 檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原始檔控制外掛程式，MSSCCPRJ。SCC 檔案"
  - "MSSCCPRJ。SCC 檔案"
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# MSSCCPRJ。SCC 檔案
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當 Visual Studio 方案或專案放置在 IDE 中使用的原始檔控制時，IDE 會從原始檔控制外掛程式的字串形式接收兩個關鍵的資訊。 這些字串 「 AuxPath 」 和 「 ProjName 」，是不透明的 ide，但在版本控制中找出方案或專案所使用的外掛程式。 IDE 經常取得這些字串第一次呼叫 [SccGetProjPath](../extensibility/sccgetprojpath-function.md), ，它然後未來呼叫的方案或專案檔中儲存 [SccOpenProject](../extensibility/sccopenproject-function.md)。 內嵌在方案和專案檔時，「 AuxPath 」 和 「 ProjName 」 字串不會自動更新使用者的分支，分岔，或複製在版本控制的方案和專案檔。 若要確定方案和專案檔會指向其版本控制中的正確位置，使用者必須手動更新字串。 字串的僅限不透明，因為它不一定清楚如何更新。  
  
 原始檔控制外掛程式可以避免這個問題 「 AuxPath 」 和 「 ProjName 」 字串儲存在稱為 MSSCCPRJ 的特殊檔案。SCC 檔案。 這是本機的用戶端的檔案所擁有及維護的外掛程式。 這個檔案從未開出原始檔控制下，但是會產生由外掛程式中針對每個包含原始檔控制檔案的目錄。 若要判斷哪些檔案是 Visual Studio 方案和專案檔，原始檔控制外掛程式可以比較檔案的副檔名會針對標準或使用者提供的清單。 一旦 IDE 偵測到的外掛程式支援 MSSCCPRJ。SCC 檔案，它就內嵌 「 AuxPath 」 和 「 ProjName 」 字串至方案和專案檔，它會從 MSSCCPRJ 讀取這些字串。SCC 檔案。  
  
 原始檔控制外掛程式支援 MSSCCPRJ。SCC 檔案必須遵守下列指導方針:  
  
-   只能有一個 MSSCCPRJ。SCC 檔案的每個目錄。  
  
-   MSSCCPRJ。SCC 檔案可包含的 「 AuxPath 」 和 「 ProjName 」 的指定目錄內的原始檔控制下的多個檔案。  
  
-   「 AuxPath 」 字串的長度不能引號內。 它可包含雙引號括住做為分隔符號 \(例如，雙引號括住一組可用來表示空字串\)。 從 MSSCCPRJ 讀取時，IDE 會帶狀所有從 「 AuxPath 」 字串的引號。SCC 檔案。  
  
-   MSSCCPRJ"ProjName"字串。SCC 檔案必須符合傳回的字串 `SccGetProjPath` 函式。 如果函式所傳回的字串括住它 MSSCCPRJ 中的字串。SCC 檔案必須具有引號括住，反之亦然。  
  
-   MSSCCPRJ。SCC 檔案建立或更新的檔案會放置在原始檔控制。  
  
-   如果 MSSCCPRJ。SCC 檔案會被刪除，提供者應該重新執行原始檔控制作業，有關該目錄下一次產生它。  
  
-   MSSCCPRJ。SCC 檔案必須嚴格遵守定義的格式。  
  
## MSSCCPRJ 的圖例。SCC 檔案格式  
 以下是 MSSCCPRJ 的範例。SCC 檔案格式 \(行號，才會提供做為指南，和不應該包含在檔案內文\):  
  
 \[第 1 行\] `SCC = This is a Source Code Control file`  
  
 \[第 2 行\]  
  
 \[第 3 行\] `[TestApp.sln]`  
  
 \[第 4 行\] `SCC_Aux_Path = "\\server\vss\"`  
  
 \[第 5 行\] `SCC_Project_Name = "$/TestApp"`  
  
 \[第 6 行\]  
  
 \[列 7\] `[TestApp.csproj]`  
  
 \[第 8\] `SCC_Aux_Path = "\\server\vss\"`  
  
 \[第 9 行\] `SCC_Project_Name = "$/TestApp"`  
  
 第一行指出檔案的用途，並做為此類型的所有檔案的簽章。 這一行應該會出現這所有 MSSCCPRJ 中一樣。SCC 檔案:  
  
 `SCC = This is a Source Code Control file`  
  
 接下來是設定為每個檔案，方括號中的檔案名稱來標記的區段。 此區段會追蹤每個檔案重複。 這一行是範例檔案名稱，也就是 `[TestApp.csproj]`。 IDE 必須要有下列兩行。 它不會不過，定義的樣式定義的值。 變數是 `SCC_Aux_Path` 和 `SCC_Project_Name`。  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 沒有任何結尾分隔符號至這個區段。 Scc.h 標頭檔中定義的檔案，以及出現在檔案中的所有常值名稱。 如需詳細資訊，請參閱[使用做為索引鍵來尋找原始檔控制外掛程式的字串](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)。  
  
## 請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [使用做為索引鍵來尋找原始檔控制外掛程式的字串](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)