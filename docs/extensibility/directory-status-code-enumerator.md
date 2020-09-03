---
title: Enumeratore del codice di stato della directory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b5ebf61f2baa6e4277e27cd3c4d18a51e64f835
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712149"
---
# <a name="directory-status-code-enumerator"></a>Enumeratore del codice di stato della directory
L' `SccDirStatus` enumeratore contiene valori costanti denominati che specificano lo stato di una directory nel sistema di controllo del codice sorgente. Questa enumerazione viene utilizzata da [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Questa operazione è stata introdotta nella versione 1,2 dell'API del plug-in del controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Members
 Non è stato possibile ottenere lo stato SCC_DIRSTATUS_INVALID; non fare affidamento su di esso.

 SCC_DIRSTATUS_NOTCONTROLLED directory non è sotto il controllo del codice sorgente.

 SCC_DIRSTATUS_CONTROLLED directory è sotto il controllo del codice sorgente.

 SCC_DIRSTATUS_EMPTYPROJ progetto corrispondente a questa directory è vuoto.

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
