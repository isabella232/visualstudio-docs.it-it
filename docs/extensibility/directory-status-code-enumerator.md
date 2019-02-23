---
title: Enumeratore di codice di stato directory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e62685a1a351c9a5773e18a53316106a18af66a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694660"
---
# <a name="directory-status-code-enumerator"></a>Enumeratore di codice di stato directory
Il `SccDirStatus` enumeratore contiene denominati valori costanti che specificano lo stato di una directory nel sistema di controllo di origine. Questa enumerazione viene utilizzata per la [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Questa è stata introdotta nella versione 1.2 dell'API dei plug-in controllo di origine.

## <a name="syntax"></a>Sintassi

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Membri
 Non è stato possibile ottenere lo stato SCC_DIRSTATUS_INVALID; non fare affidamento su di esso.

 SCC_DIRSTATUS_NOTCONTROLLED Directory non è incluso nel controllo del codice sorgente.

 Directory SCC_DIRSTATUS_CONTROLLED è incluso nel controllo sorgente.

 Progetto SCC_DIRSTATUS_EMPTYPROJ corrispondente a questa directory è vuota.

## <a name="see-also"></a>Vedere anche
- [Plug-in controllo codice sorgente](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)