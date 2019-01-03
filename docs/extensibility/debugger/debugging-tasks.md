---
title: Attività di debug | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aa719871e075a5448fa2d351c5bd7950a833601a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900152"
---
# <a name="debug-tasks"></a>Eseguire il debug di attività
Per eseguire il debug di un programma, deve essere avviato e un motore di debug (DE) deve essere associato, altrimenti la Germania deve essere collegato a un programma avviato in precedenza. Una volta collegato, la Germania necessario generare alcuni eventi di avvio. In risposta, il pacchetto di debug tenta di associare i punti di interruzione impostati nell'IDE. Quando il programma raggiunge un punto di interruzione associato, il processo si interromperà e attende l'input utente.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Problemi di sicurezza](../../extensibility/debugger/security-issues.md)  
 Vengono illustrati i passaggi di sicurezza necessari per eseguire il debug di un programma.  
  
 [Avviare un programma](../../extensibility/debugger/launching-a-program.md)  
 Vengono fornite istruzioni dettagliate su come specificare un CRI, che chiama il sistema operativo per avviare il programma.  
  
 [Connettersi direttamente a un programma](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Descrive il processo usato per eseguire il debug di un programma in un processo già in esecuzione.  
  
 [Inviare gli eventi di avvio dopo un avvio](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Elenca gli eventi che si verificano dopo che la Germania è collegato al programma, fino a quando il programma è in corrispondenza del punto di ingresso principale ed è pronto per il debug.  
  
 [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)  
 Viene illustrato come la Germania invia in genere un evento punto di ingresso, un evento di completamento del carico o un evento di arresto, a seconda delle circostanze.  
  
 [Eseguire l'associazione dei punti di interruzione](../../extensibility/debugger/binding-breakpoints.md)  
 Viene descritto come fare, se l'utente imposta un punto di interruzione, l'IDE formula la richiesta e richiede la sessione di debug per creare il punto di interruzione.  
  
 [Valutare le espressioni](../../extensibility/debugger/evaluating-expressions.md)  
 Viene illustrato come creare espressioni e ciò che accade quando viene valutata un'espressione.  
  
 [Visualizzare e visualizzare i dati](../../extensibility/debugger/visualizing-and-viewing-data.md)  
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