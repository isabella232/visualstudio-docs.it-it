---
title: Finestra di dialogo Interrompi debug in corso | Microsoft Docs
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
ms.openlocfilehash: 3beefe16f8883eb64d7d0a2641cabf9eb1f702fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72729662"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Terminazione debug in corso (finestra di dialogo)
Questa finestra di dialogo viene visualizzata quando il debugger tenta di interrompere una sessione di debug, ma questa operazione richiede tempo. L'interruzione di una sessione di debug è in genere un'operazione molto veloce e questa finestra di dialogo non viene visualizzata. Talvolta, tuttavia, è necessario più tempo per la disconnessione da tutti i processi in fase di debug. Se l'interruzione della sessione richiede diversi secondi o si verifica un errore di disconnessione, viene visualizzata questa finestra di dialogo. Se ciò avviene di frequente, è possibile che sia presente un problema interno. Può quindi essere opportuno contattare il Servizio Supporto Tecnico Clienti Microsoft.

 È possibile attendere la disconnessione dei processi e la chiusura della finestra di dialogo oppure utilizzare il pulsante **Termina ora** per terminare immediatamente l'operazione.

 **Interrompi ora** Fare clic su questo pulsante per terminare immediatamente la sessione di debug. L'utilizzo di **Stop Now** verrà terminato anziché scollegare i processi di cui è in corso il debug. Se si esegue il debug di processi di sistema, l'interruzione di tali processi con **Termina ora** può generare effetti imprevisti e indesiderati.

## <a name="see-also"></a>Vedere anche
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Scollegamento di programmi](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))