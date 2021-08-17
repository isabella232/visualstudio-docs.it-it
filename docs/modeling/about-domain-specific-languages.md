---
title: Informazioni sui linguaggi specifici del dominio
description: Informazioni su come un linguaggio specifico di dominio (DSL) è progettato per esprimere le istruzioni in un particolare spazio di problemi o dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 54eeb75a623a7c20d0fad3f5f66e30c0b4617558
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069418"
---
# <a name="about-domain-specific-languages"></a>Informazioni sui linguaggi specifici del dominio

A differenza di un linguaggio per utilizzo generico, ad esempio C# o UML, un linguaggio specifico di dominio (DSL) è progettato per esprimere istruzioni in un particolare spazio di problemi o dominio.

Le DSL note includono espressioni regolari e SQL. Ogni linguaggio DSL è molto migliore di un linguaggio generico per la descrizione delle operazioni su stringhe di testo o un database, ma molto di più per descrivere idee che non sono nel proprio ambito. Anche i singoli settori hanno dSL propri. Nel settore delle telecomunicazioni, ad esempio, le lingue di descrizione delle chiamate sono ampiamente usate per specificare la sequenza di stati in una chiamata telefonica e nel settore dei viaggi aerei viene usato un linguaggio DSL standard per descrivere le prenotazioni di voli.

L'azienda e il progetto si occupano anche di set speciali di concetti che possono essere descritti con un DSL. Ad esempio, è possibile definire un DSL per una di queste applicazioni:

- Pianificare i percorsi di navigazione in un sito Web.

- Diagrammi di cablaggio per componenti elettronici.

- Reti di nastri trasportatori e apparecchiature per la gestione dei bagagli per un aeroporto.

Quando si progetta un DSL, si definisce una classe di dominio per ognuno dei concetti importanti del dominio, ad esempio una pagina Web, una lampadina o un banco check-in dell'aeroporto.  Per collegare *i concetti,* è possibile definire relazioni di dominio, ad esempio collegamento ipertestuale, cavo o nastro trasportatore.

Gli utenti del DSL creano *modelli.* I modelli *sono* istanze del DSL. Ad esempio, descrivono un sito Web specifico, il cablaggio di un particolare dispositivo o il sistema di gestione dei bagagli in un determinato aeroporto.

Gli utenti possono visualizzare un modello come diagramma o come Windows modulo. I modelli possono anche essere visualizzati come XML, ovvero come vengono archiviati. Quando si definisce un DSL, si definisce la modalità di visualizzazione delle istanze di ogni classe di dominio e relazione sullo schermo dell'utente. Un DSL tipico viene visualizzato come una raccolta di icone o rettangoli connessi tramite frecce.

La figura seguente illustra un modello di piccole dimensioni in un DSL diagrammatico:

![Modello dell'albero della famiglia Tudor](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>Cosa è possibile fare con le DSL

Un'applicazione tipica di un DSL è generare codice di programma o altri elementi. Quando si definisce il DSL, è possibile definire modelli di testo che leggono un modello del DSL e generano file di testo. 

Ad esempio, è possibile scrivere modelli che accettano un piano aeroportuale e generano parte del software per la gestione dei bagagli, nonché alcuni documenti utente che descrivono il piano.

Dopo aver definito un DSL, è possibile distribuirlo ad altri utenti che possono installarlo nei propri computer. Gli utenti del DSL possono creare e modificare modelli in Visual Studio.

È anche possibile definire comandi di menu e altri strumenti che consentono agli utenti di modificare il DSL, vincoli di convalida per garantire che il DSL venga usato correttamente e modelli di elemento che consentono agli utenti di creare nuove istanze. È possibile eseguire il wrapping di una o più DSL con i relativi strumenti e altre Visual Studio come pacchetto integrato.

In genere, viene creato un linguaggio specifico di dominio quando un team di sviluppo deve scrivere codice simile per diversi prodotti. Ad esempio, una società specializzata in sistemi di gestione dei bagagli potrebbe definire un DSL di traccia dei bagagli da cui generare parte del codice per ogni installazione. I vantaggi del DSL sono che i clienti possono comprenderlo, che il codice generato da esso è affidabile e che il sistema può essere aggiornato rapidamente se i requisiti dei clienti cambiano.

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] consente di creare un linguaggio specifico di dominio con la propria finestra di progettazione grafica e la notazione del diagramma e quindi di usare il linguaggio per generare il codice sorgente appropriato per ogni progetto.

## <a name="domain-specific-development"></a>Domain-Specific sviluppo

Lo sviluppo specifico di dominio è il processo di identificazione delle parti delle applicazioni che possono essere modellate usando un linguaggio specifico di dominio e quindi di costruire il linguaggio e distribuirlo agli sviluppatori di applicazioni. Gli sviluppatori usano il linguaggio specifico di dominio per costruire modelli specifici delle applicazioni, usare i modelli per generare codice sorgente e quindi usare il codice sorgente per sviluppare le applicazioni.

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspetti dello sviluppo Domain-Specific grafica

