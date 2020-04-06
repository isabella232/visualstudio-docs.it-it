---
title: Proprietà IDebugProperty3::CreateObjectID . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d3993d674f029260dbe32d16c576cb239ff8d6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721180"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Crea un ID univoco per questa proprietà per garantire che sia univoco tra tutte le altre proprietà.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo viene chiamato quando il gestore di debug della sessione desidera assicurarsi che questa proprietà viene identificata in modo univoco tra tutte le altre proprietà. Il motore di debug (DE) supporta questo metodo a meno che le proprietà che gestisce sono già identificate in modo univoco. Se il DE non supporta questo `E_NOTIMPL`metodo, restituisce .

 Qualsiasi ID univoco `CreateObjectID` creato con viene eliminato quando il [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) viene chiamato il metodo; questo segnala anche la fine della necessità di identificare in modo univoco questa proprietà.

> [!NOTE]
> Non esiste alcun metodo per recuperare questo ID univoco, in modo che `CreateObjectID` il DE può eseguire tutte le opzioni desiderate per ID univoci quando viene chiamato il metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
