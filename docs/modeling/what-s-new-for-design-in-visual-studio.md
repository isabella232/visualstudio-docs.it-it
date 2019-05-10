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
ms.openlocfilehash: dc75c7414e0fff18f76d14f8f9a4e0779a9e7a2b
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476542"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novità relative alla progettazione in Visual Studio 2017

## <a name="live-dependency-validation"></a>Convalida delle dipendenze in tempo reale

Rimozione delle dipendenze indesiderate è una parte importante della gestione del debito tecnico. Visual Studio fornisce la convalida live delle dipendenze, incluse informazioni dettagliate sui problemi, ad esempio in cui si trovano. Dipendenze in tempo reale convalida accetta completa i vantaggi delle nuove funzionalità nell'elenco degli errori e nell'editor.

![Convalida delle dipendenze in tempo reale in azione](media/dep-validation-whatsnew-01.png)

Esperienza di creazione è stata modificata per semplificare la convalida delle dipendenze più accessibili e individuabili. La terminologia è cambiato da "Diagramma livello" a "Diagramma di dipendenze".

Il **architettura** menu contiene ora un comando per creare direttamente un diagramma delle dipendenze:

![Elemento di dipendenza in tempo reale del menu architettura](media/dep-validation-whatsnew-02.png)

I nomi delle proprietà di livello e le descrizioni sono state modificate in modo da renderli più significativi:

![Nomi delle proprietà di dipendenza in tempo reale aggiornato](media/dep-validation-whatsnew-03.png)

Noterete immediatamente l'impatto delle modifiche nei risultati di analisi per il codice nella soluzione corrente ogni volta che si salva il diagramma. Non è necessario attendere il completamento dei **convalidare le dipendenze** comando.

Per altre informazioni, vedere [questo post di blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Sono state rimosse le finestre di progettazione UML

Le finestre di progettazione UML sono state rimosse da Visual Studio.

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

Supporto per visualizzare l'architettura di .NET e C++ codice è disponibile attraverso [mappe codici](map-dependencies-across-your-solutions.md).

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