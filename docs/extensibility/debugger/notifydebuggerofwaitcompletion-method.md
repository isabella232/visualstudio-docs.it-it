---
title: Metodo NotifyDebuggerOfWaitCompletion | Microsoft Docs
description: Informazioni sul metodo NotifyDebuggerOfWaitCompletion, che è un segnaposto usato come destinazione del punto di interruzione dal debugger.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f4ba75017e277f12c6d3727ddc3d14a7dfd3483a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710332"
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
