---
title: Arrestare il debug nella finestra di dialogo di avanzamento | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.stopnow
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dba046c57e7b3990b3bf31994da699bed1e6442
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792281"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Terminazione debug in corso (finestra di dialogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa finestra di dialogo viene visualizzata quando il debugger tenta di interrompere una sessione di debug, ma questa operazione richiede tempo. L'interruzione di una sessione di debug è in genere un'operazione molto veloce e questa finestra di dialogo non viene visualizzata. Talvolta, tuttavia, è necessario più tempo per la disconnessione da tutti i processi in fase di debug. Se l'interruzione della sessione richiede diversi secondi o si verifica un errore di disconnessione, viene visualizzata questa finestra di dialogo. Se ciò avviene di frequente, è possibile che sia presente un problema interno. Può quindi essere opportuno contattare il Servizio Supporto Tecnico Clienti Microsoft.  
  
 È possibile attendere il disconnessione dei processi e questa finestra di dialogo, o usare il **Termina ora** pulsante per forzare la terminazione immediata.  
  
 **Interrompere ora**  
 Fare clic su questo pulsante per terminare immediatamente la sessione di debug. Usando **Termina ora**terminerà, anziché disconnessi i processi in corso il debug. Se si esegue il debug di processi di sistema, terminazione tali processi con **Termina ora** può avere effetti imprevisti e indesiderati.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Disconnessione di programmi](http://msdn.microsoft.com/en-us/f2c756c2-8079-474b-94c2-01c19a141a01)



