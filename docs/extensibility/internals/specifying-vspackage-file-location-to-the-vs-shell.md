---
title: "指定 VS Shell VSPackage 檔案位置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managed 的 VSPackages，檔案位置"
  - "VSPackages，管理封裝檔案位置"
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 指定 VS Shell VSPackage 檔案位置
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 必須能夠找出組件 DLL 載入 VSPackage。 您可以找到以各種方式下, 表中所述。  
  
|方法|描述|  
|--------|--------|  
|使用程式碼基底登錄機碼。|程式碼基底的索引鍵可用來直接 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 從任何完整的檔案路徑載入 VSPackage 的組件。 索引鍵的值應該是 DLL 的檔案路徑。 這是最好的方式有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 載入您的封裝組件。 這項技術有時稱為 「 程式碼基底\/私密金鑰安裝目錄技術。 」 在註冊期間的程式碼基底值透過傳遞至註冊屬性類別的執行個體 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> 型別。|  
|將放入 DLL **PrivateAssemblies** 目錄。|將組件中的 **PrivateAssemblies** 子目錄 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 目錄。 組件位於 **PrivateAssemblies** 會自動偵測，但不是會顯示在 **加入參考** 對話方塊。 之間的差異 **PrivateAssemblies** 和 **PublicAssemblies** 是組件中 **PublicAssemblies** 會列舉在 **加入參考** 對話方塊。 如果您選擇不使用 「 私用程式碼基底\/安裝目錄 」 的技術，則您應安裝到 **PrivateAssemblies** 目錄。|  
|使用強式名稱組件和組件登錄機碼。|組件金鑰可用來明確導向 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 載入強式名稱為 VSPackage 組件。 索引鍵的值應該是強式名稱組件。|  
|將放入 DLL **PublicAssemblies** 目錄。|最後，組件也可以放入 **PublicAssemblies** 子目錄。 組件位於 **PublicAssemblies** 會自動偵測，也會出現在 **加入參考** 對話方塊 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。<br /><br /> VSPackage 組件應該只放在 **PublicAssemblies** 如果它們包含的目錄管理要由其他 VSPackage 開發人員重複使用的元件。 大部分的組件不符合此準則。|  
  
> [!NOTE]
>  使用強式名稱的所有相依組件的已簽署組件。 這些組件也應該安裝在您的目錄或全域組件快取 \(GAC\) 中。 這樣可防止具有相同的主檔名，所謂的弱式名稱繫結的組件的衝突。