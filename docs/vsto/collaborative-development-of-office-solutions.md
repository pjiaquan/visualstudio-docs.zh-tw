---
title: "Office 方案的共同開發 | Microsoft Docs"
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
  - "共同開發 [Visual Studio 中的 Office 程式開發]"
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發], 共同開發"
  - "Visual Studio 中的 Office 程式開發, 共同作業"
  - "原始檔控制 [Visual Studio 中的 Office 程式開發]"
ms.assetid: c493354b-17d3-4e50-85f0-968b104bc978
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Office 方案的共同開發
  多位開發人員可以共同處理某個 Office 專案，方法就和共同處理其他 Visual Studio 專案一樣。  即使 Office 安裝在不同的位置上，Visual Studio 還是可以正確找出每部電腦上的 Microsoft Office 安裝。  但是，有一些重要的考量必須留意。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 偵錯屬性並非共用  
 偵錯屬性不是在原始檔控制下由多個使用者共用。  Visual Basic 和 Visual C\# 專案會將偵錯屬性儲存在使用者專屬檔案 \(\<*專案名稱*\>.vbproj.user 或 \<*專案名稱*\>.csproj.user\) 中，而這個檔案不在原始檔控制的範圍內。  如果超過一個人在進行偵錯，每個人都必須以手動方式輸入偵錯屬性。  
  
 如果專案是存放在網路共用上，而不在原始檔控制中，就必須另外採取其他步驟，以便讓共同作業的開發人員開啟方案並測試組件。  
  
## 原始檔控制需要簽出所有檔案  
 如果您在專案中進行原始檔控制，則每次變更程式碼檔時，都應該要簽出 \[**方案總管**\] 中程式碼檔 \(如 ThisDocument、ThisWorkbook 或 ThisAddIn 程式碼檔\) 底下的所有檔案，即使是預設為隱藏的檔案也要簽出。  如果只簽出最上層的程式碼檔，則進行的變更可能會遺失。  
  
 在您進行變更之後，請將所有檔案再次簽入。  如需專案中隱藏之程式碼檔的詳細資訊，請參閱 [在 Visual Studio 環境下的 Office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)。  
  
## 網路上非正式共同作業的安全性  
 對於所有位在網路位置 \(如 \\\\\<*伺服器名稱*\>\\\<*共用名稱*\>\) 的文件層級方案，必須將完整位置加入至您所使用之 Microsoft Office 應用程式的信任資料夾清單中。  請選取併入主資料夾下所有子目錄的選項，或特別將偵錯和組建資料夾加入至信任資料夾清單。  如需這個做法的詳細資訊，請參閱 [授與信任給文件](../vsto/granting-trust-to-documents.md)。  
  
 在建置階段自動產生的暫存憑證不受密碼保護。  這些憑證會包含開發人員的登入名稱和其他個人資訊。  如果您部署了以暫存憑證簽署的自訂，則其他人可能可以存取這些資訊。  
  
## 請參閱  
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [建置 Office 方案](../vsto/building-office-solutions.md)  
  
  