---
title: "點陣圖的項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "點陣圖，VSCT XML 結構描述項目"
  - "點陣圖項目 (VSCT XML 結構描述)"
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# 點陣圖的項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定義點陣圖。 從資源，或是從檔案載入點陣圖。  
  
## 語法  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|guid|必要項。 GUID ID 的命令識別項的 GUID。<br /><br /> 無法與任何 VSPackage 或其他命令群組 guid 屬性的點陣圖。  它應該是唯一點陣圖定義，且不應用於其他用途。|  
|resID|GUID ID 的命令識別項的識別碼。 需要 resID 或 href 屬性。<br /><br /> ResID 屬性會是決定要在合併命令 table 從中載入點陣圖區整數資源識別碼。  載入命令資料表時，將會從相同的模組資源載入資源識別碼所指定的點陣圖。|  
|usedList|需要 resID 屬性是否存在。 選取可用的映像中的點陣圖區。|  
|href|點陣圖的路徑。 需要 resID 或 href 屬性。<br /><br /> 指定映像檔，這個檔案內嵌在產生的二進位搜尋 include 路徑。  命令資料表合併期間，複製映像，並不需要任何額外的資源查閱或負載。  如果 usedList 屬性不存在，則在區域中的所有映像。 **Note:**  映像可能包括.bmp、.png 與.gif 的幾種格式之一來提供。  較早版本的編譯器不支援具有 alpha 資訊為部分透明的 32 位元點陣圖影像。 這些版本的因應措施是使用.png 格式。|  
|條件|選擇項。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[點陣圖的項目](../extensibility/bitmaps-element.md)|分組點陣圖項目。|  
  
## 範例  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" /> <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS" usedList="1, 2, 3, 4"/>  
```  
  
## 請參閱  
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)