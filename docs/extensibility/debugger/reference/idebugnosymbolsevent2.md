---
description: Segnala all'interfaccia Visual Studio del debugger per avvisare l'utente che non è stato possibile trovare i simboli per l'eseguibile avviato.
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
ms.openlocfilehash: 9740f0026977bd865e6493733ca50348e2fb0843b7f3b2fe2ac41e2744dad659
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121277504"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Segnala [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] all'interfaccia utente del debugger di avvisare l'utente che non è stato possibile trovare i simboli per l'eseguibile avviato.

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
