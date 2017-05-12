---
title: "如何：設定內含清單的安全性"
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
  - "內含清單 [Visual Studio 中的 Office 程式開發]"
  - "使用權限 [Visual Studio 中的 Office 程式開發]"
ms.assetid: 0609d8f0-4630-4e17-aeb3-14f3134165cf
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# 如何：設定內含清單的安全性
  如果您具有系統管理員使用權限，可將信任決策儲存在內含清單，設定 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示，以控制是否向使用者提供安裝 Office 方案的選項。  如需內含清單的詳細資訊，請參閱[使用內含清單信任 Office 方案](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 對於五個區域之每個區域中的方案，您可以設定下列選項：  
  
-   啟用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示金鑰和內含清單。  您可以允許使用者對已使用任何憑證簽署的 Office 方案授與信任。  
  
-   限制 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示金鑰和內含清單。  您可以允許使用者安裝已使用憑證簽署的 Office 方案，而該憑證可識別發行者 \(Publisher\)，但尚未受信任。  
  
-   停用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示金鑰和內含清單。  您可以防止使用者安裝任何未明確使用信任憑證簽署的 Office 方案。  
  
## 啟用內含清單  
 當您希望對使用者顯示安裝和執行來自某區域之任何 Office 方案的選項時，請啟用該區域的內含清單。  
  
#### 若要使用登錄編輯程式啟用內含清單  
  
1.  開啟登錄編輯器：  
  
    1.  按一下 \[**開始**\]，再按一下 \[**執行**\]。  
  
    2.  在 \[**開啟**\] 方塊中，輸入 **regedt32.exe**，然後按一下 \[**確定**\]。  
  
2.  尋找下列登錄機碼：  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     如果機碼不存在，請加以建立。  
  
3.  如果還沒有，請加入下列子機碼 \(Subkey\) 做為 \[**字串值**\] 以及關聯值。  
  
    |字串值子機碼|值|  
    |------------|-------|  
    |**網際網路**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**Disabled**|  
    |**MyComputer**|**Enabled**|  
    |**近端內部網路**|**Enabled**|  
    |**TrustedSites**|**Enabled**|  
  
     根據預設，**Internet** 的值為 **AuthenticodeRequired**，而 **UntrustedSites** 的值為 **Disabled**。  
  
#### 若要以程式設計的方式啟用內含清單  
  
1.  建立 Visual Basic 或 Visual C\# 主控台應用程式。  
  
2.  開啟 Program.vb 或 Program.cs 檔案以進行編輯，然後加入下列程式碼。  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  建置並執行應用程式。  
  
## 限制內含清單  
 限制內含清單，以在確認方案已用具有已知識別 \(Identity\) 的 Authenticode 憑證來簽署之後，才提示使用者決定是否信任。  
  
#### 若要限制內含清單  
  
1.  開啟登錄編輯器：  
  
    1.  按一下 \[**開始**\]，再按一下 \[**執行**\]。  
  
    2.  在 \[**開啟**\] 方塊中，輸入 **regedt32.exe**，然後按一下 \[**確定**\]。  
  
2.  尋找下列登錄機碼：  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     如果機碼不存在，請加以建立。  
  
3.  如果還沒有，請加入下列子機碼 \(Subkey\) 做為 \[**字串值**\] 以及關聯值。  
  
    |字串值子機碼|值|  
    |------------|-------|  
    |**UntrustedSites**|**Disabled**|  
    |**網際網路**|**AuthenticodeRequired**|  
    |**MyComputer**|**AuthenticodeRequired**|  
    |**近端內部網路**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     根據預設，**Internet** 的值為 **AuthenticodeRequired**，而 **UntrustedSites** 的值為 **Disabled**。  
  
#### 若要以程式設計的方式限制內含清單  
  
1.  建立 Visual Basic 或 Visual C\# 主控台應用程式。  
  
2.  開啟 Program.vb 或 Program.cs 檔案以進行編輯，然後加入下列程式碼。  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  建置並執行應用程式。  
  
## 停用內含清單  
 您可以停用內含清單，讓使用者只可以安裝經過信任的已知憑證簽署的方案。  
  
#### 若要停用內含清單  
  
1.  開啟登錄編輯器：  
  
    1.  按一下 \[**開始**\]，再按一下 \[**執行**\]。  
  
    2.  在 \[**開啟**\] 方塊中，輸入 **regedt32.exe**，然後按一下 \[**確定**\]。  
  
2.  如果下列登錄機碼尚未存在，請加以建立：  
  
     **\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel**  
  
3.  如果還沒有，請加入下列子機碼 \(Subkey\) 做為 \[**字串值**\] 以及關聯值。  
  
    |字串值子機碼|值|  
    |------------|-------|  
    |**UntrustedSites**|**Disabled**|  
    |**網際網路**|**Disabled**|  
    |**MyComputer**|**Disabled**|  
    |**近端內部網路**|**Disabled**|  
    |**TrustedSites**|**Disabled**|  
  
#### 若要以程式設計的方式停用內含清單  
  
1.  建立 Visual Basic 或 Visual C\# 主控台應用程式。  
  
2.  開啟 Program.vb 或 Program.cs 檔案以進行編輯，然後加入下列程式碼。  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3.  建置並執行應用程式。  
  
## 請參閱  
 [使用內含清單信任 Office 方案](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [保護 Office 方案](../vsto/securing-office-solutions.md)  
  
  