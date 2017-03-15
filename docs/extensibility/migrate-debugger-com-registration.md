---
title: "移轉 64 位元偵錯工具 COM 類別登錄 |Microsoft 文件"
ms.custom: 
ms.date: 11/10/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
caps.latest.revision: 1
author: gregg-miskelly
ms.author: greggm
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
ms.openlocfilehash: e273f31cb1f43ff79fd9a4ade37d112351dea9b5
ms.lasthandoff: 02/22/2017

---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>移轉 64 位元偵錯工具的 COM 類別登錄

>**注意︰**這份文件為初步資訊而且根據 Visual Studio 2017 RC 版本。

偵錯工具擴充功能的 （藉由使用 regasm，regsvr32，或直接寫入登錄），在 HKEY_CLASSES_ROOT 登錄 COM 類別，並載入 msvsmon.exe （遠端偵錯工具），您就可以提供此註冊，以 msvsmon 而不需要撰寫至 HKEY_CLASSES_ROOT。 這會影響舊版的.NET 偵錯工具運算式評估工具或已設定為 msvsmon.exe 程序中載入的偵錯引擎。

## <a name="msvsmon-comclass-def"></a>msvsmon-comclass def

若要使用這項技術，將 *.msvsmon-comclass-def.json 檔案旁 msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64)。

以下是範例 msvsmon-comclass def 檔註冊其中一個受管理和一個原生類別︰

檔案名稱︰ MyCompany.MyExample.msvsmon comclass def.json

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```