Un linguaggio specifico di dominio grafico deve includere le funzionalità seguenti:

- Notation

- Modello di dominio

- Generazione di artefatti

- Serializzazione

- Integrazione con Visual Studio

### <a name="notation"></a>Notation

Un linguaggio specifico di dominio deve avere un set ragionevolmente ridotto di elementi che possono essere facilmente definiti ed estesi per rappresentare costrutti specifici del dominio. Una notazione è costituita da forme, che rappresentano gli elementi, e connettori, che rappresentano le relazioni tra gli elementi, su una superficie del diagramma grafico. In [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] le forme possono essere estese e perfezionate per rappresentare gli elementi del linguaggio specifico di dominio.

### <a name="domain-model"></a>Modello di dominio

Un linguaggio specifico di dominio deve combinare il set di elementi e le relazioni tra di essi in una grammatica coerente. Deve anche definire se le combinazioni di elementi e relazioni sono valide. Ad esempio, i linguaggi di programmazione impediscono in genere l'ereditarietà circolare, in cui una classe è derivata da una seconda classe e la seconda classe è derivata dalla prima classe. I vincoli possono essere usati anche per esprimere la logica di business, ad esempio una persona non può dipendere da se stesso. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] usa i vincoli per esprimere i tipi di restrizioni richiesti dalla maggior parte dei linguaggi specifici di dominio.

### <a name="artifact-generation"></a>Generazione di artefatti

Uno degli scopi principali di un linguaggio specifico di dominio è generare un artefatto, ad esempio codice sorgente, un file XML o altri dati utilizzabili. In genere, una modifica nel modello implica una modifica nell'artefatto. È possibile [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] usare per generare elementi e rigenerarli quando si modifica il modello.

### <a name="serialization"></a>Serializzazione

Un linguaggio specifico di dominio deve essere reso persistente in un formato che può essere modificato, salvato, chiuso e ricaricato. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] usa un formato XML che consente di definire e personalizzare la modalità di serializzazione o persistenza del linguaggio specifico di dominio.

### <a name="integration-with-visual-studio"></a>Integrazione con Visual Studio

Poiché è ospitato in Visual Studio, estende molte finestre Visual Studio [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] controlli. Consente inoltre di personalizzare il comportamento di comandi di menu, elementi della casella degli strumenti e altri elementi dell'interfaccia utente.

È anche possibile creare un adattatore bus di modello per il linguaggio specifico di dominio. Questo adattatore consente di fare riferimento a un modello ed elementi all'interno di un modello e di scrivere codice in grado di accedere e aggiornare un'istanza del DSL. Usando il potente meccanismo del bus di modello, è possibile scrivere Visual Studio che funzionano con più modelli. È anche possibile scrivere applicazioni autonome che funzionano con i modelli. Per altre informazioni, vedere [Integrazione di modelli tramite Visual Studio Modelbus.](../modeling/integrating-models-by-using-visual-studio-modelbus.md)

## <a name="benefits-of-domain-specific-development"></a>Vantaggi dello Domain-Specific di sviluppo

Un linguaggio specifico di dominio può offrire i vantaggi seguenti:

- Contiene costrutti che si adattano esattamente allo spazio del problema.

     A differenza dei linguaggi per utilizzo generico, un linguaggio specifico di dominio è costituito da elementi e relazioni che rappresentano direttamente la logica dello spazio dei problemi. Ad esempio, un'applicazione di polizza assicurativa deve includere elementi per le polizze e i sinistri. Un linguaggio specifico di dominio semplifica la progettazione dell'applicazione e la ricerca e la correzione di errori di logica.

- Consente a non sviluppatori e utenti che non conoscono il dominio di comprendere la progettazione complessiva.

     Usando un linguaggio specifico di dominio grafico, è possibile creare una rappresentazione visiva del dominio in modo che gli sviluppatori non possano comprendere facilmente la progettazione dell'applicazione.

- Semplifica la creazione di un prototipo dell'applicazione finale.

     Gli sviluppatori possono usare il codice generato dal modello per creare un'applicazione prototipo che può essere mostrata ai client.

## <a name="the-process-of-domain-specific-development"></a>Processo di sviluppo Domain-Specific

La maggior parte dei team di sviluppo software che usano linguaggi specifici del dominio segue questa procedura per creare e usare i modelli:

- Il team distingue le parti variabili del dominio dalle parti che non cambiano mai.

- Gli sviluppatori scrivono codice per le parti fisse e lasciano i punti di estensione per le parti variabili.

- Lo sviluppatore di software principale o l'architetto crea un linguaggio specifico di dominio che incorpora i modelli di progettazione delle parti fisse del dominio e i punti di estensione per le parti variabili.

- Lo sviluppatore di software principale o l'architetto distribuisce il linguaggio specifico di dominio agli sviluppatori delle varie applicazioni che il team produce.

- Ogni sviluppatore crea un modello che si applica all'applicazione specifica.
