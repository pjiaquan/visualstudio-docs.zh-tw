---
title: "此連接字串包含具有純文字密碼的認證，而且未使用整合式安全性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 此連接字串包含具有純文字密碼的認證，而且未使用整合式安全性
是否要將連接字串連同這些機密資訊一起儲存到目前的 DBML 檔案和應用程式組態檔？按 \[否\] 會只儲存連接字串，不會儲存敏感資訊。  
  
 使用內含敏感資訊 \(含在連接字串中的密碼\) 的資料連接時，可以選擇是否在將連接字串儲存至專案的 DBML 檔案和應用程式組態檔時包含敏感資訊。  
  
> [!WARNING]
>  將 \[**連接**\] 屬性的 \[**應用程式設定**\] 屬性明確設定為 \[**False**\]，會將密碼加入到 DBML 檔案中。  
  
### 若要將連接字串連同敏感資訊一起儲存到專案的應用程式設定中  
  
-   按一下 \[**是**\]。  
  
     連接字串會儲存為應用程式設定。連接字串會包含純文字的敏感資訊。DBML 檔案不包含敏感資訊。  
  
### 若要將連接字串儲存到專案的應用程式設定中，但不儲存敏感資訊  
  
-   按一下 \[**否**\]。  
  
     連接字串會儲存為應用程式設定，但是不包含密碼。  
  
## 請參閱  
 [物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)