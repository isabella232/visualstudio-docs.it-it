---
description: Segnala all'interfaccia utente del debugger di Visual Studio di avvisare l'utente che non sono stati individuati i simboli per l'eseguibile avviato.
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7a060436575d51710fcef9c444ac843aa56195d0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058404"
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
