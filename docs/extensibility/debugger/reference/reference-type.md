---
description: Specifica il tipo di riferimento.
title: REFERENCE_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- REFERENCE_TYPE
helpviewer_keywords:
- REFERENCE_TYPE enumeration
ms.assetid: b1ffba10-eb9d-48ba-bf48-6d8b71d6f270
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 10348f1b5913fb8d01f0b45f30e66854325af72b271aa39546c22ca752a15f0c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377210"
---
# <a name="reference_type"></a>REFERENCE_TYPE
Specifica il tipo di riferimento.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_REFERENCE_TYPE { 
   REF_TYPE_WEAK   = 0x0001,
   REF_TYPE_STRONG = 0x0002
};
typedef DWORD REFERENCE_TYPE;
```

```csharp
public enum enum_REFERENCE_TYPE { 
   REF_TYPE_WEAK   = 0x0001,
   REF_TYPE_STRONG = 0x0002
};
```

## <a name="fields"></a>Campi
 `REF_TYPE_WEAK`\
 Specifica un riferimento debole. Non può essere combinato con `REF_TYPE_STRONG` .

 `REF_TYPE_STRONG`\
 Specifica un riferimento sicuro. Non può essere combinato con `REF_TYPE_WEAK` .

## <a name="remarks"></a>Commenti
 Utilizzato come `dwRefType` membro della struttura [DEBUG_REFERENCE_INFO.](../../../extensibility/debugger/reference/debug-reference-info.md)

 Passato come parametro al [metodo SetReferenceType.](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)
