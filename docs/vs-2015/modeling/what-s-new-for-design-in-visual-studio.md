---
title: Cosa&#39;s novità per la progettazione
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- what's new [VIsual Studio], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 84b5ed45bfa7117eec4cbaa86ad9ca4533339d62
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001697"
---
# <a name="whats-new-for-design-in-visual-studio-in-visual-studio-2015"></a>Quali sono le novità relative alla progettazione in Visual Studio in Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Questa versione di Visual Studio include i seguenti miglioramenti, utili per comprendere e progettare meglio il codice.

 **Mappe codici e grafici delle dipendenze**

 In Visual Studio Enterprise, per comprendere le dipendenze specifiche nel codice, visualizzarle creando mappe codici. È quindi possibile esplorare queste relazioni tramite la mappa, visualizzata accanto al codice. Le mappe codici consentono di tenere traccia della propria posizione nel codice mentre si usa o si esegue il debug del codice, per cui una parte minore di codice verrà letta mentre si acquisiscono altre informazioni sulla progettazione del codice.

 Nella versione finale (RTM), sono stati creati menu di scelta rapida per gli elementi di codice e collegamenti più facili da usare mediante il raggruppamento di comandi in sezioni relative alla selezione, alla modifica, alla gestione di gruppi e alla modifica del layout del contenuto dei gruppi. Si noti inoltre che i progetti di test vengono visualizzati in uno stile diverso da altri progetti e che le icone per gli elementi nella mappa sono state aggiornate a versioni più appropriate.

 ![Mostra gli elementi selezionati in una nuova mappa codice](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Questi miglioramenti includono:

- **Diagrammi verticali migliorati**. Per soluzioni Visual Studio di medie e grandi dimensioni, è ora possibile usare un menu Architettura semplificato per ottenere mappe codici più utili per la propria soluzione. Gli assembly della soluzione vengono raggruppati in base alle cartelle della soluzione, per cui è possibile visualizzarli nel contesto e sfruttare il lavoro eseguito per strutturare la soluzione. I riferimenti al progetto e all’assembly verranno visualizzati immediatamente, quindi verranno visualizzati i tipi di collegamento. Inoltre, gli assembly esterni alla soluzione vengono raggruppati in un modo più compatto.

- **Ai progetti di test viene applicato uno stile diverso e tali progetti possono essere filtrati**. È ora possibile identificare più facilmente e rapidamente i progetti di test nella mappa perché a tali progetti viene applicato uno stile diverso. I progetti possono essere anche filtrati in modo che sia possibile concentrarsi sul codice dell'applicazione.

- **Collegamenti di dipendenza esterna semplificati**. I collegamenti di dipendenza non rappresentano più l'ereditarietà di System.Object, System.ValueType, System.Enum e System.Delegate che semplifica la visualizzazione delle dipendenze esterne nella mappa codici.

- **L’analisi dei collegamenti di dipendenza tiene in considerazione i filtri**. È possibile ottenere un diagramma utile e chiaro quando il diagramma si espande per comprendere i contributi a un collegamento di dipendenza. Il diagramma è meno pieno di informazioni e tiene in considerazione le opzioni selezionate per il filtro del collegamento.

- **Gli elementi di codice vengono aggiunti a una mappa di codice con il relativo contesto**. Poiché i diagrammi vengono ora visualizzati con il relativo contesto (fino alla cartella della soluzione e dell’assembly che è possibile filtrare se necessario), è possibile ottenere diagrammi più utili quando si trascinano elementi di codice da Esplora soluzioni, Visualizzazione classi, Visualizzatore oggetti o quando si selezionano elementi in Esplora soluzioni e si sceglie Mostra in mappa codici.

- **Ottenere mappe di codici reattive più rapidamente**. Le operazioni di trascinamento della selezione producono un risultato immediato e i collegamenti tra i nodi vengono creati molto più rapidamente, senza influire sulle operazioni successive avviate dall'utente, ad esempio l’espansione di un nodo o la richiesta di altri nodi. Quando si creano mappe di codice senza compilare la soluzione, tutti i casi estremi, ad esempio quando gli assembly non vengono compilati, vengono ora elaborati.

- **Ignorare la ricompilazione della soluzione.** Offre prestazioni migliori durante la creazione e la modifica di diagrammi.

- **Filtrare nodi e gruppi di elementi di codice**. È possibile ordinare rapidamente le mappe visualizzando o nascondendo gli elementi di codice in base alla categoria e raggruppando gli elementi di codice per cartelle di soluzioni, assembly, spazi dei nomi, cartelle di progetti e tipi.

- **Filtrare le relazioni in modo da agevolare la lettura dei diagrammi**. Il filtro dei collegamenti si applica ora anche ai collegamenti tra gruppi, che rende l’uso della finestra dei filtri meno invasivo rispetto alle versioni precedenti.

- **Creare diagrammi da Visualizzazione classi e Visualizzatore oggetti**. Trascinare la selezione di file e assembly in una mappa nuova o esistente dalle finestre Visualizzazione classi e Visualizzatore oggetti.

  Vedere [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

  **Altre modifiche di progettazione e modellazione in questa versione:**

- **Diagrammi livello**. Aggiornare questi diagrammi con Visualizzazione classi e Visualizzatore oggetti. Per soddisfare i requisiti di progettazione software, usare i diagrammi livello per descrivere le dipendenze desiderate per il software. Mantenere il codice coerente con la progettazione individuando il codice che non soddisfa questi vincoli e convalidando il codice futuro con questa linea di base.

- **Diagrammi UML**. Per creare diagrammi classi e diagrammi sequenze UML, non è più possibile usare codice, ma si possono usare i nuovi elementi UML.

- **Esplora architettura** Per creare diagrammi, non è più possibile usare Esplora architettura, ma si può usare Esplora soluzioni.

##  <a name="VersionSupport"></a> Supporto di edizione per un'architettura e strumenti di modellazione

Visual Studio 2015 è disponibile in diverse edizioni. Non tutte le forniscono il supporto per l'architettura e strumenti di modellazione. La tabella seguente illustra la disponibilità di ogni strumento.

|**Funzionalità**|**Enterprise**|**Professional**|**Community**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Mappe codice**|Yes|Supporta solo la lettura e il filtraggio di mappe codice, aggiunta di nuovi nodi generici e la creazione di un grafico diretto da una selezione.|-|-|
|**Diagrammi classi UML**|Yes|-|-|-|
|**Diagrammi di sequenza UML**|Yes|-|-|-|
|**Diagrammi caso d'uso UML**|Yes|-|-|-|
|**Diagrammi attività UML**|Yes|-|-|-|
|**Diagrammi dei componenti UML**|Yes|-|-|-|
|**Diagrammi livello**|Yes|-|-|-|
|**Grafici diretti** (diagrammi DGML)|Yes|Yes|-|-|
|**Clone di codice**|Yes|-|-|-|