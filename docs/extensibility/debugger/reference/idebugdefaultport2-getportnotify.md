---
description: Questo metodo ottiene un'interfaccia IDebugPortNotify2 per questa porta.
title: IDebugDefaultPort2::GetPortNotify | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 96a8f103a3df275657dc191183873353c7be620f1819e7950a342e5dcf12bcb9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377730"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Questo metodo ottiene [un'interfaccia IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) per questa porta.

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
[out] Oggetto [IDebugPortNotify2.](../../../extensibility/debugger/reference/idebugportnotify2.md)

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 In genere, `QueryInterface` il metodo viene chiamato sull'oggetto che implementa l'interfaccia [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) per ottenere [un'interfaccia IDebugPortNotify2.](../../../extensibility/debugger/reference/idebugportnotify2.md) Esistono tuttavia casi in cui l'interfaccia desiderata viene implementata in un oggetto diverso. Questo metodo nasconde tali circostanze e restituisce `IDebugPortNotify2` l'interfaccia dall'oggetto più appropriato.

## <a name="see-also"></a>Vedi anche
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
