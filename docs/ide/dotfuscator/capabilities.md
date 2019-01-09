---
title: Funzionalità di Dotfuscator
ms.date: 10/10/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protezione, community edition, offuscamento, .NET, gratuito, Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Informazioni sulle funzionalità della versione gratuita di Dotfuscator Community Edition inclusa in Visual Studio 2017.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: f7054eabf20da08bb22df080b0c737222b556483
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963897"
---
# <a name="capabilities-of-dotfuscator"></a>Funzionalità di Dotfuscator

Questa pagina illustra le funzionalità di Dotfuscator Community Edition (Dotfuscator CE), con alcuni riferimenti alle opzioni avanzate disponibili tramite gli [aggiornamenti][upgrades].

Dotfuscator è un sistema *post-compilazione* per le applicazioni .NET.
Con Dotfuscator CE, gli utenti di Visual Studio possono [offuscare gli assembly][obfuscation] e inserire [misure di difesa attiva][checks] nell'applicazione, senza che Dotfuscator debba accedere al codice sorgente originale.
Dotfuscator protegge l'applicazione in diversi modi, creando una strategia per la protezione a più livelli.

Dotfuscator CE supporta una vasta gamma di tipi assembly e applicazioni .NET, tra cui la [piattaforma UWP (Universal Windows Platform) ] [ uwp] e [Xamarin][xamarin].

## <a name="intellectual-property-protection"></a>Protezione della proprietà intellettuale

La progettazione, il comportamento e l'implementazione di un'applicazione sono tipi di proprietà intellettuale (IP).
Le applicazioni create per .NET Framework sono però di fatto molto intuitive. È infatti molto facile decompilare gli assembly .NET, [in quanto contengono metadati di alto livello e codice intermedio][assemblies].

Dotfuscator CE include [offuscamento .NET] di base [ obfuscation] sotto forma di [ridenominazione][renaming].
L'offuscamento del codice con Dotfuscator riduce il rischio di accesso non autorizzato al codice sorgente tramite reverse engineering, impedendo che informazioni importanti sulla denominazione rimangano pubbliche.
L'offuscamento contribuisce anche a proteggere il codice dall'esame. Si tratta di un passaggio utile per garantire che l'IP sia legalmente protetto come segreto commerciale.

Molte delle [funzionalità di protezione dell'integrità dell'applicazione](#application-integrity-protection) di Dotfuscator CE possono ostacolare ulteriormente il reverse engineering.
Può succedere ad esempio che un attore non consentito tenti di associare un debugger all'istanza di un'applicazione in esecuzione per comprendere la logica di programma.
Dotfuscator può inserire un [comportamento anti-debug] [ debug] nell'applicazione per bloccare questo tentativo.

## <a name="application-integrity-protection"></a>Protezione dell'integrità dell'applicazione

Oltre a proteggere il codice sorgente, è anche importante assicurare che l'applicazione sia usata come previsto.
Gli utenti malintenzionati possono tentare di assumere il controllo dell'applicazione per aggirare i criteri di licenza (ad esempio, in caso di pirateria), per rubare o manipolare dati sensibili gestiti dall'applicazione o per modificare il comportamento dell'applicazione.

Con Dotfuscator CE è possibile inserire il [codice di convalida dell'applicazione][checks] negli assembly, comprese misure [antimanomissione][tamper], [anti-debug][debug] e [anti-dispositivi rooted][root].
Quando viene rilevato uno stato dell'applicazione non valido, il codice di convalida può [chiamare il codice dell'applicazione per risolvere la situazione nel modo appropriato][check-app].
In alternativa, se si preferisce non scrivere codice per gestire gli utilizzi dell'applicazione non validi, è anche possibile inserire con Dotfuscator comportamenti di [risposta][check-action] senza che sia necessario modificare il codice sorgente.

Molti di questi stessi metodi possono essere anche usati per applicare le [scadenze finali] [ shelflife] dei software di valutazione.

## <a name="see-also"></a>Vedere anche

[Dotfuscator Community Edition User Guide][full] (Guida dell'utente di Dotfuscator CE)

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
[uwp]:  https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]:  https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]:  upgrades.md

[obfuscation]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[check-app]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
[check-action]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html
