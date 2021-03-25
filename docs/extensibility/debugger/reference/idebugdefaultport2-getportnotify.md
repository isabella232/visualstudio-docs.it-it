---
description: Questo metodo ottiene un'interfaccia IDebugPortNotify2 per questa porta.
title: 'IDebugDefaultPort2:: GetPortNotify | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ed43d96a7035dbd9e75a8e64a23e556997e087c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077473"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Questo metodo ottiene un'interfaccia [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) per questa porta.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>Parametri
`ppPortNotify`\
out Oggetto [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 In genere, il `QueryInterface` metodo viene chiamato sull'oggetto che implementa l'interfaccia [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) per ottenere un'interfaccia [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) . In alcuni casi, tuttavia, l'interfaccia desiderata viene implementata in un oggetto diverso. Questo metodo nasconde tali circostanze e restituisce l' `IDebugPortNotify2` interfaccia dall'oggetto più appropriato.

## <a name="see-also"></a>Vedi anche
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
