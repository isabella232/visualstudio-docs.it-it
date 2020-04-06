---
title: MACHINE_INFO_FIELDS . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89a2552bb6a8bea88f54a897b829ab89b30ff413
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714514"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
Specifica il tipo di informazioni da recuperare per una particolare macchina.

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
 Inizializzare/utilizzare `bstrName` il campo nella struttura.

 `MCIF_FLAGS`\
 Inizializzare/utilizzare `Flags` il campo nella struttura.

 `MIF_ALL`\
 Inizializzare/utilizzare tutti i campi nella struttura.

## <a name="remarks"></a>Osservazioni
 Questi valori vengono passati al [metodo GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) per indicare quali membri della struttura [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) devono essere inizializzati.

 Utilizzato anche `Fields` nel membro `MACHINE_INFO` della struttura per indicare quali campi vengono utilizzati e validi.

 Questi flag possono essere combinati `OR`con un oggetto .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
