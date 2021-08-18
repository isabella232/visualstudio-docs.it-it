---
title: Enumeratore command code | Microsoft Docs
description: L'enumeratore del codice di comando viene usato nelle opzioni per SccGetCommandOptions e SccPopulateListto per indicare il comando per cui sono specificate le opzioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 37c692cc7f2dcfa1f978b5448b84e255178a6cf390bb50a1a2918a6981a07543
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434802"
---
# <a name="command-code-enumerator"></a>Enumeratore del codice di comando
Questo enumeratore viene usato nelle opzioni per [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList](../extensibility/sccpopulatelist-function.md)per indicare il comando per cui sono specificate le opzioni.

## <a name="syntax"></a>Sintassi

```
enum SCCCOMMAND {
   SCC_COMMAND_GET,
   SCC_COMMAND_CHECKOUT,
   SCC_COMMAND_CHECKIN,
   SCC_COMMAND_UNCHECKOUT,
   SCC_COMMAND_ADD,
   SCC_COMMAND_REMOVE,
   SCC_COMMAND_DIFF,
   SCC_COMMAND_HISTORY,
   SCC_COMMAND_RENAME,
   SCC_COMMAND_PROPERTIES,
   SCC_COMMAND_OPTIONS
};
```

## <a name="members"></a>Members
SCC_COMMAND_GET corrisponde a [SccGet](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT corrisponde a [SccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN corrisponde a [SccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT corrisponde a [SccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD corrisponde a [SccAdd.](../extensibility/sccadd-function.md)

SCC_COMMAND_REMOVE corrisponde a [SccRemove](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF corrisponde a [SccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY corrisponde a [SccHistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME corrisponde a [SccRename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES corrisponde a [SccProperties](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS corrisponde a [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Vedi anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
