---
description: Questa interfaccia registrata consente a Gestione debug sessione (SDM) di ottenere informazioni sui programmi pubblicati tramite l'interfaccia IDebugProgramPublisher2.
title: Interfaccia IDebugProgramProvider2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 44eca905c761fceae02f879f8891098f9d6932c9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050520"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Questa interfaccia registrata consente a Gestione debug sessione (SDM) di ottenere informazioni sui programmi che sono stati "pubblicati" tramite [l'interfaccia IDebugProgramPublisher2.](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)

## <a name="syntax"></a>Sintassi

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
Il motore di debug implementa questa interfaccia per fornire informazioni sui programmi di cui è in corso il debug. Questa interfaccia viene registrata nella sezione DE del Registro di sistema usando la metrica `metricProgramProvider` , come descritto in Helper SDK per il [debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="notes-for-callers"></a>Note per i chiamanti
Chiamare la funzione `CoCreateInstance` com con il del provider di programmi ottenuto dal Registro di `CLSID` sistema. Vedere l'esempio.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable

|Metodo|Descrizione|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Ottiene informazioni sui programmi in esecuzione, filtrati in diversi modi.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Ottiene un nodo di programma, dato un ID processo specifico.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Stabilisce un callback per controllare gli eventi del provider associati a tipi specifici di processi.|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Stabilisce le impostazioni locali per tutte le risorse specifiche della lingua necessarie per il de.|

## <a name="remarks"></a>Commenti
In genere, un processo usa questa interfaccia per ottenere informazioni sui programmi in esecuzione in tale processo.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Esempio

```cpp
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugProgramProvider2 *pProvider = NULL;
    if (pDebugEngineGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetMetric(NULL,
                    metrictypeEngine,
                    *pDebugEngineGuid,
                    metricProgramProvider,
                    &clsidProvider,
                    strRegistrationRoot);
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugProgramProvider2> spProgramProvider;
            spProgramProvider.CoCreateInstance(clsidProvider);
            if (spProgramProvider != NULL) {
                pProvider = spProgramProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
