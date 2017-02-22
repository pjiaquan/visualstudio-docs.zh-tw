---
title: "IDiaImageData | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaImageData 介面"
ms.assetid: b696f350-fc08-4352-9287-a15e87512c1e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaImageData
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

公開 \(expose\) 基底的位置和記憶體位移的模組或映像的詳細資料。  
  
## 語法  
  
```  
IDiaImageData : IUnknown  
```  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDiaImageData`。  
  
|方法|描述|  
|--------|--------|  
|[IDiaImageData::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-relativevirtualaddress.md)|擷取虛擬記憶體中的位置，相對於應用程式的模組。|  
|[IDiaImageData::get\_virtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-virtualaddress.md)|擷取虛擬記憶體中之影像的位置。|  
|[IDiaImageData::get\_imageBase](../../debugger/debug-interface-access/idiaimagedata-get-imagebase.md)|擷取映像應該進行計算的記憶體位置。|  
  
## 備註  
 有些偵錯資料流 \(XDATA、 PDATA\) 包含複本亦儲存映像中的資料。  這些資料流物件，請查詢取得的資料`IDiaImageData`介面。  請參閱本主題，如需詳細資訊的 「 備忘稿的呼叫端 」 一節。  
  
## 呼叫者的備忘稿  
 取得這個介面，藉由呼叫`QueryInterface`的[IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)物件。  請注意，並非所有偵錯資料流處理的支援`IDiaImageData`介面。  例如，目前只有 XDATA 和 PDATA 資料流支援`IDiaImageData`介面。  
  
## 範例  
 這個範例會搜尋所有的偵錯資料流，任何支援的資料流的`IDiaImageData`介面。  如果找到這類的資料流，則會顯示此資料流中的一些資訊。  
  
```cpp#  
void ShowImageData(IDiaSession *pSession)  
{  
    if (pSession != NULL)  
    {  
        CComPtr<IDiaEnumDebugStreams> pStreamsList;  
        HRESULT hr;  
  
        hr = pSession->getEnumDebugStreams(&pStreamsList);  
        if (SUCCEEDED(hr))  
        {  
            LONG numStreams = 0;  
            hr = pStreamsList->get_Count(&numStreams);  
            if (SUCCEEDED(hr))  
            {  
                ULONG fetched = 0;  
                for (LONG i = 0; i < numStreams; i++)  
                {  
                    CComPtr<IDiaEnumDebugStreamData> pStream;  
                    hr = pStreamsList->Next(1,&pStream,&fetched);  
                    if (fetched == 1)  
                    {  
                        CComPtr<IDiaImageData> pImageData;  
                        hr = pStream->QueryInterface(__uuidof(IDiaImageData),  
                                                     (void **)&pImageData);  
                        if (SUCCEEDED(hr))  
                        {  
                            CComBSTR name;  
                            hr = pStream->get_name(&name);  
                            if (SUCCEEDED(hr))  
                            {  
                                wprintf(L"Stream %s:\n",(BSTR)name);  
                            }  
                            else  
                            {  
                                wprintf(L"Failed to get name of stream\n");  
                            }  
  
                            ULONGLONG imageBase = 0;  
                            if (pImageData->get_imageBase(&imageBase) == S_OK)  
                            {  
                                wprintf(L"  image base = 0x%0I64x\n",imageBase);  
                            }  
  
                            DWORD relVA = 0;  
                            if (pImageData->get_relativeVirtualAddress(&relVA) == S_OK)  
                            {  
                                wprintf(L"  relative virtual address = 0x%08lx\n",relVA);  
                            }  
  
                            ULONGLONG va = 0;  
                            if (pImageData->get_virtualAddress(&va) == S_OK)  
                            {  
                                wprintf(L"  virtual address = 0x%0I64x\n", va);  
                            }  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia80.dll  
  
## 請參閱  
 [介面 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)