---
title: "Icon 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML 結構描述元素，但是圖示"
  - "Icon 項目 (VSCT XML 結構描述)"
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Icon 項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

圖示標記的 guid 屬性是定義點陣圖的 guid。  Id 屬性選取點陣圖區中的位置。 這是選擇性的項目。  如果省略此元素的值 **guidOfficeIcon:msotcidNoIcon** 會隱含。  
  
## 語法  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|guid|必要項。 定義點陣圖的 guid。|  
|id|必要項。 選取該位置中的點陣圖區。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|無。|無。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[按鈕項目](../extensibility/buttons-element.md)||  
  
## 請參閱  
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)