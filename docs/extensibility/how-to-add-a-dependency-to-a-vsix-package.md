---
title: "如何︰ 將相依性加入至 VSIX 套件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "封裝參考"
  - "封裝組件"
  - "封裝 dll"
  - "vsix 參考"
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何︰ 將相依性加入至 VSIX 套件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以設定安裝中不存在目標電腦上的所有相依性的 VSIX 套件部署。 若要完成此動作，包含 VSIX 相依性，source.extension.vsixmanifest 檔案。  
  
#### 若要新增的相依性  
  
1.  開啟 source.extension.vsixmanifest 檔案中的 **設計** 檢視。 移至 **相依性** \] 索引標籤上，按一下 \[ **新增**。  
  
2.  若要將已安裝的擴充功能︰ 在 **加入新的相依性** 對話方塊中，選取 **安裝擴充功能** 然後， **名稱**, ，選取擴充功能清單上的。  
  
3.  若要新增另一個未安裝的 VSIX:: 中 **加入新的相依性** 對話方塊中，選取 **檔案系統上** ，然後使用 **瀏覽** \] 按鈕以選取的 VSIX。  
  
## 請參閱  
 [VSIX 擴充功能 1.0 結構描述參考](http://msdn.microsoft.com/zh-tw/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [VSIX 套件的剖析](../extensibility/anatomy-of-a-vsix-package.md)   
 [準備 Windows Installer 部署擴充功能](../extensibility/preparing-extensions-for-windows-installer-deployment.md)