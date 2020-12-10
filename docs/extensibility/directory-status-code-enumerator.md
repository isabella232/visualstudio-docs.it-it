---
title: Enumeratore del codice di stato della directory | Microsoft Docs
description: L'enumeratore SccDirStatus contiene valori costanti denominati che specificano lo stato di una directory nel sistema di controllo del codice sorgente e viene usato da SccDirQueryInfo.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: af72b9e14695cb954084abebc3a3c336c90af73d
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996123"
---
# <a name="directory-status-code-enumerator"></a>Enumeratore del codice di stato della directory
L' `SccDirStatus` enumeratore contiene valori costanti denominati che specificano lo stato di una directory nel sistema di controllo del codice sorgente. Questa enumerazione viene utilizzata da [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Questa operazione è stata introdotta nella versione 1,2 dell'API del plug-in del controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
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
