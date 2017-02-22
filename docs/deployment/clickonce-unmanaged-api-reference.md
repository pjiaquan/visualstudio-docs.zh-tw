---
title: "ClickOnce Unmanaged API 參考 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
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
  - "CleanOnlineAppCache [ClickOnce Unmanaged]"
  - "CleanOnlineAppCacheW interface [ClickOnce Unmanaged]"
  - "ClickOnce, Unmanaged API"
  - "GetDeploymentDataFromManifest [ClickOnce unmanaged]"
  - "LaunchApplication [ClickOnce unmanaged]"
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce Unmanaged API 參考
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

來自 dfshim.dll 的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Unmanaged 公用 API。  
  
## CleanOnlineAppCache  
 從 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式快取清除或解除安裝所有線上應用程式。  
  
### 傳回值  
 如果成功則傳回 S\_OK，否則會傳回表示失敗的 HRESULT。  如果發生 Managed 例外狀況，會傳回 0x80020009 \(DISP\_E\_EXCEPTION\)。  
  
### 備註  
 呼叫 CleanOnlineAppCache 將會啟動 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 服務 \(如果它尚未執行\)。  
  
## GetDeploymentDataFromManifest  
 從資訊清單和啟動 URL 擷取部署資訊。  
  
### 參數  
  
|參數|描述|型別|  
|--------|--------|--------|  
|`pcwzActivationUrl`|`ActivationURL` 的指標。|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|`PathToDeploymentManifest` 的指標。|LPCWSTR|  
|`pwzApplicationIdentity`|緩衝區的指標，以接收傳回之指定完整應用程式識別的 NULL 結尾字串。|LPWSTR|  
|`pdwIdentityBufferLength`|DWORD 的指標，此 DWORD 是 `pwzApplicationIdentity` 緩衝區的長度，以 WCHAR 為單位。  這包括 NULL 結尾字元所佔的空間。|LPDWORD|  
|`pwzProcessorArchitecture`|緩衝區的指標，以從資訊清單接收指定應用程式部署處理器架構的 NULL 結尾字串。|LPWSTR|  
|`pdwArchitectureBufferLength`|DWORD 的指標，此 DWORD 是 `pwzProcessorArchitecture` 緩衝區的長度，以 WCHAR 為單位。|LPDWORD|  
|`pwzApplicationManifestCodebase`|緩衝區的指標，以從資訊清單接收指定應用程式資訊清單程式碼基底的 NULL 結尾字串。|LPWSTR|  
|`pdwCodebaseBufferLength`|DWORD 的指標，此 DWORD 是 `pwzApplicationManifestCodebase` 緩衝區的長度，以 WCHAR 為單位。|LPDWORD|  
|`pwzDeploymentProvider`|緩衝區的指標，以從資訊清單接收指定部署提供者的 NULL 結尾字串 \(如有的話\)。  否則就會傳回空字串。|LPWSTR|  
|`pdwProviderBufferLength`|DWORD 的指標，此 DWORD 是 `pwzProviderBufferLength` 的長度。|LPDWORD|  
  
### 傳回值  
 如果成功則傳回 S\_OK，否則會傳回表示失敗的 HRESULT。  如果緩衝區太小，會傳回 HRESULTFROMWIN32\(ERROR\_INSUFFICIENT\_BUFFER\)。  
  
### 備註  
 指標不得為 null。  `pcwzActivationUrl` 和 `pcwzPathToDeploymentManifest` 不可為空白。  
  
 清除啟動 URL 是呼叫端的責任。  例如，在需要的位置加入逸出字元或移除查詢字串。  
  
 限制輸入長度是呼叫端的責任。  例如，URL 長度上限為 2KB。  
  
## LaunchApplication  
 使用部署 URL 啟動或安裝應用程式。  
  
### 參數  
  
|參數|描述|型別|  
|--------|--------|--------|  
|`deploymentUrl`|NULL 結尾字串的指標，該字串包含部署資訊清單的 URL。|LPCWSTR|  
|`data`|保留供將來使用。  必須為 NULL。|LPVOID|  
|`flags`|保留供將來使用。  必須為 0。|DWORD|  
  
### 傳回值  
 如果成功則傳回 S\_OK，否則會傳回表示失敗的 HRESULT。  如果發生 Managed 例外狀況，會傳回 0x80020009 \(DISP\_E\_EXCEPTION\)。  
  
## 請參閱  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>