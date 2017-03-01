---
title: "註冊單一檔案產生器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 239f68b8bdbaf910f25b9fbe6e0fdd7061fe0f16
ms.lasthandoff: 02/22/2017

---
# <a name="registering-single-file-generators"></a>註冊單一檔案產生器
若要啟用自訂工具在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，必須註冊，因此[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可以具現化，並將它關聯的特定專案類型。  
  
### <a name="to-register-a-custom-tool"></a>若要註冊自訂工具  
  
1.  請註冊自訂工具 DLL 中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]本機登錄或在系統登錄中，其內。  
  
     例如，以下是 managed MSDataSetGenerator 自訂工具，隨附的註冊資訊[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  建立所需的登錄機碼[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]下產生器的 hive\\*GUID*其中*GUID* GUID 定義特定語言專案系統或服務。 索引鍵的名稱會變成您的自訂工具的程式設計名稱。 自訂工具的索引鍵具有下列值︰  
  
    -   (預設值)  
  
         選擇項。 提供自訂工具的使用者易記描述。 這個參數是選擇性的但建議使用。  
  
    -   CLSID  
  
         必要項。 指定的類別庫實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> COM 元件的識別碼  
  
    -   GeneratesDesignTimeSource  
  
         必要項。 指出是否從這個自訂工具所產生的檔案類型就可以使用視覺化設計工具。 此參數的值必須是型別不適用於視覺化設計工具 （零） 0 或提供給視覺化設計工具的型別 (one) 1。  
  
    > [!NOTE]
    >  您必須註冊自訂的工具，分別為每個想自訂的工具，使其可用的語言。  
  
     例如，MSDataSetGenerator 將自己註冊一次針對每種語言︰  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{e6fdf8b0-f3d1-11d4-8576-0002a516ece8}\MSDataSetGenerator]  
    @="Microsoft J# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator></xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [實作單一檔案產生器](../../extensibility/internals/implementing-single-file-generators.md)   
 [決定專案的預設命名空間](../../misc/determining-the-default-namespace-of-a-project.md)   
 [公開型別，以視覺化設計工具](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [BuildManager 物件簡介](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
