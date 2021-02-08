---
title: 'IDebugPortSupplier3:: EnumPersistedPorts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 09b1fabaeb5bf887eedaa53d57bdeb3604bf2257
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840327"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
Questo metodo recupera un oggetto che consente l'enumerazione dell'elenco di porte rese permanente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumPersistedPorts(
   BSTR_ARRAY         PortNames,
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPersistedPorts(
   BSTR_ARRAY           PortNames,
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>Parametri
`PortNames`\
in Struttura di [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) contenente un elenco di nomi di porte da trovare e restituire tra le porte salvate in modo permanente. Verranno restituite solo le porte salvate in permanenza con questi nomi.

`ppEnum`\
out Oggetto che implementa l'interfaccia [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Le porte rese disponibili vengono caricate quando viene creata un'istanza di un fornitore di porte e salvate quando il fornitore della porta viene eliminato definitivamente.

## <a name="see-also"></a>Vedi anche
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)
