---
title: Preparazione al debug di progetti di console | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15ff4af24ac814dca73ee7032da2d66b29df641d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972209"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Debug della preparazione: Progetti di console (C#, C++, Visual Basic, F#)

La preparazione per il debug di un progetto console è simile a quella di un progetto Windows, ma è necessario tenere presente alcune ulteriori considerazioni. Per altre informazioni, vedere [Windows Forms Application](../debugger/debugging-preparation-windows-forms-applications.md), e [preparazione al debug:  Applicazioni Windows Forms (.NET)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100)). A causa delle similitudini esistenti tra tutte le applicazioni console, in questo argomento vengono trattati i seguenti tipi di progetto:  
  
- C#, Visual Basic, e F# applicazione Console  
  
- Applicazione console C++ (.NET)  
  
- Applicazione console C++ (Win32)  
  
  Potrebbe essere necessario specificare gli argomenti della riga di comando per l'applicazione console. Per altre informazioni, vedere [impostazioni di progetto per una configurazione di Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [impostazioni di progetto per una configurazione di Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), o [impostazioni di progetto per C# Debug Le configurazioni](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
  Come tutte le proprietà di progetto, questi argomenti sono persistenti tra le sessioni di debug e tra le sessioni di Visual Studio. Se in precedenza si è eseguito il debug dell'applicazione console, si tenga quindi presente che alcuni argomenti nella finestra di dialogo **Pagine delle proprietà di \<Progetto>** potrebbero essere stati ricavati dalle sessioni precedenti.  
  
  Un'applicazione console usa la finestra della **console** per accettare l'input e visualizzare i messaggi di output. Per scrivere le **Console** finestra, l'applicazione deve usare il **Console** oggetto anziché l'oggetto Debug. Per scrivere nella finestra di **output di Visual Studio**, usare l'oggetto Debug come di consueto. Assicurarsi di conoscere la posizione di scrittura dell'applicazione per evitare di cercare i messaggi nella finestra errata. Per altre informazioni, vedere [Classe Console](/dotnet/api/system.console), [Classe Debug](/dotnet/api/system.diagnostics.debug) e [Finestra di output](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Avvio dell'applicazione  
 Quando vengono avviate, alcune applicazioni console vengono eseguite fino al completamento, quindi si chiudono. Questo comportamento potrebbe non lasciare tempo sufficiente per interrompere l'esecuzione e per il debug. Per eseguire il debug di un'applicazione, utilizzare una delle procedure riportate di seguito per avviare l'applicazione:  
  
- Impostare un punto di interruzione nel codice e avviare l'applicazione.
  
- Avviare l'applicazione utilizzando **F10** (**Debug** > **Esegui istruzione/routine**) o **F11** (**Debug**  >  **Esegui istruzione**) e quindi spostarsi nel codice utilizzando le altre opzioni, ad esempio **esecuzione fare clic su**.
  
- Nell'editor del codice, fare doppio clic su una riga e selezionare **Esegui fino al cursore**.  
  
  Durante il debug di un'applicazione console, può essere necessario avviare l'applicazione dal prompt dei comandi anziché da Visual Studio. In tal caso, è possibile avviare l'applicazione dal prompt dei comandi e connettervi il debugger di Visual Studio. Per altre informazioni, vedere [connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
  Quando si avvia un'applicazione console da Visual Studio, la finestra della **console** viene visualizzata in secondo piano rispetto alla finestra di Visual Studio. Se si tenta di avviare l'applicazione console da Visual Studio senza alcun apparente risultato, provare a spostare la finestra di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Tipi di progetto Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)