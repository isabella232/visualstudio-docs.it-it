---
description: Specifica lo stato dei simboli per un modulo.
title: MODULE_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FLAGS
helpviewer_keywords:
- MODULE_INFO_FLAGS enumeration
ms.assetid: e22d3723-b4d4-4524-8a2f-3adb55bbd273
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 158cc849e32fc0177b784c8898ec83fe58008f60
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222341"
---
# <a name="module_info_flags"></a>MODULE_INFO_FLAGS
Specifica lo stato dei simboli per un modulo.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_MODULE_INFO_FLAGS {
   MIF_SYMBOLS_LOADED = 0x0001
};
typedef DWORD MODULE_INFO_FLAGS;
```

```csharp
public enum enum_MODULE_INFO_FLAGS {
   MIF_SYMBOLS_LOADED = 0x0001
};
```

## <a name="fields"></a>Campi
 `MIF_SYMBOLS_LOADED`\
 Almeno un set di simboli è stato caricato dal modulo. in caso contrario, non sono stati caricati simboli.

## <a name="remarks"></a>Commenti
 Questo valore viene restituito dal metodo [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
