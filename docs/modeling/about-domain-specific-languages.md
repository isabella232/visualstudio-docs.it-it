---
title: Informazioni sui linguaggi specifici del dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: bef799b564c4d7bc7eada541bf0c88067403738e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940816"
---
# <a name="about-domain-specific-languages"></a>Informazioni sui linguaggi specifici del dominio

A differenza di un linguaggio generico come c# o UML, un linguaggio specifico di dominio (DSL) è progettato per esprimere le istruzioni in una particolare area problematica o dominio.

DSL Well-Known includere espressioni regolari e SQL. Ogni linguaggio specifico di dominio è preferibile rispetto a un linguaggio generico per descrivere le operazioni su stringhe di testo o un database, ma molto peggiori per descrivere le idee che esulano dall'ambito di un proprio. Singoli settori hanno anche le proprie soluzioni DSL. Ad esempio, nel settore delle telecomunicazioni, chiamare descrizione lingue vengono ampiamente utilizzate per specificare la sequenza degli stati in una chiamata telefonica e in modalità wireless nel settore di viaggio standard che DSL viene usato per descrivere ogni nuova prenotazione dei voli.

L'azienda e il progetto utilizza inoltre set speciale di concetti che può essere descritta con un linguaggio DSL. Ad esempio, è possibile definire un linguaggio DSL di una di queste applicazioni:

-   Piano di percorsi di navigazione in un sito Web.

-   Collegare i diagrammi dei componenti elettronici.

-   Reti di nastri trasportatori e attrezzature per un aeroporto di gestione dei bagagli.

Quando si progetta un linguaggio DSL, si definisce una *della classe di dominio* per ognuno dei concetti importanti nel dominio, ad esempio una pagina web, lamp o aeroporto banco. Si definiscono *relazioni di dominio* come collegamento ipertestuale, trasmissione o un nastro trasportatore per collegare i concetti.

Gli utenti del linguaggio DSL creare *modelli.* I modelli sono *istanze* del linguaggio DSL. Ad esempio, descrivono un particolare sito Web o il collegamento di un determinato dispositivo o il sistema in un determinato aeroporto di gestione dei bagagli.

Gli utenti possono visualizzare un modello come un diagramma o un modulo di Windows. I modelli possono essere visualizzati anche come XML, ovvero come vengono archiviati. Quando si definisce un linguaggio DSL, si definiscono come le istanze di ogni classe di dominio e le relazioni vengono visualizzate sullo schermo dell'utente. Un tipico DSL viene visualizzato come una raccolta di icone o rettangoli connessi tramite frecce.

La figura seguente illustra un modello di piccole dimensioni in un linguaggio DSL basata su diagramma:

