---
title: Proprietà IDebugDocument2::GetName . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2af7f4dc01ee3a2fe3fb5026602a0b5d4f766b17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731966"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Ottiene il nome del documento in uno dei diversi formati.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetName( 
   GETNAME_TYPE gnType,
   BSTR*        pbstrFileName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE gnType,
   out string        pbstrFileName
);
```

## <a name="parameters"></a>Parametri
`gnType`\
[in] Valore dell'enumerazione [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) che determina il tipo di nome da restituire.

`pbstrFileName`\
[fuori] Restituisce una stringa contenente il nome del documento.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo può, ad esempio, restituire il nome del documento come titolo o come nome file o anche parte di un nome di file.

## <a name="see-also"></a>Vedere anche
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
