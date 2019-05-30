---
title: IDebugSettingsCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 859522ebdbe231146c73b25c5e4c92fba9809727
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321947"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Consente di eseguire il debug motori per leggere le impostazioni delle metriche in modalità remota.

## <a name="syntax"></a>Sintassi

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
Questa interfaccia viene implementata dal callback di evento del gestore di debug della sessione e usata da motori di debug. Potrebbe anche essere usata in locale anziché con estensione LIB Dbgmetric [d].

## <a name="methods"></a>Metodi
Nella tabella seguente sono illustrati i metodi di `IDebugSettingsCallback2`.

|Metodo|Descrizione|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Enumera gli analizzatori di espressioni disponibili assegnati gli identificatori di lingua e il fornitore.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Recupera un oggetto locale dell'analizzatore di espressioni espressione dato la metrica.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Recupera un valore che corrisponde alla metrica dell'analizzatore di espressioni specificata.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Recupera il file di metrica dell'analizzatore di espressioni espressione stato assegnato il nome o la metrica.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Recupera l'identificatore univoco per una metrica dell'analizzatore di espressioni in base al nome.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Recupera la stringa del valore di una metrica dell'analizzatore di espressione in base al nome.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Recupera il valore di una metrica in base al nome.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Recupera l'identificatore univoco di una metrica in base al nome.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Recupera la stringa del valore della metrica in base al nome.|

## <a name="requirements"></a>Requisiti
Intestazione: Msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrata una funzione che accetta un **IDebugSettingsCallback2** oggetto come parametro.

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