![Modello dell'albero della famiglia Tudor](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>Operazioni eseguibili con linguaggi specifici di dominio

Una tipica applicazione di un linguaggio DSL consiste nel generare codice programma o altri elementi. Quando si definisce il linguaggio DSL, è possibile definire *modelli di testo* che leggere un modello del DSL e generare file di testo.

Ad esempio, è possibile scrivere modelli che accettano un piano di aeroporto e generano parte del software per la gestione, nonché alcuni dei documenti che descrivono il piano utente bagagli.

Dopo aver definito un linguaggio DSL, è possibile distribuirlo ad altri utenti che possono installarlo nel proprio computer. Gli utenti del linguaggio DSL possono creare e modificare i modelli di Visual Studio.

È anche possibile definire comandi di menu e altri strumenti che consentono agli utenti di modificare il linguaggio DSL, vincoli di convalida per garantire che il linguaggio DSL è utilizzato correttamente e modelli di elementi che consentono agli utenti di creare nuove istanze. È possibile eseguire il wrapping di uno o più soluzioni DSL con i propri strumenti e altre estensioni di Visual Studio come pacchetto integrato.

In genere, un linguaggio specifico di dominio viene creato quando un team di sviluppo è necessario scrivere codice simile per diversi prodotti. Ad esempio, una società specializzata in sistemi di gestione dei bagagli potrebbe definire un linguaggio DSL track bagagli da cui è possibile generare il codice per ogni installazione di. I vantaggi del DSL sono possibile riconosciute dai clienti, che il codice generato da quest'ultimo sia affidabile e che il sistema può essere aggiornato rapidamente se cambiano i requisiti dei clienti.

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Consente di creare un linguaggio specifico di dominio che dispone della finestra di progettazione con interfaccia grafica e il proprio notazione dei diagrammi e quindi usare il linguaggio per generare codice sorgente appropriato per ogni progetto.

## <a name="domain-specific-development"></a>Sviluppo specifico di dominio

Sviluppo specifico di dominio è il processo di identificazione le parti delle applicazioni che possono essere modellate tramite un linguaggio specifico di dominio e quindi costruendo il linguaggio e distribuirlo agli sviluppatori di applicazioni. Gli sviluppatori di usano il linguaggio specifico di dominio per creare modelli specifici per le proprie applicazioni, utilizzare i modelli per generare codice sorgente e quindi usare il codice sorgente per sviluppare le applicazioni.

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspetti dello sviluppo specifico di dominio con interfaccia grafico

Un linguaggio specifico di dominio con interfaccia grafico deve includere le funzionalità seguenti:

- Notation

- Modello di dominio

- Generazione dell'artefatto

- Serializzazione

- Integrazione con Visual Studio

### <a name="notation"></a>Notation

Un linguaggio specifico di dominio deve avere un set relativamente ridotto di elementi che possono essere facilmente definite ed esteso in modo da rappresentare costrutti specifici di dominio. È costituito da una notazione di forme che rappresentano gli elementi, e i connettori, che rappresentano le relazioni tra gli elementi, su una superficie diagramma grafico. In [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], le forme possono essere esteso e migliorate per rappresentare gli elementi del linguaggio specifico di dominio di.

### <a name="domain-model"></a>Modello di dominio

Un linguaggio specifico di dominio è necessario combinare i set di elementi e le relazioni tra loro in una grammatica coerente. Deve anche definire se le combinazioni di elementi e relazioni sono valide. Linguaggi di programmazione, ad esempio, impediscono in genere ereditarietà circolare, in cui una classe è derivata da una seconda classe e la seconda classe viene derivata dalla classe prima. I vincoli possono essere usati anche per esprimere la logica di business, ad esempio, una persona non può essere un dipendente di se stesso. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Usa i vincoli per esprimere i tipi di restrizioni che richiedono più linguaggi specifici di dominio.

### <a name="artifact-generation"></a>Generazione dell'artefatto

Uno degli scopi principali di un linguaggio specifico di dominio consiste nel generare un artefatto, ad esempio, il codice sorgente, un file XML o alcuni altri dati utilizzabili. In genere, una modifica nel modello indica una modifica l'elemento. È possibile usare [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] consente di generare elementi e rigenerarle quando si modifica il modello.

### <a name="serialization"></a>Serializzazione

Un linguaggio specifico di dominio deve essere mantenuto in una determinata forma che può essere modificato, salvato, chiusi e ricaricato. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Usa un formato XML che consente di definire e personalizzare il modo in cui il linguaggio specifico di dominio viene serializzato o persistente.

### <a name="integration-with-visual-studio"></a>Integrazione con Visual Studio

Poiché [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] è ospitato in Visual Studio, che estende numerose finestre di Visual Studio e controlli. Consente inoltre di personalizzare il comportamento dei comandi di menu, gli elementi della casella degli strumenti e altri elementi dell'interfaccia utente.

È anche possibile creare un adattatore ModelBus per il linguaggio specifico di dominio. Questa scheda consente di elementi all'interno di un modello e consente di scrivere codice che possono accedere e aggiornare un'istanza del DSL e un modello di riferimento. Mediante il meccanismo di ModelBus potente, è possibile scrivere le estensioni di Visual Studio che funzionano con più modelli. È anche possibile scrivere applicazioni autonome che funzionano con i modelli. Per altre informazioni, vedere [l'integrazione di modelli tramite Modelbus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="benefits-of-domain-specific-development"></a>Vantaggi di sviluppo specifico di dominio

Un linguaggio specifico di dominio può offrire i vantaggi seguenti:

- Contiene costrutti che rientrano esattamente lo spazio dei problemi.

     Diversamente dai linguaggi per utilizzo generico, un linguaggio specifico di dominio è costituito da elementi e relazioni che rappresentano direttamente la logica dello spazio dei problemi. Ad esempio, un'applicazione di polizza assicurativa deve includere gli elementi per i criteri e le attestazioni. Un linguaggio specifico di dominio rende più semplice progettare l'applicazione e trovare e correggere gli errori di logica.

- Consente di non sviluppatori e le persone che non conoscono il dominio comprendere la struttura complessiva.

     Usando un linguaggio specifico di dominio con interfaccia grafico, è possibile creare una rappresentazione visiva del dominio in modo che non si occupano di sviluppo possono comprenderne facilmente l'architettura dell'applicazione.

- Rende più semplice creare un prototipo dell'applicazione finale.

     Gli sviluppatori possono usare il codice che genera il modello per creare un'applicazione di prototipo che mostrino ai client.

## <a name="the-process-of-domain-specific-development"></a>Il processo di sviluppo specifico di dominio

La maggior parte dei team di sviluppo software che usano linguaggi specifici di dominio seguire questi passaggi per creare e usare i propri modelli:

-   Il team consente di distinguere le parti variabili del dominio dalle parti che non cambiano mai.

-   Gli sviluppatori di scrivere codice per le parti fisse e lasciare i punti di estensione per le parti variabili.

-   Il responsabile dello sviluppo di software o il progettista crea un linguaggio specifico di dominio che incorpora i modelli di progettazione delle parti fisse del dominio e i punti di estensione per le parti variabili.

-   Il responsabile dello sviluppo di software o il progettista distribuisce il linguaggio specifico di dominio per gli sviluppatori delle diverse applicazioni che produce il team.

-   Ogni sviluppatore crea un modello che si applica all'applicazione specifica.