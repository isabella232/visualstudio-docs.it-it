---
title: Proprietà IDebugProgramProvider2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43557e5d81e5140967a1189e57a350595d0f7220
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721700"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Questa interfaccia registrata consente al gestore di sessione di debug (SDM) di ottenere informazioni sui programmi che sono stati "pubblicati" tramite il [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) interfaccia.

## <a name="syntax"></a>Sintassi

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
Il motore di debug (DE) implementa questa interfaccia per fornire informazioni sui programmi in fase di debug. Questa interfaccia viene registrata nella sezione DE `metricProgramProvider`del Registro di sistema utilizzando la metrica , come descritto in [SDK Helpers for Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="notes-for-callers"></a>Note per i chiamanti
Chiamare la `CoCreateInstance` funzione di `CLSID` COM con il provider di programmi ottenuto dal Registro di sistema. Vedere l'esempio.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable

|Metodo|Descrizione|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Ottiene informazioni sui programmi in esecuzione, filtrati in diversi modi.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Ottiene un nodo di programma, dato un ID di processo specifico.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Stabilisce un callback per controllare gli eventi del provider associati a tipi specifici di processi.|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Stabilisce un'impostazione locale per tutte le risorse specifiche della lingua necessarie per il DE.|

## <a name="remarks"></a>Osservazioni
Normalmente, un processo utilizza questa interfaccia per scoprire i programmi in esecuzione in quel processo.

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
