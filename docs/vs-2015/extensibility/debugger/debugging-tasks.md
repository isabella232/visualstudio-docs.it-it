---
title: Attività di debug | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4a8a9879bce6d91448bb4f29b842328ab56bb97
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58970167"
---
# <a name="debugging-tasks"></a>Attività di debug
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Per eseguire il debug di un programma, deve essere avviato e un motore di debug (DE) deve essere associato, altrimenti la Germania deve essere collegato a un programma avviato in precedenza. Una volta collegato, la Germania necessario generare alcuni eventi di avvio. In risposta, il pacchetto di debug tenta di associare i punti di interruzione impostati nell'IDE. Quando il programma raggiunge un punto di interruzione associato, il processo si interromperà e attende l'input utente.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Problemi di sicurezza](../../extensibility/debugger/security-issues.md)  
 Vengono illustrati i passaggi di sicurezza necessari per eseguire il debug di un programma.  
  
 [Avvio di un programma](../../extensibility/debugger/launching-a-program.md)  
 Vengono fornite istruzioni dettagliate su come specificare un CRI, che chiama il sistema operativo per avviare il programma.  
  
 [Collegamento diretto a un programma](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Descrive il processo usato per eseguire il debug di un programma in un processo già in esecuzione.  
  
 [Invio degli eventi di avvio dopo un avvio](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Elenca gli eventi che si verificano dopo che la Germania è collegato al programma, fino a quando il programma è in corrispondenza del punto di ingresso principale ed è pronto per il debug.  
  
 [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)  
 Viene illustrato come la Germania invia in genere un evento punto di ingresso, un evento di completamento del carico o un evento di arresto, a seconda delle circostanze.  
  
 [Associazione di punti di interruzione](../../extensibility/debugger/binding-breakpoints.md)  
 Viene descritto come fare, se l'utente imposta un punto di interruzione, l'IDE formula la richiesta e richiede la sessione di debug per creare il punto di interruzione.  
  
 [Valutazione di espressioni](../../extensibility/debugger/evaluating-expressions.md)  
 Viene illustrato come creare espressioni e ciò che accade quando viene valutata un'espressione.  
  
 [Visualizzazione di tipi e dati](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Viene spiegato come visualizzatori di tipi e visualizzatori personalizzati sono supportati dall'analizzatore di espressioni (EE).  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)  
 Descrive i principali concetti dell'architettura di debug.  
  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)  
 Fornisce una panoramica dei componenti di debug Visual Studio, che includono il DE EE e il gestore di simboli (SH).  
  
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)  
 Viene illustrato come la Germania agisce contemporaneamente all'interno di codice, documentazione e contesti di valutazione di espressioni. Viene descritto, per ognuno dei tre contesti, il percorso, posizione o valutazione pertinente a esso.  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
