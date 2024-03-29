---
title: Enumeratore di messaggi | Microsoft Docs
description: I membri di questo enumeratore vengono usati per la funzione TEXTOUTPROC, ovvero una funzione di callback fornita dall'IDE quando chiama SccOpenProject.
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
ms.openlocfilehash: 2ade39f1c90e3201d19975bd671674c8a2d113f0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110241"
---
# <a name="message-enumerator"></a>Enumeratore di messaggi
I flag seguenti vengono usati per la funzione , che è una funzione di callback fornita dall'IDE quando chiama `TEXTOUTPROC` [SccOpenProject](../extensibility/sccopenproject-function.md) (vedere [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) per informazioni dettagliate sulla funzione di callback).

 Se all'IDE viene richiesto di annullare il processo, potrebbe essere visualizzato uno dei messaggi di annullamento. In questo caso, il plug-in del controllo del codice sorgente usa `SCC_MSG_STARTCANCEL` per chiedere all'IDE di visualizzare il **pulsante** Annulla. Successivamente, è possibile inviare qualsiasi set di messaggi normali. Se uno di questi valori restituisce `SCC_MSG_RTN_CANCEL` , il plug-in chiude l'operazione e restituisce . Il plug-in esegue anche il polling `SCC_MSG_DOCANCEL` periodico per determinare se l'utente ha annullato l'operazione. Al termine di tutte le operazioni o se l'utente ha annullato, il plug-in invia `SCC_MSG_STOPCANCEL` . I tipi , SCC_MSG_WARNING e SCC_MSG_ERROR vengono usati per i messaggi visualizzati nell'elenco `SCC_MSG_INFO` di scorrimento dei messaggi. `SCC_MSG_STATUS` è un tipo speciale che indica che il testo deve essere visualizzato in una barra di stato o in un'area di visualizzazione temporanea. Non rimane permanentemente nell'elenco.

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
 SCC_MSG_RTN_CANCEL restituito dal callback per indicare l'annullamento.

 SCC_MSG_RTN_OK restituire dal callback per continuare.

 SCC_MSG_INFO message è informativo.

 SCC_MSG_WARNING Message è un avviso.

 SCC_MSG_ERROR message è un errore.

 SCC_MSG_STATUS messaggio è destinato alla barra di stato.

 SCC_MSG_DOCANCEL nessun testo; IDE restituisce `SCC_MSG_RTN_OK` o `SCC_MSG_RTN_CANCEL` .

 SCC_MSG_STARTCANCEL avvia un ciclo di annullamento.

 SCC_MSG_STOPCANCEL arresta il ciclo di annullamento.

## <a name="see-also"></a>Vedi anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
