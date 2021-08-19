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
ms.openlocfilehash: ef784a6c0d0816fdbf2ff93c5d4de09c2e4a40a5
ms.sourcegitcommit: f930bc28bdb0ba01d6f7cb48f229afecfa0c90cd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/18/2021
ms.locfileid: "122334687"
---
# <a name="upgrade-dotfuscator-community"></a>Aggiornare Dotfuscator Community

Dotfuscator Community mette numerose funzionalità di protezione delle applicazioni e protezione avanzata a disposizione immediata di tutti gli sviluppatori che usano Microsoft Visual Studio.
Gli utenti che eseguono l'aggiornamento della loro versione di Dotfuscator possono tuttavia sfruttare anche altre funzionalità.

Questo manuale dell'utente ***illustra PreEmptive Protection - Dotfuscator Community* 6**.
A seconda della cronologia di installazione e della versione di Visual Studio, è possibile che sia in esecuzione Dotfuscator Community 5, la versione principale precedente.
In tal caso, è consigliabile eseguire l'aggiornamento, perché è importante assicurarsi che al codice vengano [fornite le misure di protezione più recenti.][always-improving]
Gli aggiornamenti sono disponibili gratuitamente.

Questa pagina illustra come determinare la versione corrente, come eseguire l'aggiornamento alla versione 6, se necessario, e quali funzionalità sono state sostituite o rimosse tra le due versioni.

## <a name="determining-dotfuscators-version"></a>Determinazione della versione di Dotfuscator

Se non si è certi della versione di Dotfuscator in esecuzione, è possibile determinare la versione eseguendo una delle operazioni seguenti:

* Avviare l'interfaccia utente grafica [(GUI)][gui] di Dotfuscator Community scegliendo Strumenti dal **menu** Strumenti di Visual Studio e selezionando **PreEmptive Protection - Dotfuscator Community**.
  Nell'interfaccia utente grafica di Dotfuscator aprire il menu **?** e selezionare **Informazioni su...** per visualizzare la schermata Informazioni.
  Questa schermata elenca la versione di Dotfuscator.

* Se Dotfuscator è integrato nella compilazione con l'interfaccia della riga di comando [(ad][cli] esempio con le app [Xamarin),][xamarin] è anche possibile controllare i log di compilazione per una riga simile alla seguente:

  ```no-highlight
  Dotfuscator Community Version 5.42.0.9514-e0e25f754
  ```

  Potrebbe essere necessario aumentare il livello di dettaglio della compilazione per visualizzare questo testo.
  Per Visual Studio, vedere [Verbosity Impostazioni][verbosity].

Il primo numero intero della versione, prima del primo punto, indica la versione principale di `.` Dotfuscator.
Se si tratta di , è necessario eseguire i passaggi di aggiornamento in questa pagina, in modo da poter sfruttare le funzionalità e gli aggiornamenti di protezione più recenti di `5` Dotfuscator 6.

## <a name="upgrade-instructions"></a>Istruzioni per l'aggiornamento

Questa sezione include set di istruzioni per l'aggiornamento degli utilizzi tipici di Dotfuscator Community dalla versione 5 alla versione 6.

### <a name="installing-dotfuscator-6"></a>Installazione di Dotfuscator 6

Dotfuscator Community viene distribuito come estensione per Visual Studio.
Le istruzioni per installare Dotfuscator 6 variano in base alla versione Visual Studio disponibile:

* **Visual Studio 2019**.
  Dotfuscator Community 6 è incluso nelle versioni successive di Visual Studio 2019 (versione 16.10.0 e successive).
  [Aggiornare Visual Studio 2019 alla][vs-update] versione più recente.
  In questo modo, qualsiasi installazione di Dotfuscator Community 5 verrà aggiornata automaticamente a Dotfuscator Community 6.

    * Se Dotfuscator non è già installato, aggiornare prima Visual Studio e quindi vedere [Installazione][install].

    * Oltre alle versioni con Visual Studio, è sempre possibile ottenere le versioni più recenti di Dotfuscator Community dalla pagina [di download di Dotfuscator.][download]

* **Visual Studio 2017**.
  Questa versione di Visual Studio fornita solo con Dotfuscator Community 5.
  Tuttavia, è possibile installare o eseguire l'aggiornamento a Dotfuscator Community 6 dalla pagina Download di [Dotfuscator][download] e selezionando il collegamento di download appropriato.

  Eseguire il `.vsix` file scaricato e seguire le istruzioni per installare Dotfuscator Community 6 in Visual Studio.
  Verranno aggiornate le installazioni esistenti di Dotfuscator Community 5.

* **Versioni precedenti di Visual Studio.**
  Dotfuscator Community 6 non è supportato in queste versioni di Visual Studio.
  È consigliabile eseguire l'aggiornamento a una versione più recente di Visual Studio o da [Dotfuscator Community a Dotfuscator Professional][pro].

Se in [][register] precedenza era stato registrato Dotfuscator Community 5, tale registrazione verrà convertita automaticamente la prima volta che si esegue Dotfuscator Community 6.

### <a name="updating-paths-to-the-command-line-interface"></a>Aggiornamento dei percorsi all'interfaccia della riga di comando

Per le istruzioni sull'aggiornamento dell'interfaccia della riga di comando, vedere la pagina Aggiornamento da [Community 5][up-com] della Guida dell'utente completa di Dotfuscator Community'utente.

### <a name="upgrading-dotfuscator-config-files"></a>Aggiornamento dei file di configurazione di Dotfuscator

Per le istruzioni di aggiornamento dei file di configurazione, vedere la pagina Aggiornamento da [Community 5][up-com-d] della Guida dell'utente completa di Dotfuscator Community'utente.

