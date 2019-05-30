---
title: IDebugField::GetInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 53c0de1b956202f95b4995855ec5bdda0ebe59d3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352623"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Questo metodo ottiene visualizzabile informazioni sul campo.

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
[in] Una combinazione di [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) le costanti che consente di selezionare le informazioni da visualizzare. Se il campo rappresenta un simbolo, si tratta generalmente il nome del simbolo e il tipo.

`pFieldInfo`\
[out] Restituisce le informazioni nella classe fornita [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struttura.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)