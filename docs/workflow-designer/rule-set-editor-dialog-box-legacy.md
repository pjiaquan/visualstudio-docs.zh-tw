---
title: "規則集編輯器對話方塊 (舊版) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Rules.Design.RuleSetDialog.UI"
helpviewer_keywords: 
  - "規則集編輯器對話方塊"
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 規則集編輯器對話方塊 (舊版)
本主題描述如何在舊版 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中使用 \[**規則集編輯器**\] 對話方塊。當您需要以 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 為目標時，請使用舊版 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。  
  
 \[**規則集編輯器**\] 對話方塊用於建立和修改 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) 規則集，此規則集可序列化為 .rules 檔案。  
  
> [!NOTE]
>  如果您要以 \[**支援編碼功能的 XML 編輯器**\] 開啟 .rules 檔案，您必須先關閉工作流程或活動的相關設計工具視窗。  
  
 如需如何存取 \[**規則集編輯器**\] 對話方塊的詳細資訊，請參閱[HOW TO：建立 PolicyActivity 規則集 \(舊版\)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)。  
  
> [!WARNING]
>  舊版 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的規則編輯器，它所針對的 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 不支援多重目標。  
  
 下表說明 \[**規則集編輯器**\] 對話方塊中的使用者介面 \(UI\) 項目。  
  
|UI 項目|說明|  
|-----------|--------|  
|**新增規則**|將新的規則定義新增至規則集。|  
|**刪除**|將選取的規則從規則集內刪除。|  
|**鏈結**|指定規則集要使用哪種類型的向前鏈結。可用的選項有：<br /><br /> -   **完整鏈結**：指定使用所有的向前鏈結機制：隱含、以方法設定屬性，以及使用 **Update** 函式進行明確更新。<br />-   **循序**：指定不使用任何向前鏈結。<br />-   **僅明確更新**：指定僅在「**更新**」動作上執行向前鏈結。<br /><br /> 如需向前鏈結的詳細資訊，請參閱[使用 PolicyActivity 活動](http://go.microsoft.com/fwlink?LinkID=65004) \(英文\)。|  
|**名稱**|規則集清單資料行標題。按一下會按照名稱排序規則清單。|  
|**優先權**|規則集清單資料行標題。按一下會按照優先權排序規則清單。|  
|**重新評估**|規則集清單資料行標題。按一下會按照重新評估類型排序規則清單。|  
|**規則預覽**|規則集清單資料行標題。按一下會按照規則的條件和動作預覽排序規則清單。|  
|**名稱:**|輸入規則名稱。|  
|**優先權:**|輸入規則的優先權。預設優先權為 0。|  
|**重新評估:**|指定規則要使用哪一種規則重新評估。可用的選項有：<br /><br /> -   **永遠**：讓規則視需要重新評估。<br />-   **永不**：讓規則永不重新評估。在此狀況下，規則只執行一次。|  
|**作用中**|核取可讓規則成為作用中。|  
|**條件：**|輸入規則條件的運算式。如需運算式語法的詳細資訊，請參閱本頁的「輸入條件和動作運算式」一節。|  
|**Then 動作:**|輸入 Then 動作的運算式。如需運算式語法的詳細資訊，請參閱本頁的「輸入條件和動作運算式」一節。|  
|**Else 動作:**|輸入 Else 動作的運算式。如需運算式語法的詳細資訊，請參閱本頁的「輸入條件和動作運算式」一節。|  
|**確定**|按一下將規則集儲存為 .rules 檔案。|  
  
 如需規則集的詳細資訊，請參閱[使用 PolicyActivity 活動](http://go.microsoft.com/fwlink?LinkID=65004) \(英文\)。  
  
## 輸入條件和動作運算式  
 您可以在 \[**規則集編輯器**\] 對話方塊內的 \[條件\]、\[Then 動作\] 和 \[Else 動作\] 文字方塊中，輸入運算式文字。您可以在編輯器中輸入 **this.**，使用 IntelliSense 型的功能表，來參考工作流程中使用的欄位、屬性和方法。或者您可以直接輸入工作流程成員名稱。您可以輸入類別名稱，後面加上方法名稱，來呼叫參考型別上的靜態方法。  
  
 您可以將邏輯運算子新增至條件中，如 AND、OR 和 NOT。您也可以新增述詞 \(Predicate\)。述詞是二元 \(Binary\) 運算子和兩個運算元。支援的二元運算子有 \=\=、\>、\<、\>\= 和 \<\=。支援的運算元有常數值、算術函式和有範圍的 Public 成員。  
  
 您可以指定比較類型，也可以與 **null** 或空白字串比較。您可以對包含複雜型別之變數上的成員進行巢狀呼叫，例如，`this.Address.State == "WA"`。  
  
 運算式支援以下運算子：  
  
-   關係 \(Relational\) 運算子：\=\=、\=、\!\=  
  
-   比較運算子：\<、\<\=、\>、\>\=  
  
-   算術運算子：\+、\-、\*、\/、MOD  
  
-   邏輯運算子 \(Logical Operator\)：AND、&&、OR、&#124;&#124;、NOT、\!  
  
-   位元 \(Bitwise\) 運算子：&、&#124;  
  
 運算式運算子的優先順序是按照 C\# 運算子優先順序規則。  
  
 如需條件的詳細資訊，請參閱[Using Conditions in Workflows](http://msdn.microsoft.com/zh-tw/541211f5-d382-4810-894f-71f00b34fa77)。  
  
### 暫止和更新函式  
 \[**Then 動作:**\] 和 \[**Else 動作:**\] 運算式支援 **Halt** 和 **Update** 函式。若要使用 **Halt** 函式，請將 **Halt** 輸入 \[**Then 動作:**\] 或 \[**Else 動作:**\] 文字方塊中。**Halt** 動作會造成規則集立即停止執行，控制權回到呼叫的程式碼。您也可以將 **Update** 函式與向前鏈結搭配使用。  
  
 **Update** 陳述式在編輯器中可以兩種形式表示，以下範例顯示這兩種形式：  
  
```  
Update(this.Address.State)  
Update("this/Address/State")  
```  
  
 如需將 **Update** 與向前鏈結搭配使用的詳細資訊，請參閱[使用 PolicyActivity 活動](http://go.microsoft.com/fwlink?LinkID=65004) \(英文\)。  
  
## 請參閱  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [選取規則集對話方塊 \(舊版\)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [使用 PolicyActivity 活動](http://go.microsoft.com/fwlink?LinkID=65004)   
 [在工作流程中使用條件](http://go.microsoft.com/fwlink?LinkID=65009)