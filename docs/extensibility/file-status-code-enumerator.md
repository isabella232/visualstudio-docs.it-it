---
title: Enumeratore del codice di stato del file | Microsoft Docs
description: L'enumeratore SccStatus contiene valori costanti che specificano lo stato di un file nel sistema di controllo del codice sorgente e viene usato da SccQueryInfo e POPLISTFUNC.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e8036b4a5e8caf026da2e4da9e2347f595eaa12e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122070249"
---
# <a name="file-status-code-enumerator"></a>Enumeratore del codice di stato del file
`SccStatus`L'enumeratore contiene valori costanti denominati che specificano lo stato di un file nel sistema di controllo del codice sorgente. Questa enumerazione viene usata da [SccQueryInfo](../extensibility/sccqueryinfo-function.md) e dalla funzione di callback (per informazioni `POPLISTFUNC` dettagliate, vedere [POPLISTFUNC).](../extensibility/poplistfunc.md)

## <a name="syntax"></a>Sintassi

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>Members
 SCC_STATUS_INVALID stato non è stato ottenuto. non si basano su di esso.

 SCC_STATUS_NOTCONTROLLED file non è in controllo del codice sorgente.

 SCC_STATUS_CONTROLLED file è in controllo del codice sorgente.

 SCC_STATUS_CHECKEDOUT estratto dall'utente corrente sul disco locale.

 SCC_STATUS_OUTOTHER file è estratto da un altro utente.

 SCC_STATUS_OUTEXCLUSIVE file è estratto in modo esclusivo.

 SCC_STATUS_OUTMULTIPLE file è estratto da più di un utente.

 SCC_STATUS_OUTOFDATE il file non è il più recente.

 SCC_STATUS_DELETED file è stato eliminato dal progetto.

 SCC_STATUS_LOCKED il file è bloccato. Non sono consentite altre versioni.

 SCC_STATUS_MERGED il file è stato unito ma non ancora risolto/verificato.

 SCC_STATUS_SHARED file viene condiviso tra progetti.

 SCC_STATUS_PINNED file è condiviso con una versione esplicita.

 SCC_STATUS_MODIFIED file è stato modificato/interrotto/violato.

 SCC_STATUS_OUTBYUSER file estratto dall'utente corrente.

 SCC_STATUS_NOMERGE file non può mai essere unito e non deve essere salvato prima di get.

 SCC_STATUS_RESERVED_1 riservato per uso interno.

 SCC_STATUS_RESERVED_2 riservato per uso interno.

## <a name="see-also"></a>Vedi anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
