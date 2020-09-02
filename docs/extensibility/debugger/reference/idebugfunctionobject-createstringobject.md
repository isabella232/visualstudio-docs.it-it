---
title: 'IDebugFunctionObject:: CreateStringObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateStringObject
helpviewer_keywords:
- IDebugFunctionObject::CreateStringObject method
ms.assetid: fd6070ab-07d4-4ea1-8d71-b16592d6f1a7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 40a13b9b388caa6a1ae6e3e470e4ea02553fa0ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728526"
---
# <a name="idebugfunctionobjectcreatestringobject"></a>IDebugFunctionObject::CreateStringObject
Crea un oggetto String.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreateStringObject( 
   LPCOLESTR      pcstrString,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObject(
   string      pcstrString,
   out IDebugObject ppOjbect
);
```

## <a name="parameters"></a>Parametri
`pcstrString`\
in Valore stringa per l'oggetto stringa.

`ppObject`\
out Restituisce un oggetto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta l'oggetto stringa appena creato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Chiamare questo metodo per creare un oggetto che rappresenta una stringa che rappresenta un parametro per la funzione rappresentata dall'interfaccia [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="see-also"></a>Vedere anche
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
