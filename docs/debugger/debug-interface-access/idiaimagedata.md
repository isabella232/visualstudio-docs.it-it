---
description: Espone i dettagli della posizione di base e degli offset di memoria del modulo o dell'immagine.
title: IDiaImageData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData interface
ms.assetid: b696f350-fc08-4352-9287-a15e87512c1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: da217ac40830700bf48968a9ed29821f88f190ec
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074820"
---
# <a name="idiaimagedata"></a>IDiaImageData
Espone i dettagli della posizione di base e degli offset di memoria del modulo o dell'immagine.

## <a name="syntax"></a>Sintassi

```
IDiaImageData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
Nella tabella seguente vengono illustrati i metodi di `IDiaImageData` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaImageData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-relativevirtualaddress.md)|Recupera il percorso nella memoria virtuale del modulo relativo all'applicazione.|
|[IDiaImageData::get_virtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-virtualaddress.md)|Recupera la posizione nella memoria virtuale dell'immagine.|
|[IDiaImageData::get_imageBase](../../debugger/debug-interface-access/idiaimagedata-get-imagebase.md)|Recupera la posizione di memoria in cui deve essere basata l'immagine.|

## <a name="remarks"></a>Commenti
Alcuni flussi di debug (XDATA, PDATA) contengono copie dei dati archiviati anche nell'immagine. È possibile eseguire query su questi oggetti dati di flusso per `IDiaImageData` l'interfaccia . Per informazioni dettagliate, vedere la sezione "Note per i chiamanti" in questo argomento.

## <a name="notes-for-callers"></a>Note per i chiamanti
Ottenere questa interfaccia chiamando `QueryInterface` su un [oggetto IDiaEnumDebugStreamData.](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) Si noti che non tutti i flussi di debug supportano `IDiaImageData` l'interfaccia . Ad esempio, attualmente solo i flussi XDATA e PDATA supportano `IDiaImageData` l'interfaccia .

## <a name="example"></a>Esempio
Questo esempio cerca in tutti i flussi di debug qualsiasi flusso che supporta `IDiaImageData` l'interfaccia . Se viene trovato un flusso di questo tipo, vengono visualizzate alcune informazioni su tale flusso.

```C++
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

## <a name="requirements"></a>Requisiti
Intestazione: Dia2.h

Libreria: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
