---
title: Enumeratore di codice di stato di file | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e63311698a21cdb5fed3d0ab5eee799d94ed109
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013847"
---
# <a name="file-status-code-enumerator"></a>Enumeratore di codice di stato file
Il `SccStatus` enumeratore contiene denominati valori costanti che specificano lo stato di un file nel sistema di controllo di origine. Questa enumerazione viene utilizzata per la [SccQueryInfo](../extensibility/sccqueryinfo-function.md) e il `POPLISTFUNC` funzione di callback (vedere [POPLISTFUNC](../extensibility/poplistfunc.md) per informazioni dettagliate).  
  
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
 File non è incluso nel controllo del codice sorgente.  
  
 SCC_STATUS_CONTROLLED  
 File è incluso nel controllo del codice sorgente.  
  
 SCC_STATUS_CHECKEDOUT  
 Estratto dall'utente corrente sul disco locale.  
  
 SCC_STATUS_OUTOTHER  
 File estratto da un altro utente.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 File estratto in modo esclusivo.  
  
 SCC_STATUS_OUTMULTIPLE  
 File estratto da più di un utente.  
  
 SCC_STATUS_OUTOFDATE  
 Il file non è più recente.  
  
 SCC_STATUS_DELETED  
 File è stato eliminato dal progetto.  
  
 SCC_STATUS_LOCKED  
 File è bloccato; non le versioni più consentite.  
  
 SCC_STATUS_MERGED  
 File è stato unito ma non ancora corretto o verificato.  
  
 SCC_STATUS_SHARED  
 File viene condiviso tra i progetti.  
  
 SCC_STATUS_PINNED  
 File viene condiviso da una versione esplicita.  
  
 SCC_STATUS_MODIFIED  
 File è stato modificato, interrotto o violato.  
  
 SCC_STATUS_OUTBYUSER  
 File estratto dall'utente corrente.  
  
 SCC_STATUS_NOMERGE  
 File non può essere unite e non deve essere salvato prima di un'operazione GET.  
  
 SCC_STATUS_RESERVED_1  
 Riservato per uso interno.  
  
 SCC_STATUS_RESERVED_2  
 Riservato per uso interno.  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)