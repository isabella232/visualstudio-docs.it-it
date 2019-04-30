---
title: Novità relative alla progettazione in Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: fb7ef710d117318d475e32f19b5ca2511b94f8bc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386930"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novità relative alla progettazione in Visual Studio 2017

## <a name="live-dependency-validation"></a>Convalida delle dipendenze in tempo reale

Rimozione delle dipendenze indesiderate è una parte importante della gestione del debito tecnico. La convalida Live delle dipendenze è ora incluso, fornendo informazioni precise sui problemi e beneficiare completamente le nuove funzionalità nell'elenco degli errori e nell'editor.

![Convalida delle dipendenze in tempo reale in azione](media/dep-validation-whatsnew-01.png)

Esperienza di creazione è stata modificata per semplificare la convalida delle dipendenze e più accessibili, individuabili modificando la terminologia da "Diagramma livello" a "Diagramma delle dipendenze".

Il **architettura** menu contiene ora un comando per creare direttamente un diagramma delle dipendenze:

![Elemento di dipendenza in tempo reale del menu architettura](media/dep-validation-whatsnew-02.png)

... e i nomi delle proprietà di un livello in un diagramma delle dipendenze e le relative descrizioni, sono stati modificati per renderli più significativi:

![Nomi delle proprietà di dipendenza in tempo reale aggiornato](media/dep-validation-whatsnew-03.png)

Noterete ora che l'impatto delle modifiche immediatamente nei risultati di analisi per il codice nella soluzione corrente ogni volta che si salva il diagramma. Non devi attendere più il completamento del comando "Convalida delle dipendenze".

Per altre informazioni, vedere [questo post di blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Sono state rimosse le finestre di progettazione UML

Le finestre di progettazione UML sono state rimosse da questa versione di Visual Studio Enterprise.

* Diagrammi UML sono ora presentati come file XML
* Esplora modelli UML non esiste più
* I riferimenti non vengono più utilizzati per la convalida delle dipendenze di progetto di modellazione
* Il nodo "Riferimenti livello" in Esplora soluzioni non viene più visualizzato
* L'azione di compilazione "Convalida" in un diagramma delle dipendenze (Layer) non viene più usato, l'attività di compilazione è stato rimosso
* La struttura del progetto è stata mantenuta per sequenze di andata e ritorno tra versioni
* Si può comunque aprire, creare, modificare e salvare un diagramma delle dipendenze (Layer) come XML
* Elementi di lavoro TFS collegati a un diagramma delle dipendenze (Layer) non sono accessibili nell'area di progettazione
* Il collegamento back-dal linguaggio specifico di dominio o un livello non è più supportato
* Estendibilità UML nel SDK di modellazione non è più supportato

Tuttavia, il supporto per l'architettura di codice .NET e C++ la visualizzazione è disponibile tramite [mappe codici](map-dependencies-across-your-solutions.md)e i miglioramenti significativi alla convalida delle dipendenze descritto in precedenza.

Se sei un utente significative delle finestre di progettazione UML, è possibile continuare a usare Visual Studio 2015 o versioni precedenti, anche se si decide in uno strumento alternativo per le esigenze di UML.

Per altre informazioni, vedere [questo post di blog](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Supporto di edizione per un'architettura e strumenti di modellazione

Visual Studio è disponibile in diverse edizioni. Non tutte le forniscono il supporto per l'architettura e strumenti di modellazione. La tabella seguente illustra la disponibilità di ogni strumento.

|**Funzionalità**|**Edizione Enterprise**|**Professional edition**|**Edizione community**|
|-|-|-|-|
|**Mappe codice**|Yes|Solo supporta la lettura di mappe codice, il filtro di codice viene eseguito il mapping, aggiunta di nuovi nodi generici e la creazione di un grafico diretto da una selezione.|-|
|**Diagrammi delle dipendenze**|Yes|Supporta solo la lettura di diagrammi delle dipendenze.|Supporta solo la lettura di diagrammi delle dipendenze.|
|**Grafici diretti** (diagrammi DGML)|Yes|Yes|Yes|
|**Clone di codice**|Yes|-|-|