### <a name="updating-xamarin-integration"></a>Aggiornamento dell'integrazione di Xamarin

Per le istruzioni sull'aggiornamento di Xamarin Integration, vedere la pagina Aggiornamento da [Community 5][up-com-xa] della Guida dell'utente completa di Dotfuscator Community'utente

### <a name="updating-references-to-attribute-libraries"></a>Aggiornamento dei riferimenti alle librerie di attributi

Per le istruzioni di aggiornamento dei riferimenti alle librerie di attributi, vedere la pagina Aggiornamento da [Community 5][up-com-li] della Guida dell'utente completa Community Dotfuscator.

## <a name="removed-features"></a>Funzionalità rimosse

Dotfuscator Community 6 introduce modifiche di rilievo rispetto a Dotfuscator Community 5.
Se si usa Dotfuscator Community 5, questa sezione descrive come gestire le modifiche che potrebbero richiedere modifiche alla compilazione o influire sull'output di Dotfuscator.
Un elenco completo delle modifiche è disponibile nel [log delle modifiche][changelog].

## <a name="registering-dotfuscator-community"></a>Registrazione di Dotfuscator Community

Gli utenti registrati di Dotfuscator Community ottengono l'accesso a funzionalità aggiuntive, ad esempio il [supporto della riga di comando][cli], che rendono più facile l'integrazione di Dotfuscator Community nel processo di compilazione automatico. Con la registrazione verrà anche concesso l'accesso a uno strumento integrato usato per la [decodifica delle tracce dello stack offuscate][decode-obfuscated].

La registrazione è veloce, semplice e gratuita.
Per registrare Dotfuscator Community, vedere [le istruzioni nella guida dell'utente completa di Dotfuscator Community][register-ce].

## <a name="upgrading-to-dotfuscator-professional"></a>Aggiornamento a Dotfuscator Professional

Mentre Dotfuscator Community offre un livello di protezione di base, l'aggiornamento a ***PreEmptive Protection - Dotfuscator Professional*** consente di accedere alle trasformazioni di offuscamento avanzate e alle funzionalità di protezione. Queste includono:

* *Protezione della proprietà intellettuale*
  * Opzioni di ridenominazione aggiuntive, tra cui Enhanced Overload Induction™ e selezione casuale degli identificatori.
  * Accesso alle trasformazioni di offuscamento a livello aziendale, incluse le [trasformazioni destinate ad annullare la decompilazione automatica del codice][control-flow].
  * La possibilità di [nascondere stringhe sensibili][string-encryption], rendendo impossibile una ricerca semplice del codice decompilato.
  * Possibilità di [incorporare in][watermarking]modo discreto le stringhe di proprietà e distribuzione negli assembly , (filigrana software) consentendo di determinare l'origine di perdite di software non autorizzate.
  * La possibilità di [combinare più assembly in uno solo][linking], rendendo ancora più difficile per gli utenti malintenzionati determinare i ruoli degli elementi di codice, poiché è stata eliminata la separazione dei ruoli.
  * La possibilità di [rimuovere automaticamente il codice non usato dall'applicazione][pruning], riducendo la quantità di codice sensibile inviato.
* *Protezione dell'integrità dell'applicazione*
  * [Comportamenti di difesa delle applicazioni][check-actions] aggiuntivi.
  * La possibilità di inserire codice anti-manomissione e anti-debug negli assembly `.dll`.
  * La possibilità di specificare un periodo di avviso prima della scadenza finale di un'applicazione.
  * La possibilità di comunicare il codice dell'applicazione durante un periodo di avviso di scadenza o dopo la scadenza.

Dotfuscator Professional è l'[obfuscator .NET][net-obfuscator] di riferimento del settore ed è adatto per gli sviluppatori aziendali che richiedono supporto, manutenzione e aggiornamenti di prodotto continui.
Dotfuscator Professional offre anche una migliore integrazione con Visual Studio e viene concesso in licenza per uso commerciale.

Per altre informazioni sulle funzionalità avanzate di protezione delle applicazioni di Dotfuscator Professional, visitare la pagina panoramica di [Dotfuscator][product-about] e confrontare [Dotfuscator Professional con Dotfuscator Community][product-compare].

[Le versioni di valutazione completamente supportate di Dotfuscator Professional sono][eval]disponibili su richiesta preemptive.com. .

## <a name="see-also"></a>Vedi anche

[Aggiornare Dotfuscator Community][full]

<!-- Copyright © 2021 PreEmptive Solutions, LLC -->

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

[Guida dell'utente Community Dotfuscator][home]

[always-improving]:  https://www.preemptive.com/always-improving
[gui]:  https://www.preemptive.com/dotfuscator/ce/docs/help/getting_started_gui.html
[xamarin]:  https://www.preemptive.com/dotfuscator/ce/docs/help/getting_started_xamarin.html
[verbosity]:  ../how-to-view-save-and-configure-build-log-files.md?view=vs-2019&preserve-view=true#to-change-the-amount-of-information-included-in-the-build-log
[vs-update]:  ../../install/update-visual-studio.md?view=vs-2019&preserve-view=true
[install]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html
[download]:  https://www.preemptive.com/products/dotfuscator/downloads
[pro]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[register]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_register.html
[up-com]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrade_from_5.html#pctoc-updating-paths-to-the-command-line-interface
[up-com-d]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrade_from_5.html#pctoc-upgrading-dotfuscator-config-files
[up-com-xa]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrade_from_5.html#pctoc-updating-xamarin-integration
[up-com-li]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrade_from_5.html#pctoc-updating-references-to-attribute-libraries
[changelog]:  https://www.preemptive.com/support/dotfuscator-support/dotfuscator-ce-change-log
[home]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html