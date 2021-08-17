---
title: Novità relative alla progettazione in Visual Studio 2017
description: Informazioni sulle nuove funzionalità per la progettazione del codice, ad esempio la convalida delle dipendenze in tempo reale, disponibili in Visual Studio 2017.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 5fd93098ce569247774b6af5828b7696201b8835
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055276"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novità relative alla progettazione in Visual Studio 2017

## <a name="live-dependency-validation"></a>Convalida delle dipendenze in tempo reale

La rimozione delle dipendenze indesiderate è una parte importante della gestione del debito tecnico. Visual Studio convalida in tempo reale delle dipendenze, incluse informazioni precise sui problemi, ad esempio la posizione in cui si trovano. La convalida delle dipendenze in tempo reale offre tutti i vantaggi delle nuove funzionalità dell'Elenco errori e dell'editor.

![Convalida delle dipendenze in tempo reale in azione](media/dep-validation-whatsnew-01.png)

L'esperienza di creazione è stata modificata per rendere la convalida delle dipendenze più individuabile e più accessibile. La terminologia è cambiata da "Diagramma livello" a "Diagramma dipendenze".

Il menu **Architettura** contiene ora un comando per creare direttamente un diagramma delle dipendenze:

![Voce Dipendenza in tempo reale nel menu Architettura](media/dep-validation-whatsnew-02.png)

I nomi e le descrizioni delle proprietà dei livelli sono stati modificati per renderli più significativi:

![Nomi delle proprietà aggiornate delle dipendenze in tempo reale](media/dep-validation-whatsnew-03.png)

L'impatto delle modifiche nei risultati dell'analisi per il codice corrente nella soluzione viene immediatamente visualizzato ogni volta che si salva il diagramma. Non è necessario attendere il completamento del comando **Convalida dipendenze.**

Per informazioni dettagliate, vedere [questo post di blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Le finestre di progettazione UML sono state rimosse

Le finestre di progettazione UML sono state rimosse Visual Studio.

* I diagrammi UML vengono ora presentati come file XML
* Esplora modelli UML non esiste più
* I riferimenti al progetto di modellazione non vengono più usati per la convalida delle dipendenze
* Il nodo "Riferimenti al livello" Esplora soluzioni non viene più visualizzato
* L'azione di compilazione "Convalida" in un diagramma dipendenze (livello) non viene più usata. L'attività di compilazione è stata rimossa
* La struttura del progetto viene mantenuta per il round trip tra le versioni
* È comunque possibile aprire, creare, modificare e salvare un diagramma delle dipendenze (livello) come XML
* Gli elementi di lavoro TFS collegati a un diagramma di dipendenza (livello) non sono accessibili nell'area di progettazione
* Il back linking da a DSL o a un livello non è più supportato
* L'estendibilità UML in Modeling SDK non è più supportata

Il supporto per la visualizzazione dell'architettura del codice .NET e C++ è disponibile tramite le [mappe codice.](map-dependencies-across-your-solutions.md)

Se si è un utente significativo delle finestre di progettazione UML, è possibile continuare a usare Visual Studio 2015 o versioni precedenti mentre si decide uno strumento alternativo per le proprie esigenze UML.

Per informazioni dettagliate, vedere [questo post di blog](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Supporto dell'edizione per gli strumenti di architettura e modellazione

Visual Studio è disponibile in diverse edizioni. Non tutti questi strumenti offrono supporto per gli strumenti di architettura e modellazione. La tabella seguente illustra la disponibilità di ogni strumento.

|**Funzionalità**|**Enterprise edizione**|**Professional edizione**|**Community edizione**|
|-|-|-|-|
|**Mappe codice**|Sì|Supporta solo la lettura delle mappe codice, il filtraggio delle mappe codice, l'aggiunta di nuovi nodi generici e la creazione di un nuovo Graph diretto da una selezione.|-|
|**Diagrammi delle dipendenze**|Sì|Supporta solo la lettura dei diagrammi delle dipendenze.|Supporta solo la lettura dei diagrammi delle dipendenze.|
|**Grafici diretti** (diagrammi DGML)|Sì|Sì|Sì|
|**Clonazione del codice**|Sì|-|-|
