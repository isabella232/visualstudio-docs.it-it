---
title: Metodo NotifyDebuggerOfWaitCompletion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28811ba402803d1ddb9a6dd08a18d32db6257386
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889413"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Metodo NotifyDebuggerOfWaitCompletion
Metodo segnaposto usato come destinazione un punto di interruzione dal debugger. Questo metodo non deve essere impostato come inline o ottimizzato.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib. dll*)

## <a name="syntax"></a>Sintassi

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Note
 Tutte le operazioni di join con un'attività devono chiamare questo metodo se i bit di notifica di debugger è impostato.

## <a name="requirements"></a>Requisiti

## <a name="see-also"></a>Vedere anche
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)