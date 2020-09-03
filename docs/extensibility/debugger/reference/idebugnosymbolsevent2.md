---
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9483c5a434ddfddb3f877111deabea9be6520b05
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726718"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Segnala all' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaccia utente del debugger di avvisare l'utente che non sono stati individuati i simboli per l'eseguibile avviato.

## <a name="syntax"></a>Sintassi

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementato dai motori di debug e utilizzato dall' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaccia utente del debugger.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
