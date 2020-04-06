---
title: Enumeratore di messaggi Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e09b72bd228839268cffc228dd0dc503cc82bd9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702513"
---
# <a name="message-enumerator"></a>Enumeratore dei messaggi
I flag seguenti vengono `TEXTOUTPROC` utilizzati per la funzione, ovvero una funzione di callback fornita dall'IDE quando chiama [SccOpenProject](../extensibility/sccopenproject-function.md) (vedere [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) per informazioni dettagliate sulla funzione di callback).

 Se all'IDE viene chiesto di annullare il processo, potrebbe ricevere uno dei messaggi di annullamento. In questo caso, il plug-in controllo del codice sorgente utilizza `SCC_MSG_STARTCANCEL` per chiedere all'IDE di visualizzare il Annulla pulsante. **Cancel** Dopo questo, qualsiasi set di messaggi normali può essere inviato. Se uno di `SCC_MSG_RTN_CANCEL`questi restituisce , il plug-in chiude l'operazione e restituisce . Il plug-in esegue `SCC_MSG_DOCANCEL` inoltre il polling periodico per determinare se l'utente ha annullato l'operazione. Al termine di tutte le operazioni o se l'utente ha annullato, il plug-in invia `SCC_MSG_STOPCANCEL`. I `SCC_MSG_INFO`tipi , SCC_MSG_WARNING e SCC_MSG_ERROR vengono utilizzati per i messaggi visualizzati nell'elenco a scorrimento dei messaggi. `SCC_MSG_STATUS`è un tipo speciale che indica che il testo deve essere visualizzato in una barra di stato o in un'area di visualizzazione temporanea. Non rimane permanentemente nell'elenco.

## <a name="syntax"></a>Sintassi

```
enum { 
   SCC_MSG_RTN_CANCEL = -1, 
   SCC_MSG_RTN_OK = 0, 
   SCC_MSG_INFO = 1 
   SCC_MSG_WARNING, 
   SCC_MSG_ERROR, 
   SCC_MSG_STATUS, 
   SCC_MSG_DOCANCEL, 
   SCC_MSG_STARTCANCEL, 
   SCC_MSG_STOPCANCEL 
};
```

## <a name="members"></a>Membri
 SCC_MSG_RTN_CANCEL Restituisce da callback per indicare cancel.

 SCC_MSG_RTN_OK restituire dal callback per continuare.

 SCC_MSG_INFO Messaggio è informativo.

 messaggio di SCC_MSG_WARNING è un avviso.

 SCC_MSG_ERROR Messaggio è un errore.

 SCC_MSG_STATUS Messaggio è destinato alla barra di stato.

 SCC_MSG_DOCANCEL Nessun testo; L'IDE restituisce `SCC_MSG_RTN_OK` o `SCC_MSG_RTN_CANCEL`.

 SCC_MSG_STARTCANCEL Avvia un ciclo di annullamento.

 SCC_MSG_STOPCANCEL Interrompe il ciclo di annullamento.

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
