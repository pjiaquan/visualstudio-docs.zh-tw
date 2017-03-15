---
title: "如何：設定 ClickOnce 部署錯誤的自訂記錄檔位置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 部署, 錯誤記錄"
  - "ClickOnce 部署, 疑難排解"
  - "疑難排解 ClickOnce 部署"
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：設定 ClickOnce 部署錯誤的自訂記錄檔位置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 會維護所有部署的啟動記錄檔，  這些記錄檔會記錄有關安裝及初始化 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署的任何錯誤。  根據預設，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 會為每個部署啟動過程建立一個記錄檔，  它會將這些記錄檔儲存在 Temporary Internet Files 資料夾內。  當啟動失敗，且使用者在產生的錯誤對話方塊內按一下 \[**詳細資料**\] 時，會向使用者顯示部署的記錄檔。  
  
 您可以使用 \[登錄編輯程式\] \(**regedit.exe**\) 設定自訂的記錄檔路徑，針對特定用戶端變更這個行為。  在這個情形下，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 會將所有部署的啟動成功和失敗情況記錄在單一檔案中。  
  
> [!CAUTION]
>  如果您使用 \[登錄編輯程式\] 的方式不正確，可能會發生嚴重的問題，甚至可能需要重新安裝作業系統。  使用 \[登錄編輯程式\] 時請自行負責。  
  
> [!NOTE]
>  為了避免記錄檔變得太大，您偶而需要截斷或刪除記錄檔。  
  
 下列程序將說明如何為單一用戶端設定自訂記錄檔的位置。  
  
### 若要設定自訂記錄檔的位置  
  
1.  開啟 **Regedit.exe**。  
  
2.  巡覽到 `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` 節點。  
  
3.  將 `LogFilePath` 字串值設定為您偏好之自訂記錄檔位置的完整路徑和檔案名稱。  
  
     這個位置必須位於使用者具有寫入權限的目錄中。  例如，在 Windows Vista，建立下列資料夾結構並將 `LogFilePath` 設定為 C:\\Users\\\<username\>\\Documents\\Logs\\ClickOnce\\installation.log。  
  
## 請參閱  
 [疑難排解 ClickOnce 部署](../deployment/troubleshooting-clickonce-deployments.md)