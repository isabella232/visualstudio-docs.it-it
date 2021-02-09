---
title: 'IDebugDocumentContext2:: compare | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 959d909d0c777110905aff3b11c8c29d27d628dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880762"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Confronta questo contesto del documento con una matrice specificata di contesti di documento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Compare( 
   DOCCONTEXT_COMPARE       compare,
   IDebugDocumentContext2** rgpDocContextSet,
   DWORD                    dwDocContextSetLen,
   DWORD*                   pdwDocContext
);
```

```csharp
int Compare( 
   enum_ DOCCONTEXT_COMPARE compare,
   IDebugDocumentContext2[] rgpDocContextSet,
   uint                     dwDocContextSetLen,
   out uint                 pdwDocContext
);
```

## <a name="parameters"></a>Parametri
`compare`\
in Valore dell'enumerazione [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) che specifica il tipo di confronto.

`rgpDocContextSet`\
in Matrice di oggetti [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) che rappresentano i contesti di documento confrontati con.

`dwDocContextSetLen`\
in Lunghezza della matrice dei contesti di documento da confrontare.

`pdwDocContext`\
out Restituisce l'indice nella `rgpDocContextSet` matrice del primo contesto del documento che soddisfa il confronto.

## <a name="return-value"></a>Valore restituito
 Restituisce `S_OK` se è stata trovata una corrispondenza. Restituisce `S_FALSE` se non è stata trovata alcuna corrispondenza. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Gli oggetti [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) passati nella matrice devono essere implementati dallo stesso motore di debug che implementa l' `IDebugDocumentContext2` oggetto su cui viene chiamato il metodo; in caso contrario, il confronto non è valido.

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
