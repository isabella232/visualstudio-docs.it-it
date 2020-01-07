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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593499"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novità relative alla progettazione in Visual Studio 2017

## <a name="live-dependency-validation"></a>Convalida delle dipendenze in tempo reale

Rimozione delle dipendenze indesiderate è una parte importante della gestione del debito tecnico. Visual Studio fornisce la convalida in tempo reale delle dipendenze, incluse informazioni precise sui problemi, ad esempio la posizione in cui si trovano. La convalida delle dipendenze in tempo reale sfrutta tutti i vantaggi delle nuove funzionalità del Elenco errori e dell'editor.

![Convalida delle dipendenze in tempo reale in azione](media/dep-validation-whatsnew-01.png)

L'esperienza di creazione è cambiata per rendere la convalida delle dipendenze più individuabile e più accessibile. La terminologia è cambiata da "diagramma livello" a "diagramma delle dipendenze".

Il **architettura** menu contiene ora un comando per creare direttamente un diagramma delle dipendenze:

![Elemento di dipendenza in tempo reale del menu architettura](media/dep-validation-whatsnew-02.png)

I nomi e le descrizioni delle proprietà del livello sono stati modificati per renderli più significativi:

![Nomi delle proprietà di dipendenza in tempo reale aggiornato](media/dep-validation-whatsnew-03.png)

Si noterà immediatamente l'effetto delle modifiche nei risultati dell'analisi per il codice corrente della soluzione ogni volta che si salva il diagramma. Non è necessario attendere il completamento del comando **convalida dipendenze** .

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

Il supporto per la visualizzazione dell'architettura di .NET C++ e del codice è disponibile tramite le [mappe codici](map-dependencies-across-your-solutions.md).

Se sei un utente significative delle finestre di progettazione UML, è possibile continuare a usare Visual Studio 2015 o versioni precedenti, anche se si decide in uno strumento alternativo per le esigenze di UML.

Per altre informazioni, vedere [questo post di blog](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Supporto di edizione per un'architettura e strumenti di modellazione

Visual Studio è disponibile in diverse edizioni. Non tutte le forniscono il supporto per l'architettura e strumenti di modellazione. La tabella seguente illustra la disponibilità di ogni strumento.

|**Funzionalità**|**Edizione Enterprise**|**Professional edition**|**Edizione community**|
|-|-|-|-|
|**Mappe codice**|Sì|Solo supporta la lettura di mappe codice, il filtro di codice viene eseguito il mapping, aggiunta di nuovi nodi generici e la creazione di un grafico diretto da una selezione.|-|
|**Diagrammi delle dipendenze**|Sì|Supporta solo la lettura di diagrammi delle dipendenze.|Supporta solo la lettura di diagrammi delle dipendenze.|
|**Grafici diretti** (diagrammi DGML)|Sì|Sì|Sì|
|**Clone di codice**|Sì|-|-|
