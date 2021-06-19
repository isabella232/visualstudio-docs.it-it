---
title: Impostazioni di progetto per una configurazione di debug VB | Microsoft Docs
description: Informazioni su come modificare le impostazioni del progetto per una configurazione Visual Basic di debug nella finestra Pagine delle proprietà di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f16d0dde62a23d8272cb89aec46f2ce952f18979
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385207"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Impostazioni di progetto per una configurazione di debug Visual Basic
È possibile modificare le impostazioni di progetto per una configurazione di debug [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nella finestra di dialogo **Pagine delle proprietà**, come descritto in [Configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md). Nelle tabelle riportate di seguito sono indicate le sezioni della finestra di dialogo **Pagine delle proprietà** in cui sono disponibili le impostazioni correlate al debugger.

> [!WARNING]
> Questo argomento non si applica alle app UWP. Vedere [Avviare una sessione di debug (VB, C#, C++ e XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

### <a name="debug-tab"></a>Scheda Debug

| Impostazione | Descrizione |
|------------------------------| - |
| **Configuration** | Imposta la modalità per la compilazione dell'applicazione. Le opzioni disponibili sono **Attiva (Debug)**, **Debug**, **Release**, **Tutte le configurazioni**. |
| **Azione di avvio** | Questo gruppo di controlli specifica l'azione che verrà eseguita quando si sceglie Avvia dal menu Debug.<br /><br /> -   **Avvia progetto** è l'impostazione predefinita e avvia il progetto di avvio per il debug. <br />-   **Avvia programma esterno** consente di avviare un programma che non fa parte di un progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e di stabilire una connessione al programma. Per altre informazioni, vedere [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **Avvia browser con URL** consente di eseguire il debug di un'applicazione Web. |
| **Argomenti della riga di comando** | Specifica gli argomenti della riga di comando per il programma da sottoporre a debug. Il nome del comando è il nome del programma specificato in Avvia programma esterno. Se l'opzione Azione di avvio è impostata su Avvia URL, gli argomenti della riga di comando verranno ignorati. |
| **Directory di lavoro** | Specifica la cartella di lavoro del programma sottoposto a debug. In [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] la cartella di lavoro è la cartella dalla quale viene avviata l'applicazione. La cartella di lavoro predefinita è \bin\Debug or \bin\Release, a seconda della configurazione corrente. |
| **Usare un computer remoto** | Quando la casella di controllo è selezionata, il debug remoto è attivato. Nella casella di testo è possibile digitare il nome di un computer remoto in cui verrà eseguita l'applicazione ai fini del debug oppure un [nome di server Msvsmon](../debugger/remote-debugging.md). Il percorso del file EXE nel computer remoto viene specificato dalla proprietà Percorso di output nella scheda Compilazione. Il percorso deve essere una directory condivisibile nel computer remoto. |
| **Debug codice non gestito** | Consente di eseguire il debug delle chiamate al codice Win32 nativo (non gestito) dall'applicazione gestita in uso. Ha lo stesso effetto della selezione di Misto per Tipo debugger in un progetto [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. |
| **Debug SQL Server** | Consente di eseguire il debug di oggetti di database di SQL Server. |

### <a name="compile-tab-press-advanced-compile-options-button"></a>Scheda Compila (scegliere il pulsante Opzioni di compilazione avanzate)

| Impostazione | Descrizione |
|---------------------------| - |
| **Abilita ottimizzazioni** | Si consiglia di non selezionare questa opzione. L'ottimizzazione rende più difficile il debug perché il codice effettivamente eseguito è diverso dal codice sorgente visualizzato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Se il codice è ottimizzato, non caricare i simboli per impostazione predefinita quando si esegue il debug con Just My Code. |
| **Genera informazioni di debug** | Questa impostazione, predefinita in entrambe le versioni di debug e di rilascio ed equivalente all'opzione del compilatore /debug, determina la creazione delle informazioni di debug in fase di compilazione. Il debugger utilizza tali informazioni per mostrare i nomi delle variabili e altri dati in un formato utile quando si esegue il debug. Se il programma viene compilato senza specificarle, la funzionalità del debugger risulterà limitata. Per altre informazioni, vedere [/debug](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| **Definire la costante DEBUG** | La definizione di questo simbolo attiva la compilazione condizionale delle funzioni di output della [classe Debug](/dotnet/api/system.diagnostics.debug). Quando è definito, i metodi della classe Debug generano l'output per la [finestra Output](../ide/reference/output-window.md). In caso contrario, tali metodi non verranno compilati e non verrà generato alcun output. Questo simbolo deve essere definito nella versione di debug e non nella versione di rilascio. La relativa definizione in una versione di rilascio determina la creazione di codice non necessario che rallenta l'esecuzione del programma. |
| **Definire una costante TRACE** | La definizione di questo simbolo attiva la compilazione condizionale delle funzioni di output della [classe Trace](/dotnet/api/system.diagnostics.trace). Quando è definito, i metodi della classe Trace generano l'output per la [finestra Output](../ide/reference/output-window.md). In caso contrario, tali metodi non verranno compilati e non verrà generato alcun output. Questo simbolo è definito per impostazione predefinita in entrambe le versioni di debug e di rilascio. |

## <a name="see-also"></a>Vedi anche
- [Impostazioni e preparazione del debugger](../debugger/debugger-settings-and-preparation.md)