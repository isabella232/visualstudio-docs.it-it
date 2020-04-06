---
title: Attività di debug Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d41f53ab1392ea3c31908faf65a871fa100fbb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738962"
---
# <a name="debug-tasks"></a>Attività di debug
Per eseguire il debug di un programma, è necessario avviarlo e un motore di debug (DE) deve essere collegato ad esso, altrimenti il DE deve essere collegato a un programma avviato in precedenza. Una volta collegato, il DE deve generare determinati eventi di avvio. In risposta, il pacchetto di debug tenta di associare i punti di interruzione impostati nell'IDE. Quando il programma raggiunge un punto di interruzione associato, si arresta e attende l'input dell'utente.

## <a name="in-this-section"></a>Contenuto della sezione
 [Problemi di sicurezza](../../extensibility/debugger/security-issues.md) Vengono illustrati i passaggi di sicurezza necessari per eseguire il debug di un programma.

 [Avviare un programma](../../extensibility/debugger/launching-a-program.md) Fornisce istruzioni dettagliate su come specificare un DE, che chiama il sistema operativo per avviare il programma.

 [Collegare direttamente a un programma](../../extensibility/debugger/attaching-directly-to-a-program.md) Viene descritto il processo utilizzato per eseguire il debug di un programma in un processo già in esecuzione.

 [Inviare eventi di avvio dopo un avvio](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Elenca gli eventi che si svolgono una volta che il DE è collegato al programma, fino a quando il programma è al suo punto di ingresso principale ed è pronto per il debug.

 [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md) Viene illustrato come il DE in genere invia un evento di punto di ingresso, un evento di completamento del carico o un evento di arresto, a seconda delle circostanze.

 [Associare punti di interruzioneBind breakpoints](../../extensibility/debugger/binding-breakpoints.md) Viene descritto come, se l'utente imposta un punto di interruzione, l'IDE formula la richiesta e richiede la sessione di debug per creare il punto di interruzione.

 [Valutare le espressioni](../../extensibility/debugger/evaluating-expressions.md) Viene illustrato come vengono create le espressioni e cosa accade quando viene valutata un'espressione.

 [Visualizzare e visualizzare i dati](../../extensibility/debugger/visualizing-and-viewing-data.md) Viene illustrato come i visualizzatori di tipo e i visualizzatori personalizzati sono supportati dall'analizzatore di espressioni (EE).

## <a name="related-sections"></a>Sezioni correlate
 [Concetti del debuggerDebugger concepts](../../extensibility/debugger/debugger-concepts.md) Vengono descritti i concetti principali relativi all'architettura di debug.

 [Componenti del debugger](../../extensibility/debugger/debugger-components.md) Viene fornita una panoramica dei componenti di debug di Visual Studio, che includono DE, EE e gestore di simboli (SH).

 [Contesti del debuggerDebugger contexts](../../extensibility/debugger/debugger-contexts.md) Viene illustrato il funzionamento simultaneo del DE all'interno di contesti di valutazione del codice, della documentazione e dell'espressione. Descrive, per ognuno dei tre contesti, la posizione, la posizione o la valutazione pertinente.

## <a name="see-also"></a>Vedere anche
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
