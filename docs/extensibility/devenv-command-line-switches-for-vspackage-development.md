---
title: Opzioni di Command-Line Devenv per lo sviluppo vspackage | Microsoft Docs
description: Informazioni su come gli sviluppatori possono automatizzare le attività dalla riga di comando quando eseguono devenv.exe, il file che avvia l Visual Studio IDE.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Setup command line switch
- /ResetSkipPkgs command line switch
- /RootSuffix command line switch
- /SafeMode command line switch
- /Splash command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4ea08b4714a79e09fce5933b67997a032532481f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904243"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Opzioni della riga di comando devenv per lo sviluppo di pacchetti VSPackage

Visual Studio consente agli sviluppatori di automatizzare le attività dalla riga di comando quando eseguono , il file che avvia l Visual Studio `devenv.exe` IDE.

 Le attività includono:

- Distribuzione di applicazioni in configurazioni predefinite dall'esterno dell'IDE.

- Compilazione automatica di progetti usando impostazioni di compilazione predefinite o configurazioni di debug.

- Caricamento dell'IDE in configurazioni specifiche, il tutto dall'esterno dell'IDE. È anche possibile personalizzare l'IDE all'avvio.

## <a name="guidelines-for-switches"></a>Linee guida per i commutatori

Visual Studio documentazione descrive le opzioni della riga di comando a `devenv` livello di utente. Per altre informazioni, vedere [Opzioni della riga di comando Devenv](../ide/reference/devenv-command-line-switches.md). Lo strumento supporta anche opzioni della riga di comando aggiuntive utili per lo sviluppo, la distribuzione e il debug di `devenv` VSPackage.

| Opzione della riga di comando | Descrizione |
|---------------------| - |
| `/ResetSkipPkgs` | Cancella tutte le opzioni di caricamento ignorate che sono state aggiunte dagli utenti che vogliono evitare il caricamento di VSPackage problematici, quindi avvia Visual Studio. La presenza di un tag SkipLoading disabilita il caricamento di un VSPackage. La cancellazione del tag abilita nuovamente il caricamento del pacchetto VSPackage.<br /><br /> Questa opzione non accetta argomenti. |
| `/RootSuffix` | Avvia Visual Studio usando un percorso alternativo. Il comando seguente viene eseguito dal collegamento creato dal programma di Visual Studio SDK:<br /><br /> `devenv /RootSuffix exp`<br /><br /> In questo caso, `exp` identifica una posizione con un suffisso specifico ( ad esempio, anziché `10.0Exp` `10.0` ). L'istanza sperimentale consente di eseguire il debug di un VSPackage separatamente dall'istanza di Visual Studio che si sta usando per scrivere codice.<br /><br /> Questa opzione può assumere qualsiasi stringa che identifica un percorso creato usando VSRegEx.exe. Per altre informazioni, vedere [Istanza sperimentale](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Avvia Visual Studio in modalità provvisoria, caricando solo l'IDE e i servizi predefiniti. L'opzione impedisce il caricamento di tutti i pacchetti VSPackage di terze parti `/SafeMode` all'Visual Studio, garantendo un'esecuzione stabile.<br /><br /> Questa opzione non accetta argomenti. |
| `/Setup` | Forza Visual Studio di unire i metadati delle risorse che descrivono menu, barre degli strumenti e gruppi di comandi da tutti i pacchetti VSPackage disponibili. È possibile eseguire questo comando solo come amministratore. <br /><br /> Questa opzione non accetta argomenti. Il comando `devenv /Setup` viene in genere eseguito come ultimo passaggio del processo di installazione. L'uso `/Setup` dell'opzione non avvia l'IDE.|
| `/Splash` | Mostra la Visual Studio iniziale, come di consueto, e quindi visualizza una finestra di messaggio prima di visualizzare l'IDE principale. La finestra di messaggio consente di studiare la schermata iniziale, ad esempio per verificare la presenza di un'icona del prodotto VSPackage.<br /><br /> Questa opzione non accetta argomenti. |

## <a name="see-also"></a>Vedere anche

- [Aggiungere opzioni della riga di comando](../extensibility/adding-command-line-switches.md)
- [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md)
