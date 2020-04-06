---
title: Proprietà IDebugProcess2::Detach . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9036ebc44835ab6c3ebd08b9fad4408d9cb97461
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724121"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
Disconnette il debugger da questo processo disconnettendo tutti i programmi nel processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Tutti i programmi e il processo continuano a essere eseguiti, ma non fanno più parte della sessione di debug. Al termine dell'operazione di disconnessione, non verranno inviati più eventi di debug per questo processo (e i relativi programmi).

## <a name="see-also"></a>Vedere anche
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
