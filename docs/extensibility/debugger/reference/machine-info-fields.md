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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 448edb134ba6065c85ee1547c73f45f9df769563
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122103143"
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
 Inizializzare/usare `bstrName` il campo nella struttura .

 `MCIF_FLAGS`\
 Inizializzare/usare `Flags` il campo nella struttura .

 `MIF_ALL`\
 Inizializzare/usare tutti i campi nella struttura .

## <a name="remarks"></a>Commenti
 Questi valori vengono passati al [metodo GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) [](../../../extensibility/debugger/reference/machine-info.md) per indicare quali membri della struttura MACHINE_INFO devono essere inizializzati.

 Usato anche nel `Fields` membro della struttura per indicare quali campi vengono usati e `MACHINE_INFO` validi.

 Questi flag possono essere combinati con un oggetto bit per `OR` bit.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
