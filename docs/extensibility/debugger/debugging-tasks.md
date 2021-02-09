---
title: Attività di debug | Microsoft Docs
description: Informazioni sulle attività necessarie per eseguire il debug di un programma, ad esempio per collegarlo a un motore di debug, generare eventi di avvio e raggiungere i punti di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f27bc3f261e66791f41034923989b2cd61e09db6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904763"
---
# <a name="debug-tasks"></a>Attività di debug
Per eseguire il debug di un programma, è necessario avviarlo ed è necessario collegare un motore di debug (DE); in caso contrario, il DE deve essere collegato a un programma avviato in precedenza. Una volta collegato, il DE deve generare determinati eventi di avvio. In risposta, il pacchetto di debug tenta di associare i punti di interruzione impostati nell'IDE. Quando il programma raggiunge un punto di interruzione associato, si interrompe e attende l'input dell'utente.

## <a name="in-this-section"></a>Contenuto della sezione
 [Problemi di sicurezza](../../extensibility/debugger/security-issues.md) Vengono illustrati i passaggi di sicurezza necessari per eseguire il debug di un programma.

 [Avviare un programma](../../extensibility/debugger/launching-a-program.md) Vengono fornite istruzioni dettagliate su come specificare un DE, che chiama il sistema operativo per avviare il programma.

 [Connettersi direttamente a un programma](../../extensibility/debugger/attaching-directly-to-a-program.md) Descrive il processo utilizzato per eseguire il debug di un programma in un processo già in esecuzione.

 [Invia eventi di avvio dopo un avvio](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Elenca gli eventi che si verificano quando il DE è collegato al programma, finché il programma non si trova nel punto di ingresso principale ed è pronto per il debug.

 [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md) Viene illustrato il modo in cui in genere invia un evento del punto di ingresso, un evento di completamento del caricamento o un evento di arresto, a seconda delle circostanze.

 [Associa](../../extensibility/debugger/binding-breakpoints.md) punti di interruzione Viene descritto come, se l'utente imposta un punto di interruzione, l'IDE formula la richiesta e richiede la sessione di debug per creare il punto di interruzione.

 [Espressioni di valutazione](../../extensibility/debugger/evaluating-expressions.md) Illustra il modo in cui vengono create le espressioni e cosa accade quando viene valutata un'espressione.

 [Visualizzare e visualizzare i dati](../../extensibility/debugger/visualizing-and-viewing-data.md) Viene illustrato come i visualizzatori di tipi e i visualizzatori personalizzati sono supportati dall'analizzatore di espressioni.

## <a name="related-sections"></a>Sezioni correlate
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md) Vengono descritti i principali concetti dell'architettura di debug.

 [Componenti del debugger](../../extensibility/debugger/debugger-components.md) Viene fornita una panoramica dei componenti di debug di Visual Studio, che includono il gestore DE, EE e Symbol (SH).

 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md) Spiega in che modo il DE opera simultaneamente nei contesti di codice, documentazione e valutazione delle espressioni. Viene descritto, per ognuno dei tre contesti, la posizione, la posizione o la valutazione pertinente.

## <a name="see-also"></a>Vedi anche
 [Operazioni preliminari](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
