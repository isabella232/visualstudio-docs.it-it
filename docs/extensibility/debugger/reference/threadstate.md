---
description: Specifica lo stato del thread.
title: THREADSTATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e4aa5162259cf1937ef24506a32be9d87fb61327
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042738"
---
# <a name="threadstate"></a>THREADSTATE
Specifica lo stato del thread.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
typedef DWORD THREADSTATE;
```

```csharp
public enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
```

## <a name="fields"></a>Campi
 `THREADSTATE_RUNNING`\
 Indica che il thread è in esecuzione.

 `THREADSTATE_STOPPED`\
 Indica che il thread è stato arrestato a causa di un punto di interruzione.

 `THREADSTATE_FRESH`\
 Indica che il thread è stato creato, ma non è ancora in esecuzione codice.

 `THREADSTATE_DEAD`\
 Indica che il thread non è attivo.

 `THREADSTATE_FROZEN`\
 Indica che il thread è bloccato (non è possibile eseguire alcuna esecuzione).

## <a name="remarks"></a>Commenti
 Usato per `dwThreadState` il campo della struttura [THREADPROPERTIES.](../../../extensibility/debugger/reference/threadproperties.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
