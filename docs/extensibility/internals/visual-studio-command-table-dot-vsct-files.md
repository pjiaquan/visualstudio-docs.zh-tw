---
title: "Visual Studio 命令資料表 (。Vsct) 檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT 檔案、 概觀"
  - "Visual Studio 命令資料表設定檔 (VSCT)、 概觀"
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Visual Studio 命令資料表 (。Vsct) 檔案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

命令資料表的組態檔是說明命令的 VSPackage 包含一組文字檔案。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 資料表 \(VSCT\) 編譯器會以 XML 為基礎的組態檔 \(.vsct 檔\) 編譯成二進位命令資料表 \(.cto\) 輸出檔的命令。 結果.cto 檔案並建立所使用的命令資料表 \(CTC\) 編譯器來編譯.ctc 組態檔相同。 不過，以 XML 為基礎的.vsct 檔案有一些優點，例如 XML 編輯器和 XML IntelliSense。  
  
 若要深入了解的語法和語意 \(semantics\).vsct 檔案，請參閱 [設計 XML 命令資料表 \(。Vsct\) 檔案](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## 在本節中  
 [設計 XML 命令資料表 \(。Vsct\) 檔案](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 描述如何設計.vsct 檔案。  
  
 [如何: 建立。Vsct 檔案](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 比較建立.vsct 檔的方法。 描述手動建立新的.vsct 檔的程序。  
  
## 相關章節  
 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)  
 提供有關每個區段的命令資料表的 XML 組態檔的詳細資料。  
  
 [Command Table Configuration \(.Ctc\) Files](http://msdn.microsoft.com/zh-tw/3413dda1-f372-4669-bcf0-c64d3463842c)  
 提供已被取代的.ctc 檔案格式的概觀。  
  
 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 描述命令資料表格式規格。  
  
 [在 Vspackage 中的資源](../../extensibility/internals/resources-in-vspackages.md)  
 描述如何使用 managed VSPackages 中的 managed 和 unmanaged 資源。  
  
 [命令、 功能表和工具列](../../extensibility/internals/commands-menus-and-toolbars.md)  
 說明如何建立包含功能表、 工具列和命令的下拉式方塊的 UI。