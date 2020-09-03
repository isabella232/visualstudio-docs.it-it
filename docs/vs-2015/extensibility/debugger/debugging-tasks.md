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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200604"
---
# <a name="debugging-tasks"></a>Attività di debug
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Per eseguire il debug di un programma, è necessario avviarlo ed è necessario collegare un motore di debug (DE); in caso contrario, il DE deve essere collegato a un programma avviato in precedenza. Una volta collegato, il DE deve generare determinati eventi di avvio. In risposta, il pacchetto di debug tenta di associare i punti di interruzione impostati nell'IDE. Quando il programma raggiunge un punto di interruzione associato, si interrompe e attende l'input dell'utente.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Problemi di sicurezza](../../extensibility/debugger/security-issues.md)  
 Vengono illustrati i passaggi di sicurezza necessari per eseguire il debug di un programma.  
  
 [Avvio di un programma](../../extensibility/debugger/launching-a-program.md)  
 Vengono fornite istruzioni dettagliate su come specificare un DE, che chiama il sistema operativo per avviare il programma.  
  
 [Collegamento diretto a un programma](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Descrive il processo utilizzato per eseguire il debug di un programma in un processo già in esecuzione.  
  
 [Invio degli eventi di avvio dopo un avvio](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Elenca gli eventi che si verificano quando il DE è collegato al programma, finché il programma non si trova nel punto di ingresso principale ed è pronto per il debug.  
  
 [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)  
 Viene illustrato il modo in cui in genere invia un evento del punto di ingresso, un evento di completamento del caricamento o un evento di arresto, a seconda delle circostanze.  
  
 [Associazione di punti di interruzione](../../extensibility/debugger/binding-breakpoints.md)  
 Viene descritto come, se l'utente imposta un punto di interruzione, l'IDE formula la richiesta e richiede la sessione di debug per creare il punto di interruzione.  
  
 [Valutazione di espressioni](../../extensibility/debugger/evaluating-expressions.md)  
 Illustra il modo in cui vengono create le espressioni e cosa accade quando viene valutata un'espressione.  
  
 [Visualizzazione di tipi e dati](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Viene illustrato come i visualizzatori di tipi e i visualizzatori personalizzati sono supportati dall'analizzatore di espressioni.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)  
 Vengono descritti i principali concetti dell'architettura di debug.  
  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)  
 Viene fornita una panoramica dei componenti di debug di Visual Studio, che includono il gestore DE, EE e Symbol (SH).  
  
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)  
 Spiega in che modo il DE opera simultaneamente nei contesti di codice, documentazione e valutazione delle espressioni. Viene descritto, per ognuno dei tre contesti, la posizione, la posizione o la valutazione pertinente.  
  
## <a name="see-also"></a>Vedere anche  
 [Per iniziare](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
