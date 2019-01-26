---
title: Enumeratore di messaggio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3fb85f727f4059e76bf5b73c71c0514a4c8cfc24
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54969785"
---
# <a name="message-enumerator"></a>Enumeratore di messaggio
I flag seguenti vengono utilizzati per il `TEXTOUTPROC` funzione, che è una funzione di callback che nell'IDE è disponibile quando si chiama il [SccOpenProject](../extensibility/sccopenproject-function.md) (vedere [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) per informazioni dettagliate su callback funzione).  
  
 Se l'IDE è richiesto per annullare il processo, potrebbe essere visualizzato uno dei messaggi di annullamento. In questo caso, l'origine controllo utilizzi plug-in `SCC_MSG_STARTCANCEL` chiedere l'IDE per visualizzare il **annullare** pulsante. Successivamente, è possibile inviare qualsiasi set di messaggi normali. Se uno qualsiasi di questi restituisce `SCC_MSG_RTN_CANCEL`, quindi il plug-in viene chiusa l'operazione e restituisce. Il plug-in anche esegue il polling `SCC_MSG_DOCANCEL` periodicamente per determinare se l'utente ha annullato l'operazione. Quando tutte le operazioni vengono eseguite o se l'utente ha annullato, il plug-in Invia `SCC_MSG_STOPCANCEL`. Il `SCC_MSG_INFO`, SCC_MSG_WARNING, e i tipi SCC_MSG_ERROR vengono utilizzati per i messaggi visualizzati nell'elenco scorrevole dei messaggi. `SCC_MSG_STATUS` è un tipo speciale che indica che il testo dovrebbe essere inclusa in una barra di stato o l'area di visualizzazione temporaneo. Non resta in modo permanente nell'elenco.  
  
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
 SCC_MSG_RTN_CANCEL  
 Restituito dal callback per indicare l'annullamento.  
  
 SCC_MSG_RTN_OK  
 Restituito dal callback per continuare.  
  
 SCC_MSG_INFO  
 Messaggio è di tipo informativo.  
  
 SCC_MSG_WARNING  
 Messaggio è un avviso.  
  
 SCC_MSG_ERROR  
 Messaggio è un errore.  
  
 SCC_MSG_STATUS  
 Messaggio è destinato a barra di stato.  
  
 SCC_MSG_DOCANCEL  
 Nessun testo; Restituisce IDE `SCC_MSG_RTN_OK` o `SCC_MSG_RTN_CANCEL`.  
  
 SCC_MSG_STARTCANCEL  
 Avvia un ciclo di annullamento.  
  
 SCC_MSG_STOPCANCEL  
 Arresta il ciclo di annullamento.  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)