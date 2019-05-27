---
title: IDebugDocumentContext2::Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 037dc4232753bbae8e15a0a2cf4bd42781910cb9
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204719"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Confronta questo contesto di documento in una matrice specificata di contesti di documento.

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
[in] Un valore compreso il [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) enumerazione che specifica il tipo di confronto.

`rgpDocContextSet`\
[in] Matrice di [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) gli oggetti che rappresentano i contesti di documento cui è confrontati.

`dwDocContextSetLen`\
[in] La lunghezza della matrice di contesti di documento da confrontare.

`pdwDocContext`\
[out] Restituisce l'indice nel `rgpDocContextSet` matrice del contesto del documento prima che soddisfa il confronto.

## <a name="return-value"></a>Valore restituito
 Restituisce `S_OK` se è stata trovata una corrispondenza. Restituisce `S_FALSE` se è stata trovata alcuna corrispondenza. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 Il [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) oggetti che vengono passati nella matrice devono essere implementati dallo stesso motore di debug che implementa il `IDebugDocumentContext2` oggetto chiamato; in caso contrario, il confronto non è valido.

## <a name="see-also"></a>Vedere anche
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)