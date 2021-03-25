---
title: Metodo NotifyDebuggerOfWaitCompletion | Microsoft Docs
description: Informazioni sul metodo NotifyDebuggerOfWaitCompletion, che è un segnaposto utilizzato come destinazione del punto di interruzione dal debugger.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d58bb7a5e3a3395b534e5679ec303e5d93d5dc85
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054738"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Metodo NotifyDebuggerOfWaitCompletion
Metodo segnaposto utilizzato come destinazione del punto di interruzione dal debugger. Questo metodo non deve essere inline o ottimizzato.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

## <a name="syntax"></a>Sintassi

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Osservazioni
 Tutte le operazioni di join con un'attività devono chiamare questo metodo se è impostato il bit di notifica del debugger.

## <a name="requirements"></a>Requisiti

## <a name="see-also"></a>Vedi anche
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
