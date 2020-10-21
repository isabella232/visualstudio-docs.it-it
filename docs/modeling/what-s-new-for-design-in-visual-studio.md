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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "92299519"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novità relative alla progettazione in Visual Studio 2017

## <a name="live-dependency-validation"></a>Convalida delle dipendenze in tempo reale

La rimozione di dipendenze indesiderate è una parte importante della gestione del debito tecnico. Visual Studio fornisce la convalida in tempo reale delle dipendenze, incluse informazioni precise sui problemi, ad esempio la posizione in cui si trovano. La convalida delle dipendenze in tempo reale sfrutta tutti i vantaggi delle nuove funzionalità del Elenco errori e dell'editor.

![Convalida delle dipendenze attive in azione](media/dep-validation-whatsnew-01.png)

L'esperienza di creazione è cambiata per rendere la convalida delle dipendenze più individuabile e più accessibile. La terminologia è cambiata da "diagramma livello" a "diagramma delle dipendenze".

Il menu **architettura** contiene ora un comando per creare direttamente un diagramma delle dipendenze:

![Elemento dipendenza in tempo reale nel menu architettura](media/dep-validation-whatsnew-02.png)

I nomi e le descrizioni delle proprietà del livello sono stati modificati per renderli più significativi:

![Nomi di proprietà aggiornati sulle dipendenze attive](media/dep-validation-whatsnew-03.png)

Si noterà immediatamente l'effetto delle modifiche nei risultati dell'analisi per il codice corrente della soluzione ogni volta che si salva il diagramma. Non è necessario attendere il completamento del comando **convalida dipendenze** .

Per informazioni dettagliate, vedere [questo post di blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Le finestre di progettazione UML sono state rimosse

Le finestre di progettazione UML sono state rimosse da Visual Studio.

* I diagrammi UML sono ora presentati come file XML
* Esplora modelli UML non esiste più
* I riferimenti al progetto di modello non vengono più utilizzati per la convalida delle dipendenze
* Il nodo "riferimenti a livello" in Esplora soluzioni non è più visualizzato
* L'azione di compilazione "convalida" in un diagramma di dipendenza (livello) non è più utilizzata. l'attività di compilazione è stata rimossa
* La struttura del progetto viene mantenuta per le sequenze di andata e ritorno tra le versioni
* È comunque possibile aprire, creare, modificare e salvare un diagramma di dipendenza (livello) come XML
* Gli elementi di lavoro TFS collegati a un diagramma di dipendenza (livello) non sono accessibili nell'area di progettazione
* Il collegamento di nuovo da a DSL o a un livello non è più supportato
* L'estendibilità UML nell'SDK di modellazione non è più supportata

Il supporto per la visualizzazione dell'architettura del codice .NET e C++ è disponibile tramite le [mappe codice](map-dependencies-across-your-solutions.md).

Se si è un utente significativo delle finestre di progettazione UML, è possibile continuare a usare Visual Studio 2015 o versioni precedenti, mentre si decide di usare uno strumento alternativo per le proprie esigenze UML.

Per informazioni dettagliate, vedere [questo post di blog](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Supporto dell'edizione per gli strumenti di architettura e modellazione

Visual Studio è disponibile in diverse edizioni. Non tutti forniscono supporto per gli strumenti di architettura e modellazione. La tabella seguente illustra la disponibilità di ogni strumento.

|**Funzionalità**|**Enterprise Edition**|**Edizione Professional**|**Edizione community**|
|-|-|-|-|
|**Mappe codice**|Sì|Supporta solo la lettura delle mappe codice, l'applicazione di filtri alle mappe del codice, l'aggiunta di nuovi nodi generici e la creazione di un nuovo grafico diretto da una selezione.|-|
|**Diagrammi delle dipendenze**|Sì|Supporta solo la lettura di diagrammi di dipendenza.|Supporta solo la lettura di diagrammi di dipendenza.|
|**Grafici diretti** (diagrammi DGML)|Sì|Sì|Sì|
|**Clone del codice**|Sì|-|-|
