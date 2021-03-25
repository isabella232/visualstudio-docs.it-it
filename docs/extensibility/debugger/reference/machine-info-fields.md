---
description: Specifica il tipo di informazioni da recuperare per un computer specifico.
title: MACHINE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3361ed090dc724f948d98aa0037949e0c573d56d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057936"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
Specifica il tipo di informazioni da recuperare per un computer specifico.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>Campi
 `MCIF_NAME`\
 Inizializza/usa il `bstrName` campo nella struttura.

 `MCIF_FLAGS`\
 Inizializza/usa il `Flags` campo nella struttura.

 `MIF_ALL`\
 Inizializzare/utilizzare tutti i campi della struttura.

## <a name="remarks"></a>Commenti
 Questi valori vengono passati al metodo [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) per indicare quali membri della struttura [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) devono essere inizializzati.

 Usato anche nel `Fields` membro della `MACHINE_INFO` struttura per indicare quali campi vengono usati e validi.

 Questi flag possono essere combinati con un bit per bit `OR` .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
