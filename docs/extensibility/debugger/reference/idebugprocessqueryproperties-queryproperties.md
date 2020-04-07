---
title: Proprietà IDebugProcessQueryProperties::QueryProperties . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties::QueryProperties
ms.assetid: 976a9962-b689-45bb-afb6-16b2c5dbc3b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4daac369485febe38e3366d413985bda90b30f05
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723326"
---
# <a name="idebugprocessquerypropertiesqueryproperties"></a>IDebugProcessQueryProperties::QueryProperties
Questo metodo esegue una query per i valori di proprietà specificati del processo di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT QueryProperties(
   ULONG                  celt,
   PROCESS_PROPERTY_TYPE *rgdwPropTypes,
   VARIANT               *rgtPropValues);
```

```csharp
int QueryProperties(
   uint                       celt,
   enum_PROCESS_PROPERTY_TYPE rgdwPropTypes,
   out object[ ]              rgtPropValues);
```

## <a name="parameters"></a>Parametri
`celt`\
[in] Dimensione delle matrici contenenti le definizioni di proprietà e i valori delle proprietà.

`dwPropType`\
[in] Matrice che contiene le definizioni delle proprietà sottoposte a query. I valori possibili sono:

- PROCESS_PROPERTY_COMMAND_LINE n. 1

- PROCESS_PROPERTY_CURRENT_DIRECTORY 2

- PROCESS_PROPERTY_ENVIRONMENT_VARIABLES n. 3

`pvarPropValue`\
[fuori] Matrice contenente i valori delle proprietà.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo viene utilizzato raramente.

## <a name="see-also"></a>Vedere anche
- [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)
