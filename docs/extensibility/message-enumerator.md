---
title: Enumeratore message | Microsoft Docs
description: I membri di questo enumeratore vengono usati per la funzione TEXTOUTPROC, una funzione di callback fornita dall'IDE quando chiama SccOpenProject.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4f0bcffa2f0d579d101c2ebcaed92e097c9443c8d4a54c50a6ff7ac798e30258
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414142"
---
# <a name="message-enumerator"></a>Enumeratore di messaggi
I flag seguenti vengono usati per la funzione , che è una funzione di callback fornita dall'IDE quando chiama `TEXTOUTPROC` [SccOpenProject](../extensibility/sccopenproject-function.md) (vedere [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) per informazioni dettagliate sulla funzione di callback).

 Se all'IDE viene richiesto di annullare il processo, potrebbe essere visualizzato uno dei messaggi di annullamento. In questo caso, il plug-in del controllo del codice sorgente usa `SCC_MSG_STARTCANCEL` per chiedere all'IDE di visualizzare il **pulsante** Annulla. Successivamente, è possibile inviare qualsiasi set di messaggi normali. Se uno di questi restituisce `SCC_MSG_RTN_CANCEL` , il plug-in chiude l'operazione e restituisce un risultato. Il plug-in esegue inoltre periodicamente il `SCC_MSG_DOCANCEL` polling per determinare se l'utente ha annullato l'operazione. Al termine di tutte le operazioni o se l'utente ha annullato, il plug-in invia `SCC_MSG_STOPCANCEL` . I tipi , SCC_MSG_WARNING e SCC_MSG_ERROR vengono usati per i messaggi visualizzati `SCC_MSG_INFO` nell'elenco di scorrimento dei messaggi. `SCC_MSG_STATUS` è un tipo speciale che indica che il testo deve essere visualizzato in una barra di stato o in un'area di visualizzazione temporanea. Non rimane permanentemente nell'elenco.

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

## <a name="members"></a>Members
 SCC_MSG_RTN_CANCEL restituire dal callback per indicare l'annullamento.

 SCC_MSG_RTN_OK restituire dal callback per continuare.

 SCC_MSG_INFO messaggio è informativo.

 SCC_MSG_WARNING message è un avviso.

 SCC_MSG_ERROR message è un errore.

 SCC_MSG_STATUS messaggio è destinato alla barra di stato.

 SCC_MSG_DOCANCEL nessun testo; L'IDE `SCC_MSG_RTN_OK` restituisce o `SCC_MSG_RTN_CANCEL` .

 SCC_MSG_STARTCANCEL avvia un ciclo di annullamento.

 SCC_MSG_STOPCANCEL arresta il ciclo di annullamento.

## <a name="see-also"></a>Vedi anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
