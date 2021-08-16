---
description: Utilizzato per determinare se un programma può arrestare l'esecuzione dopo aver raggiunto un punto specifico dell'esecuzione.
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 995b197cd74612f324344c8fe9b74f9f96fc89449abfd83ba656f4102c9b52cf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378068"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
Utilizzato per determinare se un programma può arrestare l'esecuzione dopo aver raggiunto un punto specifico dell'esecuzione.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="fields"></a>Campi
`CANSTOP_ENTRYPOINT`\
Specifica il punto di ingresso del programma specificato.

`CANSTOP_STEPIN`\
Specifica l'esecuzione di istruzioni in una funzione.

## <a name="remarks"></a>Commenti
Passato come argomento al metodo [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) per confermare con Gestione debug sessione (SDM) se è possibile arrestarsi dopo aver raggiunto il punto di ingresso del programma o dopo l'esecuzione di istruzioni in una funzione o in un metodo.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
