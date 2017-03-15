---
title: "如何：重新簽署應用程式和部署資訊清單 | Microsoft Docs"
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
  - "ClickOnce 部署, 簽署資訊清單"
  - "部署應用程式 [ClickOnce], 簽署資訊清單"
  - "部署應用程式, 簽署資訊清單"
  - "Office 應用程式, 簽署資訊清單"
  - "Visual Studio 中的 Office 程式開發, 簽署資訊清單"
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：重新簽署應用程式和部署資訊清單
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

對 Windows Form 應用程式、Windows Presentation Foundation 應用程式 \(xbap\) 或 Office 方案之應用程式資訊清單中的部署屬性進行變更之後，您必須以憑證來重新簽署應用程式及部署資訊清單。  這項程序有助於確保不會在使用者電腦上安裝遭到修改的檔案。  
  
 另一個可能要重新簽署資訊清單的情況，是在客戶想要以自己的憑證來簽署應用程式及部署資訊清單的時候。  
  
## 重新簽署應用程式和部署資訊清單  
 這個程序假設您已經對應用程式資訊清單檔 \(.manifest\) 完成變更。  如需詳細資訊，請參閱 [HOW TO：變更部署屬性](http://msdn.microsoft.com/zh-tw/66052a3a-8127-4964-8147-2477ef5d1472)。  
  
#### 若要使用 Mage.exe 重新簽署應用程式和部署資訊清單  
  
1.  開啟 \[**Visual Studio 命令提示字元**\] 視窗。  
  
2.  將目錄切換到包含您要簽署之資訊清單檔的資料夾。  
  
3.  輸入下列命令以簽署應用程式資訊清單檔。  以加上副檔名的資訊清單檔名稱，取代 ManifestFileName。  以憑證檔的相對或完整路徑取代 Certificate，並以該憑證的密碼取代 Password。  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     例如，您可以執行下列命令來簽署增益集、Windows Form 應用程式或 Windows Presentation Foundation 瀏覽器應用程式的應用程式資訊清單。  不建議在實際執行環境中使用 Visual Studio 所建立的暫時憑證來進行部署。  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  輸入下列命令以更新和簽署部署資訊清單檔，並依照上述步驟取代預留位置名稱。  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     例如，您可以執行下列命令來更新和簽署 Excel 增益集、Windows Form 應用程式或 Windows Presentation Foundation 瀏覽器應用程式的部署資訊清單。  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  \(選擇性\) 將主要部署資訊清單 \(publish\\*appname*.application\) 複製到您的版本部署目錄 \(publish\\Application Files\\*appname*\_*version*\)。  
  
## 更新和重新簽署應用程式和部署資訊清單  
 這個程序假設您已變更應用程式資訊清單檔 \(.manifest\)，但是還有其他檔案也已更新。  更新檔案時，也必須更新代表檔案的雜湊。  
  
#### 若要使用 Mage.exe 更新和重新簽署應用程式和部署資訊清單  
  
1.  開啟 \[**Visual Studio 命令提示字元**\] 視窗。  
  
2.  將目錄切換到包含您要簽署之資訊清單檔的資料夾。  
  
3.  移除發行輸出資料夾中檔案的副檔名 .deploy。  
  
4.  輸入下列命令，使用已更新檔案的新雜湊來更新應用程式資訊清單，並簽署應用程式資訊清單檔案。  以加上副檔名的資訊清單檔名稱，取代 ManifestFileName。  以憑證檔的相對或完整路徑取代 Certificate，並以該憑證的密碼取代 Password。  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     例如，您可以執行下列命令來簽署增益集、Windows Form 應用程式或 Windows Presentation Foundation 瀏覽器應用程式的應用程式資訊清單。  不建議在實際執行環境中使用 Visual Studio 所建立的暫時憑證來進行部署。  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  輸入下列命令以更新和簽署部署資訊清單檔，並依照上述步驟取代預留位置名稱。  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     例如，您可以執行下列命令來更新和簽署 Excel 增益集、Windows Form 應用程式或 Windows Presentation Foundation 瀏覽器應用程式的部署資訊清單。  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  將副檔名 .deploy 加回檔案中，但不含應用程式和部署資訊清單檔案。  
  
7.  \(選擇性\) 將主要部署資訊清單 \(publish\\*appname*.application\) 複製到您的版本部署目錄 \(publish\\Application Files\\*appname*\_*version*\)。  
  
## 請參閱  
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce 和 Authenticode](../deployment/clickonce-and-authenticode.md)   
 [受信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)   
 [如何：啟用 ClickOnce 安全性設定](../deployment/how-to-enable-clickonce-security-settings.md)   
 [如何：設定 ClickOnce 應用程式的安全性區域](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [如何：設定 ClickOnce 應用程式的自訂使用權限](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [如何：以限制使用權限偵錯 ClickOnce 應用程式](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [如何：新增信任發行者至 ClickOnce 應用程式的用戶端電腦](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [如何：設定 ClickOnce 信任提示行為](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)