---
title: Arrestare il debug nella finestra di dialogo di avanzamento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af69cd07087da19205ede3bc6576f87bd24279c9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979023"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Terminazione debug in corso (finestra di dialogo)
Questa finestra di dialogo viene visualizzata quando il debugger tenta di interrompere una sessione di debug, ma questa operazione richiede tempo. L'interruzione di una sessione di debug è in genere un'operazione molto veloce e questa finestra di dialogo non viene visualizzata. Talvolta, tuttavia, è necessario più tempo per la disconnessione da tutti i processi in fase di debug. Se l'interruzione della sessione richiede diversi secondi o si verifica un errore di disconnessione, viene visualizzata questa finestra di dialogo. Se ciò avviene di frequente, è possibile che sia presente un problema interno. Può quindi essere opportuno contattare il Servizio Supporto Tecnico Clienti Microsoft.  
  
 È possibile attendere la disconnessione dei processi e la chiusura della finestra di dialogo oppure utilizzare il pulsante **Termina ora** per terminare immediatamente l'operazione.  
  
 **Termina ora**  
 Fare clic su questo pulsante per terminare immediatamente la sessione di debug. Usando **Termina ora** terminerà, anziché disconnessi i processi in corso il debug. Se si esegue il debug di processi di sistema, l'interruzione di tali processi con **Termina ora** può generare effetti imprevisti e indesiderati.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Disconnessione di programmi](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))