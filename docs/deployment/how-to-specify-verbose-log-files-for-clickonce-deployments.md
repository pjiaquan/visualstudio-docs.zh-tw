---
title: "如何：指定供 ClickOnce 部署使用的詳細資訊記錄檔 | Microsoft Docs"
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
  - "ClickOnce 部署, 記錄"
  - "記錄檔, ClickOnce 部署"
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：指定供 ClickOnce 部署使用的詳細資訊記錄檔
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 會維護所有部署的活動記錄檔。  這些記錄檔會記錄有關安裝、初始化、更新及解除安裝 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署的詳細資料。  若要增加 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 寫入這些記錄檔的詳細資料，請使用 \[登錄編輯程式\] \(**regedit.exe**\) 來指定資料的詳細等級。  
  
> [!CAUTION]
>  如果您使用 \[登錄編輯程式\] 的方式不正確，可能會發生嚴重的問題，甚至可能需要重新安裝作業系統。  使用 \[登錄編輯程式\] 時請自行負責。  
  
 下列程序說明如何為目前的使用者指定 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 記錄檔的詳細等級。  若要降低詳細等級，請移除這個登錄值。  
  
### 若要指定顯示詳細資訊的記錄檔  
  
1.  開啟 **Regedit.exe**。  
  
2.  巡覽至 `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` 節點。  
  
3.  若有必要，建立名為 `LogVerbosityLevel` 的新字串值。  
  
4.  將 `LogVerbosityLevel` 值設為 `1`。  
  
## 請參閱  
 [疑難排解 ClickOnce 部署](../deployment/troubleshooting-clickonce-deployments.md)