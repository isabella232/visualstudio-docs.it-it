---
title: Opzioni della riga di comando di Devenv per lo sviluppo di VSPackage Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712187"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Opzioni della riga di comando devenv per lo sviluppo di pacchetti VSPackage

Visual Studio consente agli sviluppatori di automatizzare `devenv.exe`le attività dalla riga di comando durante l'esecuzione, il file che avvia l'IDE di Visual Studio.

 Le attività includono:

- Distribuzione di applicazioni in configurazioni predefinite dall'esterno dell'IDE.

- Compilazione automatica di progetti utilizzando impostazioni di compilazione preimpostate o configurazioni di debug.

- Caricamento dell'IDE in configurazioni specifiche, il tutto dall'esterno dell'IDE. È inoltre possibile personalizzare l'IDE all'avvio.

## <a name="guidelines-for-switches"></a>Linee guida per gli interruttori

La documentazione di Visual `devenv` Studio descrive le opzioni della riga di comando a livello utente. Per ulteriori informazioni, vedere [Opzioni della riga di comando Devenv](../ide/reference/devenv-command-line-switches.md). Lo `devenv` strumento supporta anche opzioni della riga di comando aggiuntive utili con lo sviluppo, la distribuzione e il debug di VSPackage.The tool also supports additional command-line switches that are useful with VSPackage development, deployment, and debugging.

| Opzione della riga di comando | Descrizione |
|---------------------| - |
| `/ResetSkipPkgs` | Cancella tutte le opzioni di caricamento ignora che sono state aggiunte dagli utenti che vogliono evitare il caricamento di VSPackage problematici, quindi avvia Visual Studio. La presenza di un tag SkipLoading disabilita il caricamento di un PACCHETTO VSPackage. Cancellazione del tag riabilita il caricamento del pacchetto VSPackage.<br /><br /> Questa opzione non accetta argomenti. |
| `/RootSuffix` | Avvia Visual Studio utilizzando un percorso alternativo. Il comando seguente viene eseguito dal collegamento creato dal programma di installazione di Visual Studio SDK:<br /><br /> `devenv /RootSuffix exp`<br /><br /> In questo `exp` caso, identifica una posizione con `10.0Exp` un `10.0`particolare suffisso (ad esempio, anziché ). L'istanza sperimentale consente di eseguire il debug di un VSPackage separatamente dall'istanza di Visual Studio che si sta utilizzando per scrivere codice.<br /><br /> Questa opzione può accettare qualsiasi stringa che identifica un percorso creato utilizzando VSRegEx.exe. Per ulteriori informazioni, vedere [Istanza sperimentale](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Avvia Visual Studio in modalità provvisoria, caricando solo l'IDE e i servizi predefiniti. L'opzione `/SafeMode` impedisce il caricamento di tutti i package VS di terze parti all'avvio di Visual Studio, garantendo l'esecuzione stabile.<br /><br /> Questa opzione non accetta argomenti. |
| `/Setup` | Impone a Visual Studio di unire i metadati delle risorse che descrivono menu, barre degli strumenti e gruppi di comandi da tutti i package VS disponibili. È possibile eseguire questo comando solo come amministratore. <br /><br /> Questa opzione non accetta argomenti. Il comando `devenv /Setup` viene in genere eseguito come ultimo passaggio del processo di installazione. L'utilizzo `/Setup` dello switch non avvia l'IDE.|
| `/Splash` | Viene visualizzata la schermata iniziale di Visual Studio, come di consueto, quindi viene visualizzata una finestra di messaggio prima di visualizzare l'IDE principale. La finestra di messaggio consente di studiare la schermata iniziale (ad esempio, per verificare la presenza di un VSPackage icona del prodotto).<br /><br /> Questa opzione non accetta argomenti. |

## <a name="see-also"></a>Vedere anche

- [Aggiungere opzioni della riga di comando](../extensibility/adding-command-line-switches.md)
- [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md)
