---
description: Crea un ID univoco per questa proprietà per assicurarsi che sia univoco tra tutte le altre proprietà.
title: IDebugProperty3::CreateObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8072bc2d7689677b27ccc3ef63f6d9176927603c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063980"
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
 Questo metodo viene chiamato quando la gestione del debug della sessione desidera assicurarsi che questa proprietà sia identificata in modo univoco tra tutte le altre proprietà. Il motore di debug supporta questo metodo, a meno che le proprietà che gestisce non siano già identificate in modo univoco. Se DE non supporta questo metodo, restituisce `E_NOTIMPL` .

 Qualsiasi ID univoco creato con viene eliminato definitivamente quando viene chiamato il metodo `CreateObjectID` [DestroyObjectID,](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) segnalando anche la fine della necessità di identificare in modo univoco questa proprietà.

> [!NOTE]
> Non esiste alcun metodo per recuperare questo ID univoco, quindi de può eseguire qualsiasi operazione per gli ID univoci quando viene `CreateObjectID` chiamato il metodo .

## <a name="see-also"></a>Vedi anche
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
