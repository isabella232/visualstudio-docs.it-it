---
title: Novità relative alla progettazione in Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 6f81cc32604abe6d90ac0d263574e97df35c63bd
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302952"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novità relative alla progettazione in Visual Studio 2017

## <a name="live-dependency-validation"></a>Convalida delle dipendenze in tempo reale

La rimozione delle dipendenze indesiderate è una parte importante della gestione del debito tecnico. Visual Studio fornisce la convalida in tempo reale delle dipendenze, incluse informazioni precise sui problemi, ad esempio la posizione in cui si trovano. La convalida delle dipendenze in tempo reale sfrutta appieno le nuove funzionalità dell'Elenco errori e dell'editor.

![Convalida delle dipendenze in tempo reale in azione](media/dep-validation-whatsnew-01.png)

L'esperienza di creazione è stata modificata per rendere la convalida delle dipendenze più individuabile e più accessibile. La terminologia è cambiata da "Diagramma livello" a "Diagramma di dipendenza".

Il menu Architettura ora contiene un comando per creare direttamente un diagramma di dipendenza:The **Architecture** menu now contains a command to directly create a Dependency diagram:

![Voce di dipendenza attiva nel menu Architettura](media/dep-validation-whatsnew-02.png)

I nomi e le descrizioni delle proprietà dei layer sono stati modificati per renderli più significativi:

![Nomi delle proprietà aggiornate per la dipendenza in tempo reale](media/dep-validation-whatsnew-03.png)

L'impatto delle modifiche nei risultati dell'analisi per il codice corrente nella soluzione viene visualizzato immediatamente ogni volta che si salva il diagramma. Non è necessario attendere il completamento del comando **Convalida dipendenze.**

Per informazioni dettagliate, vedere [questo post di blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>I progettisti UML sono stati rimossi

Le finestre di progettazione UML sono state rimosse da Visual Studio.

* I diagrammi UML sono ora presentati come file XML
* Esplora modelli UML non esiste più
* I riferimenti al progetto di modellazione non vengono più utilizzati per la convalida delle dipendenzeModeling project references are no longer used for dependency validation
* Il nodo "Riferimenti livello" in Esplora soluzioni non viene più visualizzato
* L'azione di compilazione "Convalida" in un diagramma di dipendenza (livello) non viene più utilizzata - l'attività di compilazione è stata rimossa
* La struttura del progetto viene mantenuta per il round trip tra le versioni
* È comunque possibile aprire, creare, modificare e salvare un diagramma di dipendenza (livello) come XML
* Gli elementi di lavoro TFS collegati a un diagramma di dipendenza (livello) non sono accessibili nell'area di progettazioneTFS work items linked to a Dependency (Layer) diagram are not accessible on the design surface
* Il collegamento a risoni da a DSL o a un layer non è più supportato
* L'estensibilità UML in Modeling SDK non è più supportata

Il supporto per la visualizzazione dell'architettura del codice .NET e di C'è disponibile tramite [le mappe codice.](map-dependencies-across-your-solutions.md)

Se si è un utente significativo delle finestre di progettazione UML, è possibile continuare a utilizzare Visual Studio 2015 o versioni precedenti mentre si decide uno strumento alternativo per le esigenze UML.

Per informazioni dettagliate, vedere [questo post di blog](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Supporto dell'edizione per l'architettura e gli strumenti di modellazione

Visual Studio è disponibile in diverse edizioni. Non tutti forniscono supporto per l'architettura e gli strumenti di modellazione. La tabella seguente illustra la disponibilità di ogni strumento.

|**Funzionalità**|**Edizione Enterprise**|**Edizione professionale**|**Edizione comunitaria**|
|-|-|-|-|
|**Mappe codice**|Sì|Supporta solo la lettura di mappe del codice, il filtraggio delle mappe del codice, l'aggiunta di nuovi nodi generici e la creazione di un nuovo grafico diretto da una selezione.|-|
|**Diagrammi di dipendenza**|Sì|Supporta solo la lettura dei diagrammi di dipendenza.|Supporta solo la lettura dei diagrammi di dipendenza.|
|**Grafici diretti** (diagrammi DGML)|Sì|Sì|Sì|
|**Clone del codice**|Sì|-|-|
