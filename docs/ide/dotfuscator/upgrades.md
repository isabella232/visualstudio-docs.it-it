---
title: Aggiornare Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protezione, edizione community, offuscamento, .NET, gratis, Visual Studio 2019, Visual Studio 2017, Visual Studio, aggiornare, riga di comando
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: Informazioni su come aggiornare la copia gratuita di Dotfuscator Community inclusa in Visual Studio.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: d7820460ed2b652b2e92ea845f83d5130717ba07684945a2f6429fbc9c2d1d22
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121357934"
---
# <a name="upgrade-dotfuscator-community"></a>Aggiornare Dotfuscator Community

Dotfuscator Community mette numerose funzionalità di protezione delle applicazioni e protezione avanzata a disposizione immediata di tutti gli sviluppatori che usano Microsoft Visual Studio.
Gli utenti che eseguono l'aggiornamento della loro versione di Dotfuscator possono tuttavia sfruttare anche altre funzionalità.

## <a name="registering-dotfuscator-community"></a>Registrazione di Dotfuscator Community

Gli utenti registrati di Dotfuscator Community ottengono l'accesso a funzionalità aggiuntive, ad esempio il [supporto della riga di comando][cli], che rendono più facile l'integrazione di Dotfuscator Community nel processo di compilazione automatico. Con la registrazione verrà anche concesso l'accesso a uno strumento integrato usato per la [decodifica delle tracce dello stack offuscate][decode-obfuscated].

La registrazione è veloce, semplice e gratuita.
Per registrare Dotfuscator Community, vedere [le istruzioni nella guida dell'utente completa di Dotfuscator Community][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Mentre Dotfuscator Community offre un livello base di protezione, ***PreEmptive Protection - Dotfuscator Professional*** include trasformazioni di offuscamento e funzionalità di protezione avanzate come le seguenti:

* *Protezione della proprietà intellettuale*
  * Opzioni di ridenominazione aggiuntive, tra cui Enhanced Overload Induction™ e selezione casuale degli identificatori.
  * Accesso alle trasformazioni di offuscamento a livello aziendale, incluse le [trasformazioni destinate ad annullare la decompilazione automatica del codice][control-flow].
  * La possibilità di [nascondere stringhe sensibili][string-encryption], rendendo impossibile una ricerca semplice del codice decompilato.
  * La possibilità di [incorporare in modo discreto le stringhe di proprietà e distribuzione negli assembly][watermarking], consentendo di determinare l'origine delle perdite di software non autorizzate.
  * La possibilità di [combinare più assembly in uno solo][linking], rendendo ancora più difficile per gli utenti malintenzionati determinare i ruoli degli elementi di codice, poiché è stata eliminata la separazione dei ruoli.
  * La possibilità di [rimuovere automaticamente il codice non usato dall'applicazione][pruning], riducendo la quantità di codice sensibile inviato.
* *Protezione dell'integrità dell'applicazione*
  * [Comportamenti di difesa delle applicazioni][check-actions] aggiuntivi.
  * La possibilità di specificare un periodo di avviso prima della scadenza finale di un'applicazione.
  * La possibilità di comunicare il codice dell'applicazione durante un periodo di avviso di scadenza o dopo la scadenza.

Dotfuscator Professional è l'[obfuscator .NET][net-obfuscator] di riferimento del settore ed è adatto per gli sviluppatori aziendali che richiedono supporto, manutenzione e aggiornamenti di prodotto continui.
Dotfuscator Professional offre anche una migliore integrazione con Visual Studio e viene concesso in licenza per uso commerciale.

Per altre informazioni sulle funzionalità di protezione avanzata delle applicazioni di Dotfuscator Professional, visitare la [pagina della panoramica di Dotfuscator][product-about] e il [confronto con Dotfuscator Community][product-compare] di PreEmptive Solutions.
[Le versioni di valutazione completamente supportate sono disponibili sul sito preemptive.com][eval].

## <a name="see-also"></a>Vedi anche

[Questo articolo nella guida dell'utente completa di Dotfuscator Community][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[control-flow]:  https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]:  https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]:  https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]:  https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]:  https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]:  https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions

[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[eval]:  https://www.preemptive.com/eval-request

[product-about]:  https://www.preemptive.com/products/dotfuscator/overview
[product-compare]:  https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html
