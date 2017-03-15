---
title: "專案類型的設計決策 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案類型中，專案檔案持續性"
  - "專案類型，承諾機制"
  - "專案類型中，項目"
  - "專案類型，設計決策"
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 專案類型的設計決策
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

建立新的專案類型之前，您必須進行幾種設計決策，有關您的專案類型。  您必須決定要使用何種類型的專案會包含的項目、 如何保留專案檔，及哪一種認可模型。  
  
## 專案項目  
 將您的專案會使用檔案或抽象的物件嗎?  如果您使用的檔案時，他們會參考為基礎或以目錄為基礎的檔案嗎？  是否是本機或遠端檔案或書寫的抽象物件吗？  
  
 在專案中的項目可以是檔案，或者它們可以是更抽象的物件，例如資料庫存放庫 」 或 「 資料連線\] 中的物件，在網際網路上。  如果項目是檔案，專案可以參考為基礎或以目錄為基礎的專案。  
  
 在參考基礎專案中，項目可以出現在多個專案。  不過，實際的項目所表示的檔案位於只看一個目錄中。  在目錄基礎專案中，所有的專案項目會存在於目錄結構中。  如需詳細資訊，請參閱[NIB:Item Management in Projects](http://msdn.microsoft.com/zh-tw/762e606b-7f44-4b66-97a1-e30a703654a0)。  
  
 本機項目會儲存在同一台電腦安裝應用程式的位置。  獨立的伺服器在區域網路或網際網路上其他地方，就可以儲存遠端項目。  
  
## 專案檔案的保存性  
 將資料儲存在通用的一般檔案系統中，或在結構化儲存體中吗？  會使用標準的編輯器中或專案專用編輯器開啟檔案嗎?  
  
 若要保存其資料，大部分的應用程式儲存檔案，其資料\]，然後將之讀取時使用者必須檢視或變更的資訊。  
  
 結構化儲存體，也稱為複合檔案，通常適用於數個元件物件模型 \(COM\) 物件需要將它們的永續性的資料存放在同一個檔案。  結構化儲存體，有幾個不同的軟體元件可以共用單一磁碟的檔案。  
  
 您必須考慮有關您的專案中項目的持續性的數個選項。  您可以執行下列其中一個選項其中之一：  
  
-   它已被變更時，請個別儲存每個檔案。  
  
-   擷取許多交易，在單一**儲存**作業。  
  
-   儲存在本機，再發佈至伺服器，或使用另一種方法來儲存專案項目，當項目都代表資料連線至遠端物件。  
  
 如需有關持續性的詳細資訊，請參閱[專案持續性](../../extensibility/internals/project-persistence.md)和[開啟並儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
## 專案承諾模型  
 將會開啟必要的資料物件中直接模式或交易的模式吗？  
  
 當資料物件以直接的模式開啟時，對資料所做的變更會合併，立即或當使用者以手動方式儲存檔案。  
  
 當資料物件都是使用交易性的模式開啟，時請變更會儲存在記憶體中的暫存位置，以及未認可，直到使用者手動選擇要儲存檔案。  到那個時候，必須同時發生的所有變更，或將會進行任何變更。  
  
## 請參閱  
 [檢查清單︰ 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [NIB:Item Management in Projects](http://msdn.microsoft.com/zh-tw/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [開啟並儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)   
 [專案持續性](../../extensibility/internals/project-persistence.md)   
 [專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md)   
 [專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)   
 [建立專案類型](../../extensibility/internals/creating-project-types.md)