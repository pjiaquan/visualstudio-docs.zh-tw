---
title: "專案設計工具、安全性頁 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesSecurity"
  - "vb.XBAPProjectPropertiesSecurity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "專案設計工具, [安全性] 頁面"
  - "專案設計工具中的 [安全性] 頁面"
ms.assetid: 641d9cd3-fa07-498a-8568-3c169bb4d3d5
caps.latest.revision: 34
caps.handback.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 專案設計工具、安全性頁
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

\[**專案設計工具**\] 的 \[**安全性**\] 頁面是用來針對使用 [!INCLUDE[ndptecclick](../../deployment/includes/ndptecclick_md.md)] 部署所部署的應用程式，設定程式碼存取安全性。  如需詳細資訊，請參閱 [ClickOnce 應用程式的程式碼存取安全性](../../deployment/code-access-security-for-clickonce-applications.md)。  
  
 如果要存取 \[**安全性**\] 頁面，請選取 \[**方案總管**\] 中的專案節點，然後按一下 \[**專案**\] 功能表上的 \[**屬性**\]。  當 \[**專案設計工具**\] 出現時，請按一下 \[**安全性**\] 索引標籤。  
  
## 安全性設定  
 **啟用 ClickOnce 安全性設定**  
 判斷是否可以在設計階段啟用安全性設定。  如果清除這個選項，則 \[**安全性**\] 頁面中的所有其他選項也都無法使用。  
  
> [!NOTE]
>  使用 \[**發行**\] 精靈發行應用程式時，這個選項會自動啟用。  
  
 如果選取這個選項，您可以選擇其中一個選項按鈕：\[**這是完全信任的應用程式**\] 或 \[**這是部分信任的應用程式**\]。  
  
 根據預設，WPF 瀏覽器應用程式專案中這個選項為選取。  
  
 根據預設，對於其他專案類型，這個選項為清除。  
  
 **這是完全信任的應用程式**  
 如果選取這個選項，則在用戶端電腦上安裝或執行應用程式時，應用程式就會要求「完全信任」權限。  如果可以請避免使用「完全信任」，因為應用程式將可不受限制的存取檔案系統和登錄等資源。  
  
 根據預設，WPF 瀏覽器應用程式專案中這個選項為「部分信任」。  
  
 根據預設，對其他專案類型，這個選項設定為「完全信任」。  
  
 **這是部分信任的應用程式**  
 如果選取這個選項，則在用戶端電腦上安裝或執行應用程式時，應用程式就會要求「部分信任」權限。  「*部分信任*」表示只有在要求之程式碼存取安全性權限下所允行的動作才會執行。  如需如何設定安全性權限的詳細資訊，請參閱 [ClickOnce 應用程式的程式碼存取安全性](../../deployment/code-access-security-for-clickonce-applications.md)  
  
 您可以在 \[**ClickOnce 安全性權限**\] 區域中設定這個選項，以指定「部分信任」安全性設定。  
  
## ClickOnce 安全性權限  
 **安裝應用程式的區域**  
 指定程式碼存取安全性權限的預設集合。  選擇 \[**網際網路**\] 或 \[**近端內部網路**\] 以取得限制的權限集，或者選擇 \[**\(自訂\)**\] 以設定自訂的權限集。  如果應用程式要求比區域中所授與的更多權限，ClickOnce 信任提示便會對使用者出現以授與額外權限。  如需如何設定安全性權限的詳細資訊，請參閱 [ClickOnce 應用程式的程式碼存取安全性](../../deployment/code-access-security-for-clickonce-applications.md)  
  
 根據預設，WPF Web 瀏覽器應用程式專案中這個選項為 \[**網際網路**\]。  
  
 **編輯權限 XML**  
 開啟應用程式資訊清單範本 \(app.manifest\) 來設定\[**\(自訂\)**\] 權限集的權限。  
  
 **進階**  
 開啟[進階安全性設定對話方塊](../../ide/reference/advanced-security-settings-dialog-box.md)，這個對話方塊是用來針對使用權限受到限制的應用程式進行偵錯設定。  偵錯時會檢查這些設定，而且權限例外狀況指出您的應用程式所需的權限可能多於在區域中定義的權限。  
  
## 請參閱  
 <xref:System.Security.Permissions.WebBrowserPermission>   
 <xref:System.Security.Permissions.MediaPermission>   
 [ClickOnce 應用程式的程式碼存取安全性](../../deployment/code-access-security-for-clickonce-applications.md)   
 [如何：啟用 ClickOnce 安全性設定](../../deployment/how-to-enable-clickonce-security-settings.md)   
 [如何：設定 ClickOnce 應用程式的安全性區域](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [如何：設定 ClickOnce 應用程式的自訂使用權限](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [如何：以限制使用權限偵錯 ClickOnce 應用程式](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [ClickOnce 安全性和部署](../../deployment/clickonce-security-and-deployment.md)   
 [專案屬性參考](../../ide/reference/project-properties-reference.md)   
 [進階安全性設定對話方塊](../../ide/reference/advanced-security-settings-dialog-box.md)