---
title: 'IDebugTypeFieldBuilder:: CreatePointerToType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreatePointerToType
- IDebugTypeFieldBuilder::CreatePointerToType
ms.assetid: 73966e8a-b643-43e0-9b4e-0aa4b402ebbe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 871f061df1fdc60362f39fab36136eb71f5d7e50
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718435"
---
# <a name="idebugtypefieldbuildercreatepointertotype"></a>IDebugTypeFieldBuilder::CreatePointerToType
Crea un puntatore al tipo specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreatePointerToType(
   IDebugField*  pTypeField,
   IDebugField** pPtrToTypeField
);
```

```csharp
int CreatePointerToType(
   IDebugField     pTypeField,
   out IDebugField pPtrToTypeField
);
```

## <a name="parameters"></a>Parametri
`pTypeField`\
in Tipo a cui puntare. È rappresentato dall'interfaccia [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

`pPtrToTypeField`\
out Restituisce il puntatore rappresentato da un nuovo oggetto **IDebugField** .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)
