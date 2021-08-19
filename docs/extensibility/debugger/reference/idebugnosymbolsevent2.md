---
description: Segnala all'interfaccia Visual Studio debugger per avvisare l'utente che non è stato possibile trovare i simboli per l'eseguibile avviato.
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: d3f2eed2c6ea1e50ede7ec539e9ecc80afec2b7b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160212"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Segnala all'interfaccia utente del debugger di avvisare l'utente che non è stato possibile trovare [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] simboli per l'eseguibile avviato.

## <a name="syntax"></a>Sintassi

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementato dai motori di debug e utilizzato dall'interfaccia [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] utente del debugger.

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
