---
title: "Outlook 表單區域中的自訂動作 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "自訂動作 [Visual Studio 中的 Office 程式開發]"
  - "表單區域 [Visual Studio 中的 Office 程式開發], 自訂動作"
ms.assetid: 583fd5f0-aafa-4858-9c54-38a9fdf3bede
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Outlook 表單區域中的自訂動作
  動作會顯示可供使用者用來回應 Microsoft Office Outlook 項目的按鈕。  例如，若要回應郵件項目，使用者會按一下 \[**回覆**\]、\[**全部回覆**\] 或 \[**轉寄**\] 動作按鈕。  這些動作的每一個都會建立新的郵件項目，並且使用原始項目的資訊填入新項目的欄位。  
  
 您可以建立開啟任何一種 Outlook 項目的自訂動作。  例如，您可以加入開啟新約會或工作項目的自訂動作。  設定自訂動作的屬性或使用自訂程式碼填入新項目的欄位。  自訂動作會出現在 Outlook 偵測器視窗中，所開啟項目的 \[**自訂動作**\] 下拉式清單中。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 將自訂動作加入至表單區域  
 若要將自訂動作加入至表單區域，請使用 \[**自訂動作**\] 對話方塊。  您可以展開節點，選取 \[**資訊清單**\]\[**CustomActions**\]屬性，然後按一下省略符號按鈕以開啟 \[**方案總管**\] 的 \[**自訂動作**\] 對話方塊 \(![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.png "ASP.NET Mobile 設計工具橢圓形")\)。  
  
 您可以使用 \[**自訂動作**\] 對話方塊指定「*目標表單*」\(Target Form\)。  目標表單是使用者執行自訂動作時出現的表單。  
  
 您也可以使用 \[**自訂動作**\] 對話方塊，指定在目標表單中顯示原始項目資訊的方式。  
  
 下表說明 \[**自訂動作**\] 對話方塊中提供的屬性。  
  
|屬性|描述|  
|--------|--------|  
|**AddressLike**|指定定址目標表單的方式。|  
|**Body**|指定原始項目主體附加至目標表單的方式。|  
|**Enabled**|指出是否已啟用自訂動作。  如果這個屬性設為 **false**，表示自訂動作已停用。|  
|**方法**|指定執行自訂動作時可用的回應類型。  自訂動作可傳送表單、開啟表單，或提示使用者要傳送或開啟表單。|  
|**名稱**|指定可用來在程式碼中參考這個自訂動作的內部名稱。|  
|**ShowOnRibbon**|指出是否在原始項目的功能區上顯示自訂動作。|  
|**SubjectPrefix**|指定插入目標表單主旨列開頭的文字。|  
|**TargetForm**|指定目標表單的訊息類別名稱。  例如，輸入 **IPM.Task** 開啟工作表單。|  
|**標題**|指定自訂動作按鈕的標籤。|  
  
## 自訂執行階段的自訂動作  
 您還可以使用程式碼在自訂動作中加入行為。  例如，您可以加入程式碼，用來取得電子郵件收件者的名稱，並將這些名稱當做出席者加入新的約會項目中。  若要執行這項操作，請處理 [Action](HV05247650) 物件的 [CustomAction](HV05247448) 事件。  
  
## 請參閱  
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [讓表單區域與 Outlook 訊息類別產生關聯](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  