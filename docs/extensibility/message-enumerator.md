---
title: Enumeratore Message | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702513"
---
# <a name="message-enumerator"></a>Enumeratore Message
I flag seguenti vengono usati per la `TEXTOUTPROC` funzione, che è una funzione di callback fornita dall'IDE quando chiama [SccOpenProject](../extensibility/sccopenproject-function.md) (vedere [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) per informazioni dettagliate sulla funzione di callback).

 Se all'IDE viene richiesto di annullare il processo, potrebbe essere presente uno dei messaggi di annullamento. In questo caso, il plug-in del controllo del codice sorgente USA `SCC_MSG_STARTCANCEL` per richiedere all'IDE di visualizzare il pulsante **Annulla** . Successivamente, è possibile inviare qualsiasi set di messaggi normali. Se uno di questi restituisce `SCC_MSG_RTN_CANCEL` , il plug-in chiude l'operazione e restituisce. Il plug-in esegue anche periodicamente il polling `SCC_MSG_DOCANCEL` per determinare se l'utente ha annullato l'operazione. Al termine di tutte le operazioni o se l'utente ha annullato, il plug-in Invia `SCC_MSG_STOPCANCEL` . I `SCC_MSG_INFO` tipi, SCC_MSG_WARNING e SCC_MSG_ERROR vengono utilizzati per i messaggi che vengono visualizzati nell'elenco di scorrimento dei messaggi. `SCC_MSG_STATUS` è un tipo speciale che indica che il testo deve essere visualizzato in una barra di stato o in un'area di visualizzazione temporanea. Non rimane in modo permanente nell'elenco.

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
 SCC_MSG_RTN_CANCEL restituito da callback per indicare l'annullamento.

 SCC_MSG_RTN_OK tornare da callback per continuare.

 SCC_MSG_INFO messaggio è informativo.

 SCC_MSG_WARNING messaggio è un avviso.

 SCC_MSG_ERROR messaggio è un errore.

 SCC_MSG_STATUS messaggio è destinato alla barra di stato.

 Non SCC_MSG_DOCANCEL testo; IDE restituisce `SCC_MSG_RTN_OK` o `SCC_MSG_RTN_CANCEL` .

 SCC_MSG_STARTCANCEL avvia un ciclo di annullamento.

 SCC_MSG_STOPCANCEL interrompe il ciclo di annullamento.

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
