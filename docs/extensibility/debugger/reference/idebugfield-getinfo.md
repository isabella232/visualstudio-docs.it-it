---
title: 'IDebugField:: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 21d80f222bdea8a8e17a9b74eefb7885cab0c289
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869908"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Questo metodo ottiene informazioni visualizzabili sul campo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetInfo( 
   FIELD_INFO_FIELDS dwFields,
   FIELD_INFO* pFieldInfo
);
```

```csharp
int GetInfo(
   enum_FIELD_INFO_FIELDS dwFields,
   FIELD_INFO[] pFieldInfo
);
```

## <a name="parameters"></a>Parametri
`dwFields`\
in Combinazione di [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) costanti che seleziona le informazioni da visualizzare. Se il campo rappresenta un simbolo, si tratta in genere del nome e del tipo del simbolo.

`pFieldInfo`\
out Restituisce le informazioni nella struttura [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) fornita.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
