---
title: Metodo NotifyDebuggerOfWaitCompletion | Microsoft Docs
description: Informazioni sul metodo NotifyDebuggerOfWaitCompletion, un segnaposto usato come destinazione del punto di interruzione dal debugger.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160374"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Metodo NotifyDebuggerOfWaitCompletion
Metodo segnaposto usato come destinazione del punto di interruzione dal debugger. Questo metodo non deve essere inline o ottimizzato.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

## <a name="syntax"></a>Sintassi

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Osservazioni
 Tutte le operazioni di join con un'attività devono chiamare questo metodo se il bit di notifica del debugger è impostato.

## <a name="requirements"></a>Requisiti

## <a name="see-also"></a>Vedi anche
- [Classe di attività](../../extensibility/debugger/task-class-internal-members.md)
