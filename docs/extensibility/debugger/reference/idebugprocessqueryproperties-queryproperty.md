---
title: Proprietà IDebugProcessQueryProperties::QueryProperty . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties::QueryProperty
ms.assetid: 9a91707d-a590-44ef-b122-69d9816a7a79
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b190d7ed1d3690be898334270bbd1d16584b81a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723290"
---
# <a name="idebugprocessquerypropertiesqueryproperty"></a>IDebugProcessQueryProperties::QueryProperty
Questo metodo esegue una query per un valore di proprietà specificato del processo di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT QueryProperty(
   PROCESS_PROPERTY_TYPE  dwPropType,
   VARIANT               *pvarPropValue);
```

```csharp
int QueryProperty(
   enum_PROCESS_PROPERTY_TYPE dwPropType,
   out object                 pvarPropValue);
```

## <a name="parameters"></a>Parametri
`dwPropType`\
[in] Definizione della proprietà interrogata. I valori possibili sono:

- PROCESS_PROPERTY_COMMAND_LINE n. 1

- PROCESS_PROPERTY_CURRENT_DIRECTORY 2

- PROCESS_PROPERTY_ENVIRONMENT_VARIABLES n. 3

`pvarPropValue`\
[out] Valore della proprietà.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo viene utilizzato raramente.

## <a name="see-also"></a>Vedere anche
- [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)
