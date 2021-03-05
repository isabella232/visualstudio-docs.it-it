---
description: Crea un ID univoco per questa proprietà per assicurarsi che sia univoco tra tutte le altre proprietà.
title: 'IDebugProperty3:: CreateObjectID | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e82e11d83c77131e47d815529813484d2869cdc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171439"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Crea un ID univoco per questa proprietà per assicurarsi che sia univoco tra tutte le altre proprietà.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato quando il gestore di debug della sessione vuole assicurarsi che questa proprietà sia identificata in modo univoco tra tutte le altre proprietà. Il motore di debug (DE) supporta questo metodo, a meno che le proprietà che gestisce non siano già identificate in modo univoco. Se il DE non supporta questo metodo, restituisce `E_NOTIMPL` .

 Qualsiasi ID univoco creato con `CreateObjectID` viene eliminato definitivamente quando viene chiamato il metodo [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) , che segnala anche la fine della necessità di identificare in modo univoco questa proprietà.

> [!NOTE]
> Non esiste alcun metodo per recuperare questo ID univoco, quindi il DE può eseguire qualsiasi tipo di ID univoco quando `CreateObjectID` viene chiamato il metodo.

## <a name="see-also"></a>Vedi anche
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
