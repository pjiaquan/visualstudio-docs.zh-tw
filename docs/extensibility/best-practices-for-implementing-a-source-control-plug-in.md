---
title: "實作原始檔控制外掛程式的最佳作法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原始檔控制外掛程式，最佳作法"
  - "最佳作法，原始檔控制外掛程式"
  - "原始檔控制 [Visual Studio SDK] 外掛程式"
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 實作原始檔控制外掛程式的最佳作法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

下列技術詳細資料可協助您可靠地實作原始檔控制外掛程式 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## 記憶體管理問題  
 在大部分情況下，整合式的開發環境 \(IDE\)，也就是呼叫者，會釋放，並會配置記憶體。 原始檔控制外掛程式傳回呼叫端配置的緩衝區中的字串和其他項目。 例外狀況會記錄在其發生的特定函數的描述。  
  
## 檔案名稱的陣列  
 當傳遞的檔案陣列時，它不會傳遞為連續的檔案名稱陣列。 檔案名稱，它會傳遞做為陣列的指標。 例如，在 [SccGet](../extensibility/sccget-function.md), ，檔案名稱傳遞的 `lpFileNames` 參數，其中 `lpFileNames` 實際上是指向 `char **`。`lpFileNames`\[0\] 是指向第一個名稱， `lpFileNames`\[1\] 是指向第二個名稱，等等。  
  
## 大型模型  
 所有指標都是 32 位元，即使是在 16 位元作業系統上。  
  
## 完整的路徑  
 其中的檔案名稱或目錄指定做為引數，它們必須是完整的路徑或 UNC 路徑，不包含結束的反斜線。 它是原始檔控制外掛程式，以便在轉譯為相對路徑，如果也就是基礎的原始檔控制系統需求的責任。  
  
## 指定完整的路徑註冊 dll  
 IDE 會從相對路徑 \(例如，.\\NewProvider.dll\)，不會再載入 Dll。 必須指定 DLL 的完整路徑 \(例如 C:\\Providers\\NewProvider.dll\)。 這項需求可加強安全性的 IDE，藉由防止未經授權或模擬原始檔控制 Dll 的載入。  
  
## 當您安裝原始檔控制外掛程式時檢查現有 VSSCI 外掛程式  
 若要安裝您的原始檔控制外掛程式計劃的使用者可能已經有現有原始檔控制外掛程式安裝在電腦上。 \(安裝程式\) 安裝程式外掛程式，您建立應該判斷是否有相關的登錄機碼的現有值。 如果已經設定這些機碼，您的安裝程式應該詢問使用者是否為預設原始檔控制外掛程式註冊您的外掛程式，並取代已安裝。  
  
## 錯誤結果碼和報告  
 `SCC_OK` 傳回原始檔控制函式程式碼表示作業已成功的所有檔案。 如果作業失敗，它應該會傳回發生的最後一個錯誤碼。  
  
 報告的規則是，如果在 IDE 中發生錯誤，IDE 會負責向它報告。 如果在原始檔控制系統中發生錯誤，原始檔控制外掛程式負責報告它。 比方說，「 目前沒有選取任何檔案 」 會報告在 IDE 中，而會報告 「 這個檔案已取出 」 外掛程式。  
  
## 內容結構  
 在呼叫期間 [SccInitialize](../extensibility/sccinitialize-function.md), ，呼叫端傳遞 `ppvContext` 參數，也就是未初始化的處理設為 void。 原始檔控制外掛程式可以忽略此參數，或是配置任何種類的結構，然後以該結構的指標放傳遞指標。 IDE 不了解此結構，但它會傳遞指標給這個結構到在外掛程式中的每個其他呼叫。 這提供寶貴的內容快取資訊以外掛程式，它可用來維護保存跨函式呼叫，而不使用全域變數的全域狀態資訊。 外掛程式會負責釋放在呼叫結構 [SccUninitialize](../extensibility/sccuninitialize-function.md)。  
  
 如果外掛程式設定 `SCC_CAP_REENTRANT` 位元 [SccInitialize](../extensibility/sccinitialize-function.md) \(尤其是在 `lpSccCaps` 參數\)，多個內容結構用來追蹤所有已開啟的專案。  
  
## 位元旗標和其他的命令選項  
 每個命令，例如 [SccGet](../extensibility/sccget-function.md), ，IDE 可以指定命令的行為變更的許多選項。  
  
 此 API 支援的某些選項，透過 ide 設定 `fOptions` 參數。 這些選項所述 [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md) 以及它們會影響的命令。 一般而言，這些是的選項，就不會提示使用者。  
  
 最使用者可設定的設定選項中未定義這種方式，因為它們很大異原始檔控制外掛程式。 因此，建議的機制是 **進階** \] 按鈕。 例如，在 **取得** 對話方塊中，IDE 會顯示的資訊，它了解，但它也會顯示 **進階** 如果外掛程式都具有此命令的選項按鈕。 當使用者按一下 **進階** \] 按鈕，IDE 呼叫 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 啟用原始檔控制外掛程式，以提示使用者輸入位元旗標或日期\/時間等資訊。 外掛程式會傳回此資訊在傳遞時所傳回的結構 `SccGet` 命令。  
  
## 請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)