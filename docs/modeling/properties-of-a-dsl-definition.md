---
title: "DSL 定義的屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 13
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7a8fc0474f624785a47a4ba9f970b5a1ca54dd9c
ms.lasthandoff: 02/22/2017

---
# <a name="properties-of-a-dsl-definition"></a>DSL 定義的屬性
DslDefinition 屬性會定義*定義域專屬語言*定義屬性，例如版本編號。 DslDefinition 屬性會出現在**屬性**視窗，當您按一下圖表中的開放區域*定義域專屬語言設計工具*。  
  
 如需詳細資訊，請參閱[如何定義定義域專屬語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充定義域專屬語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 DslDefinition 具有下表中的屬性︰  
  
|屬性|說明|預設|  
|--------------|-----------------|-------------|  
|存取修飾詞|決定網域類別的存取修飾詞是公用或內部。|public|  
|自訂屬性|自訂定義網域類別的屬性。<br /><br /> **請注意**用於瀏覽 按鈕新增屬性。|\<無 >|  
|公司名稱|目前的公司名稱，在系統登錄中的名稱。|目前的公司名稱|  
|名稱|這個網域類別的名稱。|目前的名稱|  
|命名空間|與這個網域類別相關的命名空間。|目前的命名空間|  
|封裝 Guid|Guid[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]產生此 dsl 的封裝。|\<無 >|  
|封裝命名空間|命名空間[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]產生此 dsl 的封裝。|\<無 >|  
|產品名稱|要註冊的產品名稱[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]產生此 dsl 的封裝。|\<無 >|  
|備註|這個網域類別相關聯的資訊。|\<無 >|  
|說明|這個網域類別的描述。|\<無 >|  
|顯示名稱|將這個網域類別產生的設計工具中顯示的名稱。|\<無 >|  
|說明關鍵字|這個網域類別相關聯的說明關鍵字。|\<無 >|  
|組建|此定義域專屬語言定義累加組建編號。|0|  
|主要版本|此定義域專屬語言定義增量的主要組建編號。|1|  
|次要版本|此定義域專屬語言定義增量的次要組建編號。|0|  
|修訂|累加修訂建置此定義域專屬語言定義的數字。|0|  
  
## <a name="see-also"></a>另請參閱  
 [定義域專屬語言工具字彙](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
