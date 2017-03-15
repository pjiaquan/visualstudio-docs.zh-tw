---
title: "範本目錄描述 (。Vsdir) 檔案 | Microsoft Docs"
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
  - ".vsdir 檔案"
  - "VSDIR 檔案"
  - "範本目錄描述檔案"
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 範本目錄描述 (。Vsdir) 檔案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

範本目錄描述檔案 (.vsdir) 是文字檔案，可讓整合式的開發環境 (IDE) 來顯示資料夾、 精靈.vsz 檔案和相關聯的專案] 對話方塊中的範本檔案。 內容包括每個檔案或資料夾的一筆記錄。 合併所有.vsdir 檔案中參考的位置時，雖然只有一個.vsdir 檔案通常會提供描述多個資料夾中，精靈或範本檔案。  
  
 資料夾 （子目錄）.vsdir 檔案，與.vsdir 檔案本身中所參考的檔案所有位於相同的目錄。 當 IDE 執行精靈，或顯示資料夾或檔案中的 **新的專案** 或 **加入新項目** 對話方塊中，IDE 會檢查包含執行的檔案，以決定.vsdir 檔案是否存在的目錄。 如果找到.vsdir 檔案時，IDE 會讀取以判斷它是否包含執行或顯示資料夾或檔案的項目。 如果找到項目，則 IDE 會在精靈的執行或顯示的內容中使用的資訊。  
  
 下列程式碼範例會從檔案 SourceFiles.vsdir 中 \< EnvSDK>\BscPrj\BscPrj\BscPrjProjectItems\Source_Files 登錄機碼︰  
  
```  
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127  
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124  
```  
  
 在此情況下，兩筆記錄會在一個檔案中。 新的一行 （歸位字元） 來分隔每一筆記錄。 每一行代表不同的檔案類型。 直立線符號 (&#124;) 字元會區隔每個記錄中的欄位。 單一目錄可以包含多個.vsdir 檔案有不同的檔案名稱，或您可以有一個.vsdir 檔案，每個檔案類型。  
  
## <a name="fields"></a>欄位  
 下表列出每一筆記錄中指定的欄位。  
  
|欄位|描述|  
|-----------|-----------------|  
|相對路徑名稱 (RelPathName)|資料夾、 範本或.vsz 檔案，例如 HeaderFile.h 或 MyWizard.vsz 的名稱。 這個欄位也可以用來代表資料夾的名稱。|  
|{clsidPackage}|可讓您存取中的當地語系化字串，例如 LocalizedName、 描述、 IconResourceId 和 SuggestedBaseName，VSPackage 的附屬動態連結程式庫 (DLL) 資源的 VSPackage 的 GUID。 如果沒有提供 DLLPath，適用於 IconResourceId。 **注意︰**  這個欄位是選擇性的除非一個或多個先前的欄位是資源識別碼。 這個欄位是對應的未當地語系化文字的第三方精靈.vsdir 檔案通常留空。|  
|LocalizedName|精靈的範本檔案的當地語系化的名稱。 這個欄位可以是字串或表單 「 #ResID 」 資源識別項。 這個名稱會顯示在 **加入新項目** 對話方塊。 **注意︰**  如果 LocalizedName 是資源識別碼，則需要 {clsidPackage}。|  
|SortPriority|整數，表示此範本檔案或精靈的相對優先權。 比方說，如果此項目有值為 1，則其他項目旁的值為 1 和 2 或更大的所有項目排序值的前面顯示此項目。<br /><br /> 排序優先順序是相對於相同的目錄中的項目。 相同的目錄中可能有一個以上的.vsdir 檔案。 在此情況下，從所有項目 *。*該目錄中的 vsdir 檔案會合併。 具有相同優先順序的項目所示的顯示名稱不區分大小寫編纂順序。  `_wcsicmp` 函數用來排序的項目。<br /><br /> .Vsdir 檔案中未說明的項目包括大於.vsdir 檔案中列出的最高優先順序號碼的優先順序數字。 結果是清單的這些項目可以顯示，不論其名稱的結尾。|  
|描述|精靈的範本檔案的當地語系化的描述。 這個欄位可以是字串或表單 「 #ResID 」 資源識別項。 此字串會出現在 **新的專案** 或 **加入新項目** ] 對話方塊中選取項目時。|  
|DLLPath 或者 {clsidPackage}|用來載入範本檔案或精靈圖示。 圖示會 IconResourceId 載入做為資源.dll 或.exe 檔案。 使用完整路徑，或使用 VSPackage 的 GUID，就可以識別此.dll 或.exe 檔案。 實作 VSPackage 的 DLL 用來載入圖示 （不附屬 DLL）。|  
|IconResourceId|在 DLL 或 VSPackage 實作 DLL，決定要顯示的圖示資源識別碼。|  
|旗標 (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>)|用來停用或啟用 **名稱** 和 **位置** 欄位上 **加入新項目** 對話方塊。 值 **旗標** 欄位相當於十進位的位元旗標的組合。<br /><br /> 當使用者選取的項目上 **新增** 索引標籤中，專案會決定是否 [名稱] 欄位和 [位置] 欄位會顯示當 **加入新項目** 第一次顯示對話方塊。 項目，透過.vsdir 檔案，可以僅限控制項是否欄位就會啟用與停用選取的項目時。|  
|SuggestedBaseName|代表檔案、 精靈或範本的預設名稱。 這個欄位是字串或表單 「 #ResID 」 資源識別項。 IDE 會使用此值來提供項目的預設名稱。 這個基底值會加到讓名稱成為唯一的例如 MyFile21.asp 整數值。<br /><br /> 在上述清單中，描述、 DLLPath、 IconResourceId、 旗標和 SuggestedBaseNumber 僅適用於範本和精靈檔案。 這些欄位不適用於資料夾。 這個事實所示的 BscPrjProjectItems 檔案中的程式碼 \< EnvSDK>\BscPrj\BscPrj\BscPrjProjectItems 登錄機碼。 這個檔案包含三筆記錄 （一個用於每個資料夾） 的每一筆記錄的四個欄位︰ RelPathName，{clsidPackage}，LocalizedName 和 SortPriority。<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120`|  
  
 當您建立精靈檔案時，您也應該考慮下列問題。  
  
-   任何有意義的資料是任何非必要的欄位應包含 0 （零），做為預留位置。  
  
-   如果未不提供任何當地語系化的名稱，則相對路徑名稱使用精靈檔案中。  
  
-   DLLPath 會覆寫 clsidPackage 的圖示位置。  
  
-   如果沒有定義圖示，IDE 會取代該擴充功能的檔案的預設圖示。  
  
-   如果不提供任何建議的基底名稱，則會使用 「 專案 」。  
  
-   如果您刪除.vsz 檔案、 資料夾或範本檔案，您也必須從.vsdir 檔案中移除其相關聯的記錄。  
  
## <a name="see-also"></a>請參閱  
 [精靈](../../extensibility/internals/wizards.md)   
 [精靈 (。Vsz) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)