---
description: Determina se il campo rappresenta un tipo chiuso.
title: IDebugExtendedField::IsClosedType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47844555c2f900e46dd0218fe3763a877d9fa711b562b5601be8adc27a98b0a9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360365"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Determina se il campo rappresenta un tipo chiuso.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT IsClosedType(
   void
);
```

```csharp
int IsClosedType();
```

## <a name="return-value"></a>Valore restituito
 Se il campo è un tipo chiuso, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` .

## <a name="see-also"></a>Vedi anche
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
