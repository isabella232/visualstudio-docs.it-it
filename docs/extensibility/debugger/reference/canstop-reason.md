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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39a22a0534a464e9899e666550b31ab24503c05d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096525"
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
Specifica l'esecuzione di un'istruzione in una funzione.

## <a name="remarks"></a>Commenti
Passato come argomento al metodo [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) per confermare con la gestione del debug della sessione (SDM) se è opportuno arrestarsi dopo il raggiungimento del punto di ingresso del programma o dopo l'esecuzione di un'istruzione in una funzione o un metodo.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
