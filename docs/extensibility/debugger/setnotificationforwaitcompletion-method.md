---
title: Metodo SetNotificationForWaitCompletion | Microsoft Docs
description: Informazioni su come il debugger usa un bit di stato per uscire da un corpo del metodo asincrono per le attività in stile promessa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 88a0140ce27816592a7c43f1304f16638a2935b2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102883"
---
# <a name="setnotificationforwaitcompletion-method"></a>Metodo SetNotificationForWaitCompletion
Imposta o cancella il bit TASK_STATE_WAIT_COMPLETION_NOTIFICATION stato.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

## <a name="syntax"></a>Sintassi

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parametri
 `enabled`

 `true` per impostare il bit; `false` per annullare l'operazione.

## <a name="exceptions"></a>Eccezioni

## <a name="remarks"></a>Osservazioni
 Il debugger imposta questo bit per uscire dal corpo di un metodo asincrono. Se `enabled` è , questo metodo deve essere chiamato solo su `true` un'attività non ancora completata. Quando `enabled` è , questo metodo può essere chiamato sulle attività `false` completate. In entrambi i eventi, deve essere usato solo per le attività in stile promessa.

## <a name="requirements"></a>Requisiti

## <a name="see-also"></a>Vedi anche
- [Classe di attività](../../extensibility/debugger/task-class-internal-members.md)
