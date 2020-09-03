---
title: Informazioni sui linguaggi specifici del dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfd073b07902e3c0a9e33dfe9ae50d4947a50ef2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75597269"
---
# <a name="about-domain-specific-languages"></a>Informazioni sui linguaggi specifici del dominio

A differenza di un linguaggio generico, ad esempio C# o UML, un linguaggio specifico di dominio (DSL) è progettato per esprimere istruzioni in un particolare spazio di problemi o dominio.

DSLs noti includono le espressioni regolari e SQL. Ogni DSL è molto migliore di un linguaggio generico per la descrizione delle operazioni su stringhe di testo o un database, ma molto peggio per descrivere idee che esulano dal proprio ambito. I singoli settori hanno anche il proprio DSLs. Nel settore delle telecomunicazioni, ad esempio, le lingue per la descrizione delle chiamate vengono ampiamente usate per specificare la sequenza di stati in una telefonata e nel settore aereo viaggi viene usato un linguaggio DSL standard per descrivere le prenotazioni dei voli.

L'azienda e il progetto riguardano anche set speciali di concetti che possono essere descritti con un linguaggio DSL. Ad esempio, è possibile definire un linguaggio DSL per una di queste applicazioni:

- Piano di percorsi di navigazione in un sito Web.

- Diagrammi di collegamento per i componenti elettronici.

- Reti di nastri trasportatori e apparecchiature per la gestione dei bagagli per un aeroporto.

Quando si progetta un linguaggio DSL, si definisce una *classe di dominio* per ognuno dei concetti importanti del dominio, ad esempio una pagina Web, una lampada o un banco di archiviazione dell'aeroporto. È possibile definire *relazioni di dominio* come collegamento ipertestuale, Wire o un nastro trasportatore per collegare i concetti.

Utenti del linguaggio DSL creare *modelli.* I modelli sono *istanze* del linguaggio DSL. Ad esempio, descrivono un particolare sito Web o il cablaggio di un particolare dispositivo o il sistema di gestione bagagli in un particolare aeroporto.

Gli utenti possono visualizzare un modello come diagramma o Windows Form. I modelli possono essere visualizzati anche come XML, ovvero come vengono archiviati. Quando si definisce un linguaggio DSL, si definisce il modo in cui le istanze di ogni classe di dominio e relazione vengono visualizzate sullo schermo dell'utente. Un tipico linguaggio DSL viene visualizzato come una raccolta di icone o rettangoli connessi tramite frecce.

Nella figura seguente viene illustrato un modello di dimensioni ridotte in un linguaggio DSL diagrammatiche:

![Modello dell'albero della famiglia Tudor](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>Cosa è possibile fare con DSLs

Un'applicazione tipica di un linguaggio DSL consiste nel generare codice programma o altri artefatti. Quando si definisce il linguaggio DSL, è possibile definire *modelli di testo* che leggono un modello del linguaggio DSL e generano file di testo.

Ad esempio, è possibile scrivere modelli che accettano un piano aeroportuale e generano parte del software per la gestione dei bagagli, oltre ad alcuni documenti utente che descrivono il piano.

Quando è stato definito un linguaggio DSL, è possibile distribuirlo ad altri utenti che possono installarlo nei propri computer. Gli utenti del linguaggio DSL possono creare e modificare i modelli in Visual Studio.

È anche possibile definire i comandi di menu e altri strumenti che consentono agli utenti di modificare il linguaggio DSL, i vincoli di convalida per garantire che il linguaggio DSL venga usato correttamente e i modelli di elemento che consentono agli utenti di creare nuove istanze. È possibile eseguire il wrapping di uno o più DSLs con i relativi strumenti e altre estensioni di Visual Studio come pacchetto integrato.

In genere, viene creato un linguaggio specifico di dominio quando un team di sviluppo deve scrivere codice simile per diversi prodotti. Ad esempio, una società specializzata nei sistemi di gestione dei bagagli potrebbe definire un linguaggio DSL di traccia del bagaglio dal quale è possibile generare parte del codice per ogni installazione. I vantaggi del linguaggio DSL sono che possono essere riconosciuti dai clienti, che il codice generato dal codice è affidabile e che il sistema può essere aggiornato rapidamente se i requisiti dei clienti cambiano.

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] consente di creare un linguaggio specifico di dominio con una finestra di progettazione grafica personalizzata e una notazione del diagramma personalizzata, quindi utilizzare il linguaggio per generare il codice sorgente appropriato per ogni progetto.

## <a name="domain-specific-development"></a>Sviluppo specifico di dominio

Lo sviluppo specifico di un dominio è il processo di identificazione delle parti delle applicazioni che possono essere modellate utilizzando un linguaggio specifico di dominio, quindi la costruzione del linguaggio e la distribuzione degli sviluppatori di applicazioni. Gli sviluppatori utilizzano il linguaggio specifico di dominio per costruire modelli specifici per le proprie applicazioni, utilizzare i modelli per generare il codice sorgente e quindi utilizzare il codice sorgente per sviluppare le applicazioni.

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspetti dello sviluppo grafico specifico di un dominio

