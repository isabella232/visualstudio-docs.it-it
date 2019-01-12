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
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3ed62724cd7d9c957e602975aebb3be8fc6547d1
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227356"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Opzioni della riga di comando devenv per lo sviluppo di VSPackage

Visual Studio consente agli sviluppatori di automatizzare le attività dalla riga di comando durante l'esecuzione `devenv.exe`, il file che avvia l'IDE di Visual Studio.  

 Le attività includono:  

- Distribuzione di applicazioni in configurazioni predefinite all'esterno dell'IDE.  

- Compilazione di progetti usando set di impostazioni automaticamente le impostazioni di compilazione o le configurazioni di debug.  

- Caricamento l'IDE in configurazioni specifiche, tutto all'esterno dell'IDE. È anche possibile personalizzare l'IDE all'avvio.  

## <a name="guidelines-for-switches"></a>Linee guida per le opzioni

Documentazione di Visual Studio descrive il livello di utente `devenv` della riga di comando. Per altre informazioni, vedere [opzioni della riga di comando Devenv](../ide/reference/devenv-command-line-switches.md). Il `devenv` lo strumento supporta anche altre opzioni della riga di comando che sono utili con VSPackage lo sviluppo, distribuzione e debug.  

| Opzione della riga di comando | Descrizione |
|---------------------| - |
| `/ResetSkipPkgs` | Cancella tutte le opzioni di caricamento skip che sono stati aggiunti dagli utenti che vogliono evitare il caricamento di pacchetti VSPackage problematici, quindi avvia Visual Studio. La presenza di un tag SkipLoading disabilita il caricamento di un pacchetto VSPackage. La cancellazione del tag riabilita il caricamento del pacchetto VSPackage.<br /><br /> Questa opzione non accetta argomenti. |
| `/RootSuffix` | Avvia Visual Studio usando un percorso alternativo. Mediante il collegamento creato dal programma di installazione di Visual Studio SDK viene eseguito il comando seguente:<br /><br /> `devenv /RootSuffix exp`<br /><br /> In questo caso `exp` identifica un percorso con un suffisso specifico (ad esempio, `10.0Exp` invece di `10.0`). L'istanza sperimentale consente di eseguire il debug di un pacchetto VSPackage separatamente dall'istanza di Visual Studio che si sta usando per scrivere codice.<br /><br /> Questa opzione può accettare qualsiasi stringa che identifica un percorso che è stato creato utilizzando VSRegEx.exe. Per altre informazioni, vedere [il processo dell'istanza sperimentale](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Avvia Visual Studio in modalità provvisoria, caricando solo l'IDE predefinito e i servizi. Il `/SafeMode` commutatore che impedisce il caricamento quando si avvia Visual Studio, garantendo un'esecuzione stabile di tutti i pacchetti VSPackage di terze parti.<br /><br /> Questa opzione non accetta argomenti. |
| `/Setup` | Forza Visual Studio l'unione dei metadati delle risorse che descrivono menu, barre degli strumenti e gruppi di comandi da tutti i pacchetti VSPackage disponibili. È solo possibile eseguire questo comando come amministratore. <br /><br /> Questa opzione non accetta argomenti. Il comando `devenv /Setup` viene in genere eseguito come ultimo passaggio del processo di installazione. Usare il `/Setup` commutatore non si avvia l'IDE.|
| `/Splash` | Mostra la schermata iniziale di Visual Studio come di consueto, schermata e quindi viene visualizzato il messaggio finestra prima di visualizzare l'IDE principale. La finestra di messaggio consente di esaminare la schermata iniziale (ad esempio, per verificare la presenza di un'icona di VSPackage del prodotto).<br /><br /> Questa opzione non accetta argomenti. |

## <a name="see-also"></a>Vedere anche

- [Aggiungere i parametri della riga di comando](../extensibility/adding-command-line-switches.md)
- [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md)