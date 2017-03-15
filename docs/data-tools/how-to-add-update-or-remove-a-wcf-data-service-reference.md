---
title: "How to: Add, Update, or Remove a WCF Data Service Reference | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service references [Visual Studio]"
  - "WCF Data Service reference"
  - "WCF data service references"
  - "ADO.NET service references"
  - "ADO.NET Data Service reference"
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Add, Update, or Remove a WCF Data Service Reference
「*服務參考*」\(Service Reference\) 能讓專案存取一個或多個 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]。  您可以使用 \[**加入服務參考**\] 對話方塊，在本機、區域網路或網際網路上搜尋目前方案中的 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 加入服務參考  
  
#### 若要加入外部服務的參考  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下要在其中加入此服務之專案的名稱，然後按一下 \[**加入服務參考**\]。  
  
     \[**加入服務參考**\] 對話方塊隨即出現。  
  
2.  在 \[**位址**\] 方塊中，輸入服務的 URL，然後按一下 \[**移至**\] 搜尋服務。  如果服務會實作使用者名稱和密碼安全性，系統可能會提示您輸入使用者名稱和密碼。  
  
    > [!NOTE]
    >  您只應參考受信任來源的服務。  加入不受信任來源的參考可能會危害安全性。  
  
     您也可以從 \[**位址**\] 清單中選取 URL，這個清單中儲存了先前找到有效服務中繼資料的 15 個 URL。  
  
     執行搜尋的同時，會顯示進度列。  您可以隨時按一下 \[**停止**\] 停止搜尋。  
  
3.  在 \[**服務**\] 清單中，展開您要使用之服務的節點，並選取實體集。  
  
4.  在 \[**命名空間**\] 方塊中，輸入要用於參考的命名空間。  
  
5.  按一下 \[**確定**\] 將參考加入至專案。  
  
     服務用戶端 \(Proxy\) 隨即產生，而且描述服務的中繼資料會加入至 app.config 檔案中。  
  
#### 若要在目前方案中加入服務的參考  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下要在其中加入此服務之專案的名稱，然後按一下 \[**加入服務參考**\]。  
  
     \[**加入服務參考**\] 對話方塊隨即出現。  
  
2.  按一下 \[**探索**\]。  
  
     目前方案中的所有服務 \([!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 和 WCF 服務\)，都會加入至 \[**服務**\] 清單。  
  
3.  在 \[**服務**\] 清單中，展開您要使用之服務的節點，並選取實體集。  
  
4.  在 \[**命名空間**\] 方塊中，輸入要用於參考的命名空間。  
  
5.  按一下 \[**確定**\] 將參考加入至專案。  
  
     服務用戶端 \(Proxy\) 隨即產生，而且描述服務的中繼資料會加入至 app.config 檔案中。  
  
## 更新服務參考  
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 的實體資料模型有時候會變更。  發生變更時，必須更新服務參考。  
  
#### 若要更新服務參考  
  
-   在 \[**方案總管**\] 中，以滑鼠右鍵按一下服務參考，然後按一下 \[**更新服務參考**\]。  
  
     從原始位置更新參考的同時，會顯示進度對話方塊，而且會重新產生服務用戶端以反映中繼資料中的任何變更。  
  
## 移除服務參考  
 如果服務參考已不再使用，您可以從方案中移除它。  
  
#### 若要移除服務參考  
  
-   在 \[**方案總管**\] 中，以滑鼠右鍵按一下服務參考，然後按一下 \[**刪除**\]。  
  
     服務用戶端會從方案中移除，而且描述服務的中繼資料也會從 app.config 檔案中移除。  
  
    > [!NOTE]
    >  任何會參考服務參考的程式碼都必須手動移除。  
  
## 請參閱  
 [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)