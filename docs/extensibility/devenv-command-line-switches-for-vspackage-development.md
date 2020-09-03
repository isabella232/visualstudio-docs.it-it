---
title: Opzioni della riga di comando devenv per lo sviluppo di VSPackage | Microsoft Docs
ms.date: 12/10/2018
ms.topic: conceptual
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad3a5125a730b9230959bbf9342b4c0a4823c4d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712187"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Opzioni della riga di comando devenv per lo sviluppo di pacchetti VSPackage

Visual Studio consente agli sviluppatori di automatizzare le attività dalla riga di comando durante l'esecuzione `devenv.exe` , il file che avvia l'IDE di Visual Studio.

 Le attività includono:

- Distribuzione di applicazioni in configurazioni predefinite dall'esterno dell'IDE.

- Creazione automatica di progetti mediante impostazioni di compilazione predefinite o configurazioni di debug.

- Caricamento dell'IDE in configurazioni specifiche, tutto dall'esterno dell'IDE. È anche possibile personalizzare l'IDE al momento dell'avvio.

## <a name="guidelines-for-switches"></a>Linee guida per le opzioni

La documentazione di Visual Studio descrive le opzioni della riga di comando a livello di utente `devenv` . Per ulteriori informazioni, vedere [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md). Lo `devenv` strumento supporta anche opzioni aggiuntive della riga di comando utili per lo sviluppo, la distribuzione e il debug di VSPackage.

| Opzione della riga di comando | Descrizione |
|---------------------| - |
| `/ResetSkipPkgs` | Cancella tutte le opzioni di caricamento ignorate che sono state aggiunte dagli utenti che desiderano evitare il caricamento di pacchetti VSPackage problematici, quindi avvia Visual Studio. La presenza di un tag SkipLoading disabilita il caricamento di un pacchetto VSPackage. La cancellazione del tag consente di riabilitare il caricamento del pacchetto VSPackage.<br /><br /> Questa opzione non accetta argomenti. |
| `/RootSuffix` | Avvia Visual Studio usando un percorso alternativo. Il comando seguente viene eseguito dal collegamento creato dal programma di installazione di Visual Studio SDK:<br /><br /> `devenv /RootSuffix exp`<br /><br /> In questo caso, `exp` identifica una posizione con un determinato suffisso, ad esempio `10.0Exp` invece di `10.0` . L'istanza sperimentale consente di eseguire il debug di un pacchetto VSPackage separatamente dall'istanza di Visual Studio usata per scrivere il codice.<br /><br /> Questa opzione può assumere qualsiasi stringa che identifichi un percorso creato con VSRegEx.exe. Per ulteriori informazioni, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Avvia Visual Studio in modalità provvisoria, caricando solo l'IDE e i servizi predefiniti. L' `/SafeMode` opzione impedisce il caricamento di tutti i pacchetti VSPackage di terze parti all'avvio di Visual Studio, garantendo un'esecuzione stabile.<br /><br /> Questa opzione non accetta argomenti. |
| `/Setup` | Impone a Visual Studio di unire i metadati delle risorse che descrivono i menu, le barre degli strumenti e i gruppi di comandi da tutti i pacchetti VSPackage disponibili. Questo comando può essere eseguito solo come amministratore. <br /><br /> Questa opzione non accetta argomenti. Il comando `devenv /Setup` viene in genere eseguito come ultimo passaggio del processo di installazione. L'uso dell' `/Setup` opzione non avvia l'IDE.|
| `/Splash` | Mostra la schermata iniziale di Visual Studio, come di consueto, e quindi Visualizza una finestra di messaggio prima di visualizzare l'IDE principale. La finestra di messaggio consente di esaminare la schermata iniziale, ad esempio per verificare la presenza di un'icona di prodotto VSPackage.<br /><br /> Questa opzione non accetta argomenti. |

## <a name="see-also"></a>Vedere anche

- [Aggiungi opzioni della riga di comando](../extensibility/adding-command-line-switches.md)
- [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md)
