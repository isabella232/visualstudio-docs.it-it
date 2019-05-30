---
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dadd4547d5b0f691b454a98ba714abea9bf6f058
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323708"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Segnali di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente per avvertire l'utente che non sono stati trovati per l'eseguibile avviato i simboli del debugger.

## <a name="syntax"></a>Sintassi

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementata dai motori di debug e utilizzato dal [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente del debugger.

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll