---
title: R Tools per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: hero-article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: data-science
ms.openlocfilehash: c18eadd6cfcdf6fc77b204f78654126ceb1862db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-r-in-visual-studio"></a>Utilizzo di R in Visual Studio

R è un linguaggio estremamente estendibile, nonché un ambiente per l'elaborazione statistica e la grafica. Viene distribuito gratuitamente con la GNU General Public License, può contare su un forte supporto della community ed è noto per la possibilità di creare tracciati di alta qualità, inclusi formule e simboli matematici. Per altre informazioni su R, visitare il sito [r-project.org](https://www.r-project.org/about.html) e vedere [An Introduction to R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html) (Introduzione a R).

R Tools per Visual Studio (RTVS) è un'estensione [open-source](https://github.com/microsoft/RTVS) gratuita per Visual Studio 2017 e Visual Studio 2015 Update 3 (o versione successiva) rilasciato con licenza MIT. Un secondo componente open-source denominato [RHost](https://github.com/microsoft/R-Host), che esegue il collegamento ai file binari dell'interprete R, viene rilasciato con la GNU Public License V2.

> [!Note]
> Gli strumenti RTVS sono attualmente supportati solo in Visual Studio in Windows e non in Visual Studio per Mac.

Per sperimentare R in Visual Studio:

- [Installare R Tools](installation.md).
- Seguire le istruzioni riportate nell'argomento [Getting Started](getting-started-with-r.md) (Introduzione), nonché quelle fornite negli argomenti [Samples](getting-started-samples.md) (Esempi) e [Getting Help](getting-started-help.md) (Informazioni di supporto).

Usare i collegamenti seguenti per saperne di più sulle funzionalità correlate a R, nonché sulle funzionalità generali di Visual Studio.

| Funzionalità | Descrizione | Documentazione generale su Visual Studio | 
| --- | --- | --- |
| [Sistema del progetto di Visual Studio](projects.md) | È possibile organizzare e gestire i file correlati in una pratica struttura e sfruttare gli utili modelli per elementi quali il codice R, la documentazione R e R Markdown, nonché per le query SQL e le stored procedure. È inoltre possibile sfruttare la funzionalità di [gestione pacchetti](package-manager.md) e l'[integrazione con SQL Server](sql-server.md).  | [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Area di lavoro](workspaces.md) | RTVS supporta l'associazione ad aree di lavoro locali e remote, consentendo all'utente di sviluppare localmente codice R con set di dati di dimensioni ridotte e quindi di eseguire facilmente tale codice su computer più potenti basati su cloud con set di dati molto più grandi. | N/D |
| [Opzioni di R Tools](options.md) | Consentono di controllare i diversi aspetti di RTVS. | [Finestra di dialogo Opzioni](../ide/reference/options-dialog-box-visual-studio.md) |
| [Modifica avanzata, IntelliSense e frammenti di codice](code-editing.md) | Sono inclusi colorazione della sintassi, [IntelliSense](code-intellisense.md) in tutto il codice e in tutte le librerie, formattazione del codice, supporto per la firma, accesso alle definizioni, opzione per trovare tutti i riferimenti, [frammenti di codice](code-snippets.md) e altro ancora. | [Writing Code in the Code and Text Editor](../ide/writing-code-in-the-code-and-text-editor.md) (Scrittura di codice nell'Editor di testo e del codice) |
| [R Markdown](rmarkdown.md) | I documenti R Markdown consentono di condividere i risultati dei dati, con codice R integrato all'interno di blocchi di codice markdown. | N/D |
| [Finestra interattiva](interactive-repl.md) | Fornisce un'esperienza completa di REPL per R con la possibilità di eseguire facilmente il codice in un file di origine nella finestra interattiva. | N/D |
| [Visualizzazione dei dati](visualizing-data.md) | La creazione di tracciati è parte integrante dell'esperienza R e RTVS supporta diverse finestre dei tracciati indipendenti, ciascuna delle quali con la propria cronologia e la possibilità di spostare tracciati da una finestra all'altra. I tracciati possono essere salvati in bitmap e file PDF oppure copiati negli Appunti come bitmap o metafile.  | N/D |
| [Variable Explorer](variable-explorer.md) | Consente di esaminare le variabili in ambiti globali o specifici del pacchetto, con la possibilità di visualizzare tabelle ordinabili ed eseguire l'esportazione in CSV. | N/D |
| [Debug con funzionalità complete](debugging.md) | Include l'integrazione con la finestra interattiva. | [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md) |

Vedere anche [Domande frequenti](faq.md).

Il video seguente fornisce anche un breve riepilogo (5 minuti e 48 secondi) delle funzionalità di R Tools:

> [!VIDEO https://www.youtube.com/embed/RcSDEfMgUvU]

## <a name="send-us-your-feedback"></a>Inviateci i vostri commenti!

1. **Problemi GitHub**: il modo migliore per contattare il team RTVS consiste nel [segnalare un problema in GitHub](https://github.com/Microsoft/RTVS/issues) oppure usare il menu **R Tools > Feedback**.

1. **Invia smile/Invia faccia imbronciata**: il menu **R Tools > Feedback** è un modo rapido per inviare commenti e suggerimenti e allegare file di log RTVS per facilitare la diagnosi del problema. I log vengono scritti in `%temp%/RTVSlogs.zip`, nel caso li si voglia inviare separatamente. La registrazione è disabilitata se si è scelto di disattivare la telemetria di Visual Studio durante l'installazione oppure usando il comando di menu **Guida > Feedback > Impostazioni**.

1. **Messaggio di posta elettronica**: è possibile inviare commenti e suggerimenti direttamente al team all'indirizzo *rtvsuserfeedback (at) microsoft.com*.
