---
title: IDebugProperty3::CreateObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee1d2a66a5ed655c132526c5d73b6673a680c971
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339865"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Crea un ID univoco per questa proprietà per assicurarsi che sia univoco tra tutte le altre proprietà.

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
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo viene chiamato quando il gestore di sessione di debug vuole assicurarsi che questa proprietà è identificata in modo univoco tra tutte le altre proprietà. Il motore di debug (DE) supporta questo metodo, a meno che le proprietà che si occupa sono già identificate. Se la Germania non supporta questo metodo, viene restituito `E_NOTIMPL`.

 Qualsiasi ID univoco creato con `CreateObjectID` viene eliminato quando il [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) viene chiamato il metodo; ciò indica anche la fine dell'esigenza di identifica in modo univoco questa proprietà.

> [!NOTE]
> Non è disponibile alcun metodo per recuperare l'ID univoco, in modo che la Germania è possibile eseguire qualsiasi risultato per ID univoci quando la `CreateObjectID` viene chiamato il metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)