---
title: MACHINE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00f1e8ea5487a4eecb6dc9fa1f2b16d18ec3fa07
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458058"
---
# <a name="machineinfofields"></a>MACHINE_INFO_FIELDS
Specifica il tipo di informazioni da recuperare per un computer specifico.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>Campi
 `MCIF_NAME`\
 Initialize/usare la `bstrName` campo nella struttura.

 `MCIF_FLAGS`\
 Initialize/usare la `Flags` campo nella struttura.

 `MIF_ALL`\
 Utilizzo o inizializzare tutti i campi della struttura.

## <a name="remarks"></a>Note
 Questi valori vengono passati per il [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) metodo per indicare i membri della [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) struttura devono essere inizializzate.

 Usato anche nel `Fields` membro del `MACHINE_INFO` struttura per indicare quali campi vengono usati e valido.

 Questi flag possono essere combinati con un bit per bit `OR`.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)