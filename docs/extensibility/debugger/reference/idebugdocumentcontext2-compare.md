---
description: Confronta il contesto del documento con una determinata matrice di contesti di documento.
title: IDebugDocumentContext2::Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa10a5dbaf141def906705dfb84dfa2b95f216e9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089251"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Confronta il contesto del documento con una determinata matrice di contesti di documento.

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
[in] Valore [dell'enumerazione DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) che specifica il tipo di confronto.

`rgpDocContextSet`\
[in] Matrice di oggetti [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) che rappresentano i contesti di documento confrontati.

`dwDocContextSetLen`\
[in] Lunghezza della matrice di contesti di documento da confrontare.

`pdwDocContext`\
[out] Restituisce l'indice nella matrice del primo contesto del documento che soddisfa `rgpDocContextSet` il confronto.

## <a name="return-value"></a>Valore restituito
 Restituisce `S_OK` se è stata trovata una corrispondenza. Restituisce `S_FALSE` se non è stata trovata alcuna corrispondenza. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Gli [oggetti IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) passati nella matrice devono essere implementati dallo stesso motore di debug che implementa l'oggetto chiamato; in caso contrario, il confronto `IDebugDocumentContext2` non è valido.

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
