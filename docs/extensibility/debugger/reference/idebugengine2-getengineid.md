---
description: Ottiene il GUID del motore di debug (DE).
title: 'IDebugEngine2:: GetEngineID | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bf785c906303bab677adadfd081ae6af276a754c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153976"
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
Ottiene il GUID del motore di debug (DE).

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetEngineID(
    GUID* pguidEngine
);
```

```csharp
int GetEngineID(
    out Guid pguidEngine
);
```

## <a name="parameters"></a>Parametri
`pguidEngine`\
out Restituisce il GUID dell'oggetto DE.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
Alcuni esempi di GUID tipici sono `guidScriptEng` , `guidNativeEng` o `guidSQLEng` . I nuovi motori di debug creeranno il proprio GUID per l'identificazione.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un `CEngine` oggetto semplice che implementa l'interfaccia [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) .

```cpp
HRESULT CEngine::GetEngineId(GUID *pguidEngine) {
    if (pguidEngine) {
        // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.
        // Other languages would require their own guidDifferentEngine to be
        //defined in the Batdbg.idl file.
        *pguidEngine = guidBatEng;
        return NOERROR; // This is typically S_OK.
    } else {
        return E_INVALIDARG;
    }
}
```

## <a name="see-also"></a>Vedi anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
