---
title: "自訂 Outlook 的功能區"
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
  - "自訂功能區, 關於自訂功能區"
  - "自訂功能區, 關於自訂功能區"
  - "偵測器 [Visual Studio 中的 Office 程式開發]"
  - "Outlook [Visual Studio 中的 Office 程式開發], 功能區"
  - "功能區 [Visual Studio 中的 Office 程式開發], Outlook"
ms.assetid: 11d10e72-806d-4d5e-b080-139bd8633eaa
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# 自訂 Outlook 的功能區
  當您在 Microsoft Office Outlook 自訂功能區時，您必須考慮自訂功能區在應用程式中出現的位置。  Outlook 會將功能區顯示在主應用程式使用者介面 \(UI\) 中，以及在使用者執行建立電子郵件訊息等特定工作時開啟的視窗中。  這些應用程式視窗名為偵測器。  
  
 ![視訊的連結](~/data-tools/media/playvideo.gif "視訊的連結") 如需相關的影片示範，請參閱 [如何使用功能區設計工具自訂 Outlook 功能區？](http://go.microsoft.com/fwlink/?LinkID=130312)。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 在主應用程式 UI 加入自訂功能區  
 Outlook 中的主應用程式 UI 稱為「總管」。  如果您使用的是 \[功能區 \(視覺化設計工具\)\] 項目，您可按一下 \[屬性\] 視窗中的 \[RibbonType\] 功能區屬性，然後選取 \[Microsoft.Outlook.Explorer\]，將功能區加入總管。  
  
## 將功能區指派給偵測器  
 您可藉由指定與偵測器訊息類別相對應的功能區類型，識別您想要自訂的偵測器。  
  
 如果您使用的是 \[功能區 \(視覺化設計工具\)\] 項目，按一下 \[屬性\] 視窗中的 \[RibbonType\] 功能區屬性，然後從值的清單中選取一或多個功能區 ID。  
  
 您可以在專案中加入多個功能區。  如果有多個功能區共用功能區 ID，請覆寫在專案 `ThisAddin` 類別中的 CreateRibbonExtensibilityObject 方法，以指定要在執行階段顯示哪個功能區。  如需詳細資訊，請參閱[功能區概觀](../vsto/ribbon-overview.md)。  如需每個功能區類型的詳細資訊，請參閱技術文件[自訂 Outlook 2007 中的功能區](http://msdn.microsoft.com/zh-tw/946e97ea-f556-4e84-8fac-01cd9214e170)。  
  
## 使用功能區 XML 來指定功能區類型  
 如果您使用 \[功能區 \(XML\)\] 項目，請檢查 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> 方法中 *ribbonID* 參數的值，並傳回適當的功能區。  
  
 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> 方法會在功能區程式碼檔中由 Visual Studio 自動產生。  *ribbonID* 參數是識別總管或特定類型偵測器的字串。  如需 *ribbonID* 參數的可能值完整清單，請參閱技術文件[自訂 Outlook 2007 中的功能區](http://msdn.microsoft.com/zh-tw/946e97ea-f556-4e84-8fac-01cd9214e170)。  
  
 下列程式碼範例示範如何只在 `Microsoft.Outlook.Mail.Compose` 偵測器中顯示自訂功能區。  這是在使用者建立新的電子郵件訊息時開啟的偵測器。  `GetResourceText()` 方法會指定要顯示的功能區，此方法產生於 **Ribbon** 類別中。  如需 **Ribbon** 類別的詳細資訊，請參閱[功能區 XML](../vsto/ribbon-xml.md)。  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/CS/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/VB/Ribbon1.vb#1)]  
  
## 請參閱  
 [在執行階段存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)   
 [功能區概觀](../vsto/ribbon-overview.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [功能區 XML](../vsto/ribbon-xml.md)  
  
  