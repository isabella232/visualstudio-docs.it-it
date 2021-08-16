---
title: Preparare il debug di progetti console | Microsoft Docs
description: Ottenere informazioni sulla preparazione per il debug di progetti console (C#, C++, Visual Basic, F#) in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ad23e0c60d995a59fcd64e952b1b52fa4e3df5ae0199468338fdceb92595ec34
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404512"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Preparazione del debug: progetti console (C#, C++, Visual Basic, F#)

La preparazione per il debug di un progetto Console è simile alla preparazione per il debug di un progetto Windows, con alcune considerazioni aggiuntive, ad esempio l'impostazione di argomenti della riga di comando e come sospendere l'app per il debug. Per altre informazioni, vedere [Preparazione del debug per un'app Windows Form](../debugger/debugging-preparation-windows-forms-applications.md). A causa delle similitudini esistenti tra tutte le applicazioni console, in questo argomento vengono trattati i seguenti tipi di progetto:

- Applicazione console C#, Visual Basic e F#

- Applicazione console C++ (.NET)

- Applicazione console C++ (Win32)

  Un'applicazione console usa la finestra della **console** per accettare l'input e visualizzare i messaggi di output. Per scrivere nella **finestra console,** l'applicazione deve usare l'oggetto **Console** anziché l'oggetto Debug. Per scrivere nella finestra di **output di Visual Studio**, usare l'oggetto Debug come di consueto. Assicurarsi di conoscere la posizione di scrittura dell'applicazione per evitare di cercare i messaggi nella finestra errata. Per altre informazioni, vedere [Classe Console](/dotnet/api/system.console), [Classe Debug](/dotnet/api/system.diagnostics.debug) e [Finestra di output](../ide/reference/output-window.md).

## <a name="set-command-line-arguments"></a>Impostare gli argomenti della riga di comando

Potrebbe essere necessario specificare gli argomenti della riga di comando per l'applicazione console. Per altre informazioni, vedere Project Impostazioni per una configurazione di [debug C++,](../debugger/project-settings-for-a-cpp-debug-configuration.md) [Project Impostazioni per una](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)configurazione di debug Visual Basic o Project Impostazioni per configurazioni di debug [C#.](../debugger/project-settings-for-csharp-debug-configurations.md)

Come tutte le proprietà di progetto, questi argomenti sono persistenti tra le sessioni di debug e tra le sessioni di Visual Studio. Pertanto, se l'applicazione console è un'applicazione di cui è stato fatto il debug in precedenza, tenere presente che potrebbero essere presenti argomenti delle sessioni precedenti immessi nella finestra di dialogo Pagine **\<Project> delle** proprietà.

## <a name="start-the-application"></a>Avviare l'applicazione

 Quando vengono avviate, alcune applicazioni console vengono eseguite fino al completamento, quindi si chiudono. Questo comportamento potrebbe non lasciare tempo sufficiente per interrompere l'esecuzione e per il debug. Per eseguire il debug di un'applicazione, utilizzare una delle procedure riportate di seguito per avviare l'applicazione:

- Impostare un punto di interruzione nel codice e avviare l'applicazione.

- Avviare l'applicazione usando **F10** (**Debug** step over ) o  >   **F11** (**Debug**  >  **Step Into**) e quindi spostarsi nel codice usando altre opzioni, ad esempio **Esegui per fare** clic su .

- Nell'editor di codice fare clic con il pulsante destro del mouse su una riga e **scegliere Esegui fino al cursore**.

  Durante il debug di un'applicazione console, può essere necessario avviare l'applicazione dal prompt dei comandi anziché da Visual Studio. In tal caso, è possibile avviare l'applicazione dal prompt dei comandi e connettervi il debugger di Visual Studio. Per altre informazioni, vedere [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

  Quando si avvia un'applicazione console da Visual Studio, la finestra della **console** viene visualizzata in secondo piano rispetto alla finestra di Visual Studio. Se si tenta di avviare l'applicazione console da Visual Studio senza alcun apparente risultato, provare a spostare la finestra di Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Debug del codice nativo](../debugger/debugging-native-code.md)
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
- [Preparare il debug di progetti C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Project Impostazioni per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)