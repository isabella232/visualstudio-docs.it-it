---
title: 'Enumeratore del codice di comando : Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15916d26ac0120417205af0bb9117a45ec0397c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739791"
---
# <a name="command-code-enumerator"></a>Enumeratore del codice di comando
Questo enumeratore viene utilizzato nelle opzioni per [il SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList](../extensibility/sccpopulatelist-function.md)per indicare il comando per il quale sono specificate le opzioni.

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

## <a name="members"></a>Membri
SCC_COMMAND_GET corrisponde a [SccGet](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT corrisponde a [SccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN corrisponde al file [SccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT Corrisponde a [SccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD Corrisponde alla proprietà [SccAdd](../extensibility/sccadd-function.md).

SCC_COMMAND_REMOVE Corrisponde a [SccRemove](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF corrisponde al file [SccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY Corrisponde alla proprietà [SccHistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME corrisponde a [SccRename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES corrisponde a [SccProperties](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS corrisponde a [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
