---
title: IDebugDocumentContext2::Compare Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0e46f765c8e4c0e12c3bb9447e0713919fae7b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731887"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Confronta questo contesto del documento con una matrice specificata di contesti del documento.

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
[in] Valore dell'enumerazione [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) che specifica il tipo di confronto.

`rgpDocContextSet`\
[in] Matrice di [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) oggetti che rappresentano i contesti del documento confrontati.

`dwDocContextSetLen`\
[in] Lunghezza della matrice di contesti di documento da confrontare.

`pdwDocContext`\
[fuori] Restituisce l'indice nella `rgpDocContextSet` matrice del primo contesto del documento che soddisfa il confronto.

## <a name="return-value"></a>Valore restituito
 Restituisce `S_OK` se è stata trovata una corrispondenza. Restituisce `S_FALSE` se non è stata trovata alcuna corrispondenza. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Osservazioni
 Gli oggetti [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) passati nella matrice devono essere implementati `IDebugDocumentContext2` dallo stesso motore di debug che implementa l'oggetto su cui viene chiamato; in caso contrario, il confronto non è valido.

## <a name="see-also"></a>Vedere anche
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
