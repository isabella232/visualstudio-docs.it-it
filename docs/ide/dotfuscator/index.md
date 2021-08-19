---
title: Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: overview
keywords: Dotfuscator, Dotfuscator CE, Dotfuscator Community, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protezione, edizione community, offuscamento, .NET, gratis, Visual Studio 2019, Visual Studio 2017, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
description: Informazioni su come proteggere le applicazioni .NET con la copia gratuita di Dotfuscator Community inclusa in Visual Studio 2017.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 6f3a23e13d37b3c71a8ab5b7f680e16d51ca3164
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101856"
---
# <a name="dotfuscator-community"></a>Dotfuscator Community

***PreEmptive Protection - Dotfuscator*** offre una soluzione di protezione completa per applicazioni .NET, facilmente integrabile in un ciclo di sviluppo software sicuro.
Questa soluzione offre funzionalità di protezione avanzata ed eliminazione per le applicazioni progettate per desktop, dispositivi mobili o server e per le applicazioni incorporate, in modo da proteggere segreti commerciali e altri dati di proprietà intellettuale, ridurre gli attacchi di pirateria e i rischi di contraffazione, nonché evitare manomissioni e operazioni di debug non autorizzate.
Dotfuscator viene eseguito sugli assembly compilati senza richiedere altre attività di programmazione e nemmeno l'accesso al codice sorgente.

![PreEmptive Protection - Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Importanza della protezione

La **protezione della proprietà intellettuale** è importante.
Il codice dell'applicazione contiene dettagli di progettazione e implementazione che possono essere considerati proprietà intellettuale.
Tuttavia, le applicazioni basate su .NET Framework [contengono metadati significativi e codice intermedio di alto livello][assemblies] ed è quindi possibile eseguirne il reverse engineering con facilità tramite uno dei numerosi strumenti automatizzati disponibili gratuitamente.
Causando l'interruzione della decompilazione, è possibile impedire la divulgazione non autorizzata di dati di proprietà intellettuale ed evitare di mostrare che il codice contiene segreti commerciali.
Dotfuscator può [offuscare][obfuscation] gli assembly .NET per impedire il reverse engineering, mantenendo invariato il comportamento dell'applicazione originale.

È inoltre importante **proteggere l'integrità dell'applicazione**.
Oltre al reverse engineering, l'applicazione può essere soggetta ad attacchi di pirateria o comunque ad azioni che ne alterano il comportamento in fase di esecuzione o ne modificano i dati.
Dotfuscator può consentire all'applicazione di [rilevare e gestire usi non autorizzati][checks], incluse eventuali manomissioni, operazioni di debug di terze parti e dispositivi rooted.

Per altre informazioni su come Dotfuscator è integrabile in un ciclo di sviluppo software sicuro, vedere la [pagina SDL App Protection][sdl-protection] (Protezione delle app nel ciclo di sviluppo software) di PreEmptive Solutions.

## <a name="about-dotfuscator-community"></a>Informazioni su Dotfuscator Community

Microsoft Visual Studio include una copia gratuita per uso personale di ***PreEmptive Protection - Dotfuscator Community***.
(Questa versione gratuita era nota in precedenza come Dotfuscator Community Edition o Dotfuscator CE.) Per istruzioni su come installare la versione di Dotfuscator Community inclusa in Visual Studio, vedere la [pagina dedicata all'installazione][install].

Dotfuscator Community offre un'ampia gamma di servizi di [protezione avanzata del software][software-protection] per sviluppatori, architetti e tester.
Esempi delle funzionalità di [offuscamento .NET][obfuscation] e di altre funzionalità di [protezione delle applicazioni][app-protection] incluse in Dotfuscator Community comprendono:

* *[Ridenominazione][renaming]* degli identificatori per rendere più difficile il reverse engineering degli assembly compilati.
* *[Anti-manomissione][tamper]* per rilevare l'esecuzione di applicazioni manomesse e terminare o gestire sessioni che hanno subito manomissioni.
* *[Anti-debug][debug]* per rilevare il collegamento di un debugger a un'applicazione in esecuzione e terminare o gestire le sessioni sottoposte a debug.
* *[Anti-dispositivi rooted][root]* per rilevare se l'applicazione è in uso in un dispositivo Android rooted e terminare o gestire le sessioni in tali dispositivi.
* *[Comportamenti di scadenza delle applicazioni][shelflife]* che codificano una data di "fine vita" e terminano le sessioni delle applicazioni scadute.

Per informazioni dettagliate su queste funzionalità, incluso il modo in cui possono essere integrate nella strategia di protezione della propria applicazione, vedere la [pagina Funzionalità][capabilities].

Dotfuscator Community offre funzionalità predefinite per la protezione di base,
ma altre misure di protezione delle applicazioni sono disponibili per gli utenti registrati di Dotfuscator Community e per gli utenti di ***PreEmptive Protection - Dotfuscator Professional***, la soluzione di [offuscamento .NET][net-obfuscator] leader del settore.
Per informazioni su come migliorare Dotfuscator, vedere la [pagina Aggiornamenti][upgrades].

## <a name="getting-started"></a>Per iniziare

::: moniker range=">=vs-2019"

Per iniziare a usare Dotfuscator Community da Visual Studio, digitare `dotfuscator` nella **casella di ricerca** (CTRL+Q).

* Se Dotfuscator Community è già installato, nella **casella di ricerca** verrà visualizzata l'opzione per avviare Dotfuscator Community sotto l'intestazione *Menu*. Per informazioni dettagliate, vedere la [pagina introduttiva della guida dell'utente completa di Dotfuscator Community][get-started].
* Se Dotfuscator Community non è ancora installato, nella **casella di ricerca** verrà visualizzata invece la voce **Installa PreEmptive Protection - Dotfuscator** sotto l'intestazione *Singoli componenti*. Per informazioni dettagliate, vedere la [pagina Installazione][install].

::: moniker-end

::: moniker range="vs-2017"

Per iniziare a usare Dotfuscator Community da Visual Studio, digitare `dotfuscator` nella barra di ricerca **Avvio veloce** (CTRL+Q).

* Se Dotfuscator Community è già installato, in **Avvio veloce** verrà visualizzata l'opzione *Menu* per avviare l'interfaccia utente di Dotfuscator Community. Per informazioni dettagliate, vedere la [pagina introduttiva della guida dell'utente completa di Dotfuscator Community][get-started].
* Se Dotfuscator Community non è ancora installato, in **Avvio veloce** verrà visualizzata l'opzione *Installa* appropriata. Per informazioni dettagliate, vedere la [pagina Installazione][install].

::: moniker-end

È anche possibile ottenere la **versione più recente** di Dotfuscator Community dalla [pagina di download di Dotfuscator nel sito preemptive.com][download].

## <a name="full-documentation"></a>Documentazione completa

Questa pagina e le relative pagine secondarie presentano una panoramica di alto livello delle funzionalità di Dotfuscator Community insieme a [istruzioni per l'installazione dello strumento][install].

Vedere la [guida dell'utente completa di Dotfuscator Community nel sito preemptive.com][full] per istruzioni dettagliate sull'utilizzo, incluse quelle per [iniziare a usare l'interfaccia utente di Dotfuscator Community][get-started].

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  /dotnet/standard/assembly-format
[software-protection]:  https://www.preemptive.com/software-protection
[obfuscation]:  https://www.preemptive.com/obfuscation
[app-protection]:  https://www.preemptive.com/application-protection
[sdl-protection]:  https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[install]:  install.md
[capabilities]:  capabilities.md
[upgrades]:  upgrades.md

[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html
