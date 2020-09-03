---
title: Enumeratore del codice di stato file | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711446"
---
# <a name="file-status-code-enumerator"></a>Enumeratore del codice di stato file
L' `SccStatus` enumeratore contiene valori costanti denominati che specificano lo stato di un file nel sistema di controllo del codice sorgente. Questa enumerazione viene utilizzata da [SccQueryInfo](../extensibility/sccqueryinfo-function.md) e dalla `POPLISTFUNC` funzione di callback (vedere [POPLISTFUNC](../extensibility/poplistfunc.md) per informazioni dettagliate).

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
 Non è stato possibile ottenere lo stato SCC_STATUS_INVALID; non fare affidamento su di esso.

 Il file di SCC_STATUS_NOTCONTROLLED non è sotto il controllo del codice sorgente.

 Il file di SCC_STATUS_CONTROLLED è sotto il controllo del codice sorgente.

 SCC_STATUS_CHECKEDOUT estratto dall'utente corrente nel disco locale.

 Il file di SCC_STATUS_OUTOTHER viene Estratto da un altro utente.

 Il file di SCC_STATUS_OUTEXCLUSIVE viene estratto in modo esclusivo.

 SCC_STATUS_OUTMULTIPLE file viene Estratto da più di un utente.

 SCC_STATUS_OUTOFDATE il file non è il più recente.

 Il file di SCC_STATUS_DELETED è stato eliminato dal progetto.

 Il file di SCC_STATUS_LOCKED è bloccato. non sono consentite altre versioni.

 Il file di SCC_STATUS_MERGED è stato Unito ma non ancora corretto o verificato.

 SCC_STATUS_SHARED file viene condiviso tra i progetti.

 SCC_STATUS_PINNED file è condiviso con una versione esplicita.

 Il file di SCC_STATUS_MODIFIED è stato modificato/violato/violato.

 Il file di SCC_STATUS_OUTBYUSER è estratto dall'utente corrente.

 Il file di SCC_STATUS_NOMERGE non può mai essere unito con e non deve essere salvato prima di un'GET.

 SCC_STATUS_RESERVED_1 riservata per uso interno.

 SCC_STATUS_RESERVED_2 riservata per uso interno.

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
