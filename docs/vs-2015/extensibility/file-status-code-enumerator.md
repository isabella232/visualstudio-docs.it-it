---
title: Enumeratore del codice di stato file | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1b6e74caa9eedd42e25339d62f5837ccfe82d001
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204370"
---
# <a name="file-status-code-enumerator"></a>Enumeratore di codice di stato file
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 SCC_STATUS_INVALID  
 Non è stato possibile ottenere lo stato; non fare affidamento su di esso.  
  
 SCC_STATUS_NOTCONTROLLED  
 Il file non è sotto il controllo del codice sorgente.  
  
 SCC_STATUS_CONTROLLED  
 Il file è sotto il controllo del codice sorgente.  
  
 SCC_STATUS_CHECKEDOUT  
 Estratto dall'utente corrente nel disco locale.  
  
 SCC_STATUS_OUTOTHER  
 Il file è Estratto da un altro utente.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 Il file è estratto in modo esclusivo.  
  
 SCC_STATUS_OUTMULTIPLE  
 Il file è Estratto da più di un utente.  
  
 SCC_STATUS_OUTOFDATE  
 Il file non è il più recente.  
  
 SCC_STATUS_DELETED  
 Il file è stato eliminato dal progetto.  
  
 SCC_STATUS_LOCKED  
 Il file è bloccato; non sono consentite altre versioni.  
  
 SCC_STATUS_MERGED  
 Il file è stato Unito ma non ancora corretto o verificato.  
  
 SCC_STATUS_SHARED  
 Il file è condiviso tra i progetti.  
  
 SCC_STATUS_PINNED  
 Il file è condiviso con una versione esplicita.  
  
 SCC_STATUS_MODIFIED  
 Il file è stato modificato/violato/violato.  
  
 SCC_STATUS_OUTBYUSER  
 Il file è estratto dall'utente corrente.  
  
 SCC_STATUS_NOMERGE  
 Il file non può mai essere sottoposto a merge con e non deve essere salvato prima di un'GET.  
  
 SCC_STATUS_RESERVED_1  
 Riservato per utilizzo interno.  
  
 SCC_STATUS_RESERVED_2  
 Riservato per utilizzo interno.  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)
