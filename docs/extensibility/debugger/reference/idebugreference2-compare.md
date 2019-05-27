---
title: IDebugReference2::Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5d1f1f4b31317e79c497e1b13dcd7e218ecd16b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212987"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Confronta un riferimento a un altro. Riservato per usi futuri.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Compare ( 
   REFERENCE_COMPARE dwCompare,
   IDebugReference2* pReference
);
```

```csharp
int Compare ( 
   enum_REFERENCE_COMPARE dwCompare,
   IDebugReference2       pReference
);
```

## <a name="parameters"></a>Parametri
`dwCompare`\
[in] Un valore compreso il [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) enumerazione che specifica l'operazione di confronto, ad esempio, maggiore o uguale a, minore di.

`pReference`\
[in] Un' [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) che rappresenta il riferimento da confrontare all'oggetto.

## <a name="return-value"></a>Valore restituito
 Restituisce sempre `E_NOTIMPL`.

## <a name="see-also"></a>Vedere anche
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)