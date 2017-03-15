---
title: "準備 Windows Installer 部署擴充功能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "vsix msi"
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 準備 Windows Installer 部署擴充功能
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您無法使用 Windows Installer 封裝 \(MSI\) 來部署 VSIX 套件。 不過，您可以擷取 MSI 部署的 VSIX 套件的內容。 本文件說明如何準備其預設輸出會是 VSIX 套件加入安裝專案中的專案。  
  
## 準備 Windows Installer 部署擴充功能專案  
 新的擴充功能專案上執行這些步驟，才能將新增到安裝專案。  
  
#### 若要準備將 Windows Installer 部署擴充功能專案  
  
1.  建立 VSPackage、 MEF 元件、 編輯器裝飾或其他包含 VSIX 資訊清單的擴充性專案類型。  
  
2.  程式碼編輯器中開啟 VSIX 資訊清單。  
  
3.  設定 VSIX 資訊清單的 InstalledByMsi 項目 `true`。 如需 VSIX 資訊清單的詳細資訊，請參閱 [VSIX 擴充功能 2.0 結構描述參考](../extensibility/vsix-extension-schema-2-0-reference.md)。  
  
     這可防止 VSIX 安裝程式嘗試安裝的元件。  
  
4.  中的專案上按一下滑鼠右鍵 **方案總管\] 中** 按一下 **屬性**。  
  
5.  選取 **VSIX** \] 索引標籤。  
  
6.  核取方塊標示為 **到下列位置複製 VSIX 內容** 輸入其中安裝專案會自動挑選檔案的路徑。  
  
## 從現有的 VSIX 套件解壓縮檔案  
 執行這些步驟，您不需要原始程式檔時，將現有的 VSIX 套件的內容加入至安裝專案。  
  
#### 若要從現有的 VSIX 套件解壓縮檔案  
  
1.  重新命名。VSIX 檔案，其中包含來自的延伸模組 *filename*至.vsix *filename*.zip。  
  
2.  將.zip 檔案的內容複製到目錄。  
  
3.  從目錄刪除 \[Content\_types\].xml 檔案。  
  
4.  先前的程序中所示，請編輯 VSIX 資訊清單。  
  
5.  將其餘的檔案加入至安裝專案。  
  
## 請參閱  
 [Visual Studio Installer Deployment](http://msdn.microsoft.com/zh-tw/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Walkthrough: Creating a Custom Action](http://msdn.microsoft.com/zh-tw/4bd4b63a-2b91-431e-839c-5752443f0eaf)