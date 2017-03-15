---
title: "指定檔案名稱的副檔名的檔案處理常式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "檔案副檔名、 指定檔案的處理常式"
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 指定檔案名稱的副檔名的檔案處理常式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

有數種方法來判斷應用程式處理特定副檔名的檔案。 OpenWithList 和 OpenWithProgids 動詞命令是兩種方式可以指定副檔名的登錄項目底下的檔案處理常式。  
  
## OpenWithList 動詞命令  
 當您以滑鼠右鍵按一下 Windows 檔案總管\] 中的檔案時，您會看到 **開啟** 命令。 如果一個以上的產品與副檔名相關聯，您會看到 **開啟** \] 子功能表。  
  
 您可以註冊不同的應用程式來開啟副檔名為 HKEY\_CLASSES\_ROOT 裡設定 OpenWithList 機碼的副檔名。 列出此機碼的檔案副檔名的應用程式出現在 **建議程式** 標題中 **開啟** 對話方塊。 下列範例顯示開啟.vcproj 檔案延伸模組已註冊的應用程式。  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  指定的應用程式的金鑰已 HKEY\_CLASSES\_ROOT\\Applications 下方的清單中。  
  
 藉由新增 OpenWithList 索引鍵，您可以宣告您的應用程式支援檔案副檔名，即使另一個應用程式會取得延伸模組的擁有權。 這可能是您的應用程式或其他應用程式的未來版本。  
  
## OpenWithProgIDs  
 以程式設計方式識別項 \(Progid\) 是易記版本 Classid 來識別應用程式或 COM 物件的版本。 共置可建立的每個物件都應該有它自己的 ProgID。 例如，VisualStudio.DTE.7.1 啟動 Visual Studio.NET 2003 VisualStudio.DTE.10.0 啟動時 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 身為專案類型或專案項目類型的擁有者，您必須建立特定版本的 ProgID 檔案副檔名。 這些 Progid 可能是多餘的在於一個以上的 ProgID 可能啟動相同的應用程式。 如需詳細資訊，請參閱[註冊副檔名動詞命令](../extensibility/registering-verbs-for-file-name-extensions.md)。  
  
 使用版本控制檔案的 Progid 的下列命名慣例，以避免重複使用其他廠商的註冊︰  
  
|副檔名|版本控制 ProgID|  
|---------|-----------------|  
|.extension|產品名稱。 extension.versionMajor.versionMinor|  
  
 您可以註冊不同的應用程式能夠開啟特定的副檔名建立版本的 Progid 做為值加入 HKEY\_CLASSES\_ROOT\\*\< 擴充功能 \>*\\OpenWithProgids 索引鍵。 此登錄機碼包含檔案副檔名相關聯的替代 Progid 的清單。 列出的 Progid 相關聯的應用程式會出現在 **開啟***產品名稱* \] 子功能表。 如果同一個應用程式中同時指定 `OpenWithList` 和 `OpenWithProgids` 索引鍵，作業系統會將合併重複的項目。  
  
> [!NOTE]
>  `OpenWithProgids` 金鑰只支援在 Windows XP。 因為其他作業系統會忽略這個機碼，請勿使用它做為唯一的註冊檔案處理常式。 若要提供更好的使用者經驗，在 Windows XP 中使用此金鑰。  
  
 加入所需的 Progid 做為 REG\_NONE 類型的值。 下列程式碼提供的 Progid 註冊副檔名的範例 \(。*ext*\).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 指定為副檔名的預設值是預設檔案處理常式的 ProgID。 如果您修改隨附於舊版的檔案副檔名 ProgID [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 或，可以接替其他應用程式，則您必須註冊 `OpenWithProgids` 鍵檔案副檔名，以及您所支援的舊 Progid\] 清單中指定新的 ProgID。 例如：  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 如果舊 ProgID 有與其相關聯，動詞命令，則這些動詞命令也會出現在 \[ **開啟** *產品名稱* 快顯功能表中。  
  
## 請參閱  
 [關於檔案名稱的副檔名](../extensibility/about-file-name-extensions.md)   
 [註冊副檔名動詞命令](../extensibility/registering-verbs-for-file-name-extensions.md)