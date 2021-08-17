---
description: Consente ai motori di debug di leggere le impostazioni delle metriche in modalità remota.
title: IDebugSettingsCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: babc486a4c8d683a3557b602273bc2e165a49420
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126258"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Consente ai motori di debug di leggere le impostazioni delle metriche in modalità remota.

## <a name="syntax"></a>Sintassi

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
Questa interfaccia viene implementata dal callback degli eventi della gestione del debug della sessione e utilizzata dai motori di debug. Può anche essere usato in locale al posto di Dbgmetric[d].lib.

## <a name="methods"></a>Metodi
Nella tabella seguente vengono illustrati i metodi di `IDebugSettingsCallback2` .

|Metodo|Descrizione|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Enumera gli analizzatori di espressioni disponibili in base alla lingua e all'identificatore del fornitore.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Recupera un oggetto locale dell'analizzatore di espressioni in base alla metrica.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Recupera un valore che corrisponde alla metrica specificata dell'analizzatore di espressioni.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Recupera il file delle metriche dell'analizzatore di espressioni in base al nome o alla metrica.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Recupera l'identificatore univoco per una metrica dell'analizzatore di espressioni in base al nome.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Recupera la stringa del valore di una metrica dell'analizzatore di espressioni in base al nome.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Recupera il valore di una metrica in base al nome.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Recupera l'identificatore univoco di una metrica in base al nome.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Recupera la stringa del valore della metrica in base al nome.|

## <a name="requirements"></a>Requisiti
Intestazione: Msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Esempio
L'esempio seguente illustra una funzione che accetta un **oggetto IDebugSettingsCallback2** come parametro.

```cpp
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)
{
    HRESULT hRes = E_FAIL;

    if ( ppCallback )
    {
        if ( EVAL(m_pdec) )
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```
