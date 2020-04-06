---
title: Enumeratore del codice di stato del file - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 184c8686ea184aea2cbd0a64873718cbe72f7615
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711446"
---
# <a name="file-status-code-enumerator"></a>Enumeratore codice di stato del file
L'enumeratore `SccStatus` contiene valori costanti denominati che specificano lo stato di un file nel sistema di controllo del codice sorgente. Questa enumerazione viene utilizzata da [SccQueryInfo](../extensibility/sccqueryinfo-function.md) e dalla `POPLISTFUNC` funzione di callback (vedere [POPLISTFUNC](../extensibility/poplistfunc.md) per i dettagli).

## <a name="syntax"></a>Sintassi

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>Membri
 SCC_STATUS_INVALID Impossibile ottenere lo Status; non fare affidamento su di esso.

 SCC_STATUS_NOTCONTROLLED File non è nel controllo del codice sorgente.

 SCC_STATUS_CONTROLLED File è nel controllo del codice sorgente.

 SCC_STATUS_CHECKEDOUT Estratto dall'utente corrente sul disco locale.

 SCC_STATUS_OUTOTHER file è estratto da un altro utente.

 SCC_STATUS_OUTEXCLUSIVE file viene estratto esclusivamente.

 SCC_STATUS_OUTMULTIPLE file è estratto da più utenti.

 SCC_STATUS_OUTOFDATE Il file non è il più recente.

 SCC_STATUS_DELETED file è stato eliminato dal progetto.

 SCC_STATUS_LOCKED Il file è bloccato; non sono più ammesse versioni.

 SCC_STATUS_MERGED file è stato unito ma non ancora fisso/verificato.

 SCC_STATUS_SHARED file viene condiviso tra i progetti.

 SCC_STATUS_PINNED File viene condiviso con una versione esplicita.

 SCC_STATUS_MODIFIED file è stato modificato/interrotto/violato.

 SCC_STATUS_OUTBYUSER file è estratto dall'utente corrente.

 SCC_STATUS_NOMERGE File non può mai essere unito e non deve essere salvato prima di un GET.

 SCC_STATUS_RESERVED_1 Riservato per uso interno.

 SCC_STATUS_RESERVED_2 Riservato per uso interno.

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
