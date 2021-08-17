---
description: Questo metodo determina se questa porta si trova nel computer locale.
title: IDebugDefaultPort2::QueryIsLocal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: c84e7d52425b6060995d7713e4aee72d931d894d9a9afc6e100c6d408d4d442f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121292728"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
Questo metodo determina se questa porta si trova nel computer locale.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Valore restituito
 Restituisce se questa porta è locale (nello stesso computer del chiamante) o `S_OK` se la porta si trova in un altro `S_FALSE` computer.

## <a name="see-also"></a>Vedi anche
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
