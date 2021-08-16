---
description: Specifica il tipo di confronto per i riferimenti.
title: REFERENCE_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- REFERENCE_COMPARE
helpviewer_keywords:
- REFERENCE_COMPARE enumeration
ms.assetid: e31cdc78-f621-498b-9ca4-aefa790b9f6f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4db5f1189340e93799fc83bfb9f38e7ac1aa92c5222de6da78e27d2aa487c7cf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121276165"
---
# <a name="reference_compare"></a>REFERENCE_COMPARE
Specifica il tipo di confronto per i riferimenti.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_REFERENCE_COMPARE { 
   REF_COMPARE_EQUAL        = 0x0001,
   REF_COMPARE_LESS_THAN    = 0x0002,
   REF_COMPARE_GREATER_THAN = 0x0003
};
typedef DWORD REFERENCE_COMPARE;
```

```csharp
public enum enum_REFERENCE_COMPARE { 
   REF_COMPARE_EQUAL        = 0x0001,
   REF_COMPARE_LESS_THAN    = 0x0002,
   REF_COMPARE_GREATER_THAN = 0x0003
};
```

## <a name="fields"></a>Campi
 `REF_COMPARE_EQUAL`\
 Specifica un confronto uguale a.

 `REF_COMPARE_LESS_THAN`\
 Specifica un confronto minore di.

 `REF_COMPARE_GREATER_THAN`\
 Specifica un confronto maggiore di.

## <a name="remarks"></a>Commenti
 Passato come argomento al [metodo Compare.](../../../extensibility/debugger/reference/idebugreference2-compare.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Confronta](../../../extensibility/debugger/reference/idebugreference2-compare.md)
