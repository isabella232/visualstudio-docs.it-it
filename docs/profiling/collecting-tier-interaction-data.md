---
title: Raccolta di dati di interazione tra livelli | Microsoft Docs
description: Informazioni su come raccogliere informazioni sulla profilatura dei livelli per le applicazioni multilivello che comunicano con i database ADO.NET servizi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6729052dea38ee39213670d001d3c95de639f7f08cd744d874e502f434073146
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121302150"
---
# <a name="collect-tier-interaction-data"></a>Raccogliere dati di interazione tra livelli

La profilatura delle interazioni tra livelli offre informazioni aggiuntive sui tempi di esecuzione delle funzioni di applicazioni multilivello che comunicano con i database tramite i servizi ADO.NET. I dati vengono raccolti solo per le chiamate di funzione sincrone.

**Versioni di Visual Studio**

I dati di profilatura dell'interazione tra livelli possono essere raccolti usando qualsiasi edizione di Visual Studio, ma possono essere visualizzati solo in Visual Studio Enterprise.

**Windows 8 e Windows Server 2012**

Per raccogliere dati di interazione tra livelli nelle applicazioni desktop di Windows 8 e nelle applicazioni Windows Server 2012, è necessario utilizzare il metodo di strumentazione. Non è possibile raccogliere dati di interazione tra livelli per le app UWP. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). È possibile includere i dati di interazione tra livelli in tutti i metodi di profilatura su un'altra versione di Windows supportata.

**Creazione guidata sessione di prestazioni**

A causa di un bug nella Creazione guidata sessione di prestazioni, è necessario aggiungere l'opzione di raccolta dati di interazione tra livelli ad un'esecuzione di profilatura da Esplora prestazioni. È inoltre necessario aggiungere il progetto, il file eseguibile o il sito Web al nodo di destinazione di Esplora prestazioni.

## <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Per aggiungere dati di interazione tra livelli all'esecuzione della profilatura tramite le pagine delle proprietà della sessione di prestazioni

1. In Esplora prestazioni scegliere **Proprietà** dal menu contestuale.

2. Selezionare la pagina **Interazioni tra livelli** e quindi selezionare la casella di controllo **Abilita profilatura interazione tra livelli**.

3. In Esplora prestazioni selezionare il nodo **Destinazioni** e quindi specificare il progetto, il file eseguibile o il sito Web che si vuole sottoporre a profilatura.

## <a name="see-also"></a>Vedi anche

[Visualizzazione interazioni tra livelli](../profiling/tier-interactions-view.md)