Un linguaggio grafico specifico di dominio deve includere le funzionalità seguenti:

- Notation

- Modello di dominio

- Generazione artefatti

- Serializzazione

- Integrazione con Visual Studio

### <a name="notation"></a>Notation

Un linguaggio specifico di dominio deve avere un set ragionevolmente ridotto di elementi che possono essere facilmente definiti ed estesi per rappresentare costrutti specifici del dominio. Una notazione è costituita da forme, che rappresentano gli elementi e i connettori, che rappresentano le relazioni tra gli elementi, in una superficie di un diagramma grafico. In [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , le forme possono essere estese e perfezionate per rappresentare gli elementi del linguaggio specifico di dominio.

### <a name="domain-model"></a>Modello di dominio

Un linguaggio specifico di dominio deve combinare il set di elementi e le relazioni tra di essi in una grammatica coerente. Deve inoltre definire se sono valide le combinazioni di elementi e relazioni. I linguaggi di programmazione, ad esempio, impediscono in genere l'ereditarietà circolare, in cui una classe è derivata da una seconda classe e la seconda classe è derivata dalla prima classe. I vincoli possono essere usati anche per esprimere la logica di business, ad esempio, una persona non può essere un dipendente di se stesso. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] USA vincoli per esprimere i tipi di restrizioni richiesti dalla maggior parte dei linguaggi specifici del dominio.

### <a name="artifact-generation"></a>Generazione artefatti

Uno degli scopi principali di un linguaggio specifico di dominio è quello di generare un artefatto, ad esempio il codice sorgente, un file XML o altri dati utilizzabili. In genere, una modifica nel modello indica una modifica nell'artefatto. È possibile utilizzare [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] per generare elementi e rigenerarli quando si modifica il modello.

### <a name="serialization"></a>Serializzazione

Un linguaggio specifico di dominio deve essere salvato in modo permanente in un formato che può essere modificato, salvato, chiuso e ricaricato. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Usa un formato XML che consente di definire e personalizzare la modalità di serializzazione o salvataggio permanente del linguaggio specifico di dominio.

### <a name="integration-with-visual-studio"></a>Integrazione con Visual Studio

Poiché [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] è ospitato in Visual Studio, estende molti controlli e finestre di Visual Studio. Consente inoltre di personalizzare il comportamento dei comandi di menu, degli elementi della casella degli strumenti e di altri elementi dell'interfaccia utente.

È inoltre possibile creare una scheda bus di modello per il linguaggio specifico di dominio. Questo adapter consente di fare riferimento a un modello ed elementi all'interno di un modello e consente di scrivere codice in grado di accedere a un'istanza del linguaggio DSL e di aggiornarla. Grazie al potente meccanismo del bus di modelli, è possibile scrivere estensioni di Visual Studio che funzionano con più modelli. È anche possibile scrivere applicazioni autonome che funzionano con i modelli. Per altre informazioni, vedere [integrazione di modelli tramite ModelBus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="benefits-of-domain-specific-development"></a>Vantaggi dello sviluppo specifico di dominio

Un linguaggio specifico di dominio può offrire i vantaggi seguenti:

- Contiene costrutti che corrispondono esattamente allo spazio del problema.

     A differenza dei linguaggi generici, un linguaggio specifico di dominio è costituito da elementi e relazioni che rappresentano direttamente la logica dello spazio del problema. Ad esempio, un'applicazione di criteri assicurativi deve includere elementi per criteri e attestazioni. Un linguaggio specifico di dominio semplifica la progettazione dell'applicazione e la ricerca e la correzione degli errori di logica.

- Consente a utenti non sviluppatori e utenti che non conoscono il dominio di comprendere il progetto generale.

     Utilizzando un linguaggio grafico specifico di dominio, è possibile creare una rappresentazione visiva del dominio in modo che gli sviluppatori non possano facilmente comprendere la progettazione dell'applicazione.

- Semplifica la creazione di un prototipo dell'applicazione finale.

     Gli sviluppatori possono utilizzare il codice generato dal modello per creare un'applicazione di prototipo che possa essere visualizzata ai client.

## <a name="the-process-of-domain-specific-development"></a>Processo di sviluppo specifico di dominio

La maggior parte dei team di sviluppo software che usano linguaggi specifici del dominio segue questa procedura per creare e usare i modelli:

- Il team distingue le parti variabili del dominio dalle parti che non cambiano mai.

- Gli sviluppatori scrivono il codice per le parti fisse e lasciano i punti di estensione per le parti variabili.

- Lo sviluppatore di software principale o l'architetto crea un linguaggio specifico di dominio che incorpora i modelli di progettazione delle parti fisse del dominio e i punti di estensione per le parti variabili.

- Lo sviluppatore di software principale o l'architetto distribuisce il linguaggio specifico di dominio agli sviluppatori delle diverse applicazioni prodotte dal team.

- Ogni sviluppatore crea un modello che si applica all'applicazione specifica.
