---
title: Dotfuscator Community Edition (CE)
ms.date: 10/10/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protezione, community edition, offuscamento, .NET, gratuito, Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Informazioni su come proteggere le applicazioni .NET con la versione gratuita di Dotfuscator Community Edition inclusa in Visual Studio 2017.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: c34eec9f8eab1f870344ec6995bfcbd8fea8739c
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="dotfuscator-community-edition-ce"></a>Dotfuscator Community Edition (CE)

*PreEmptive Protection - Dotfuscator* offre una soluzione di protezione completa per applicazioni .NET, facilmente integrabile in un ciclo di sviluppo software sicuro.
Questa soluzione offre funzionalità di protezione avanzata ed eliminazione per le applicazioni progettate per desktop, dispositivi mobili o server e per le applicazioni incorporate, in modo da proteggere segreti commerciali e altri dati di proprietà intellettuale, ridurre gli attacchi di pirateria e i rischi di contraffazione, nonché evitare manomissioni e operazioni di debug non autorizzate.
Dotfuscator viene eseguito sugli assembly compilati senza richiedere altre attività di programmazione e nemmeno l'accesso al codice sorgente.

![PreEmptive Protection - Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Importanza della protezione

La **protezione della proprietà intellettuale** è importante.
Il codice dell'applicazione contiene dettagli di progettazione e implementazione che possono essere considerati proprietà intellettuale.
Tuttavia, le applicazioni basate su .NET Framework [contengono metadati significativi e codice intermedio di alto livello][assemblies] e possono quindi essere decompilate con facilità tramite uno dei numerosi strumenti automatizzati disponibili gratuitamente.
Causando l'interruzione della decompilazione, è possibile impedire la divulgazione non autorizzata di dati di proprietà intellettuale ed evitare di mostrare che il codice contiene segreti commerciali.
Dotfuscator può [offuscare][obfuscation] gli assembly .NET per ostacolare la decompilazione, mantenendo invariato il comportamento dell'applicazione originale.

È inoltre importante **proteggere l'integrità dell'applicazione**.
Oltre alla decompilazione, l'applicazione può essere soggetta ad attacchi di pirateria o comunque ad azioni che ne alterano il comportamento in fase di esecuzione o ne modificano i dati.
Dotfuscator può consentire all'applicazione di [rilevare, segnalare e gestire usi non autorizzati][checks], incluse eventuali manomissioni, operazioni di debug di terze parti e dispositivi rooted.

Per altre informazioni su come Dotfuscator è integrabile in un ciclo di sviluppo software sicuro, vedere la [pagina SDL App Protection][sdl-protection] (Protezione delle app nel ciclo di sviluppo software) di PreEmptive Solutions.

## <a name="about-dotfuscator-ce"></a>Nozioni di base su Dotfuscator CE

Microsoft Visual Studio 2017 include una copia gratuita per uso personale di ***PreEmptive Protection - Dotfuscator* Community Edition**, noto anche con il nome di Dotfuscator CE.
Per istruzioni su come installare la versione di Dotfuscator CE inclusa in Visual Studio 2017, vedere la [pagina Installation][install] (Installazione).

Dotfuscator CE offre un'ampia gamma di servizi di [protezione avanzata del software][software-protection] per sviluppatori, architetti e tester.
Esempi delle funzionalità di [offuscamento .NET][obfuscation] e di altre funzionalità di [protezione delle applicazioni][app-protection] incluse in Dotfuscator CE comprendono:

* *[Ridenominazione][renaming]* degli identificatori per rendere più difficile la decompilazione degli assembly compilati.
* *[Anti-manomissione][tamper]* per rilevare l'esecuzione di applicazioni manomesse, trasmettere avvisi di eventi imprevisti e terminare sessioni che hanno subito manomissioni.
* *[Anti-debug][debug]* per rilevare il collegamento di un debugger a un'applicazione in esecuzione, trasmettere avvisi di eventi imprevisti e terminare le sessioni sottoposte a debug.
* *[Anti-dispositivi rooted][root]* per rilevare se l'applicazione è in uso in un dispositivo Android rooted e terminare le sessioni in tali dispositivi.
* *[Comportamenti collegati alla scadenza delle applicazioni][shelflife]* che codificano una data del "ciclo di vita", trasmettono avvisi in caso di esecuzione delle applicazioni dopo la data di scadenza e terminano le sessioni delle applicazioni scadute.
* *[Rilevamento delle eccezioni][exceptions]* per monitorare le eccezioni non gestite che si verificano all'interno dell'applicazione.
* *Rilevamento dell'uso di [sessioni][sessions] e [funzionalità][features]* per determinare quali applicazioni, e relative versioni, vengono eseguite e quali funzionalità vengono usate in tali applicazioni.

Per informazioni dettagliate su queste funzionalità, incluso il modo in cui possono essere integrate nella strategia di protezione della propria applicazione, vedere la [pagina Capabilities][capabilities] (Funzionalità).

Dotfuscator CE offre funzionalità predefinite per la protezione di base,
ma altre misure di protezione delle applicazioni sono disponibili per gli utenti registrati di Dotfuscator CE e per gli utenti di *PreEmptive Protection - Dotfuscator* Professional Edition, la soluzione più avanzata di [offuscamento .NET][net-obfuscator] attualmente disponibile.
Per informazioni su come migliorare Dotfuscator, vedere la [pagina Upgrades][upgrades] (Aggiornamenti).

## <a name="getting-started"></a>Per iniziare

Per iniziare a usare Dotfuscator CE da Visual Studio, digitare `dotfuscator` nella barra di ricerca **Avvio veloce** (CTRL+Q).

* Se Dotfuscator CE è già installato, **Avvio veloce** visualizzerà l'opzione *Menu* per avviare l'interfaccia utente di Dotfuscator CE. Per informazioni dettagliate, vedere la [pagina introduttiva della Guida dell'utente completa di Dotfuscator CE][get-started].
* Se Dotfuscator CE non è ancora installato, **Avvio rapido** visualizzerà l'opzione di *installazione* appropriata. Per informazioni dettagliate, vedere la [pagina Installation][install] (Installazione).

È anche possibile ottenere la **versione più recente** di Dotfuscator CE dalla [pagina di download di Dotfuscator sul sito preemptive.com][download].

## <a name="full-documentation"></a>Documentazione completa

Questa pagina e le relative pagine secondarie presentano una panoramica di alto livello delle funzionalità di Dotfuscator CE insieme a [istruzioni per l'installazione dello strumento][install].

Vedere la [Guida dell'utente completa di Dotfuscator CE sul sito preemptive.com][full] per istruzioni dettagliate sull'utilizzo, incluse quelle per [iniziare a usare l'interfaccia utente di Dotfuscator CE][get-started].

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/en-us/dotnet/standard/assembly-format
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

[exceptions]:  https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_exceptions.html
[sessions]:  https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_sessions.html
[features]:  https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_features.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html