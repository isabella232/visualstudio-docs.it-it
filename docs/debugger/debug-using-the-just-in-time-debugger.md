---
title: Eseguire il debug con il Debugger JIT | Microsoft Docs
ms.date: 09/24/2018
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8a9661673adf6cdab2d9a880ce27197a4e53127
ms.sourcegitcommit: 1c8e07b98fc0a44b5ab90bcef77d9fac7b3eb452
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/25/2019
ms.locfileid: "56796556"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Eseguire il debug con il Debugger JIT in Visual Studio

Debug Just-In-Time possibile avviare Visual Studio automaticamente quando un'app in esecuzione all'esterno degli errori di Visual Studio o da arresti anomali. Con Just-In-Time di debug, è possibile testare le app all'esterno di Visual Studio e aprire Visual Studio per avviare il debug quando si verifica un problema.

Il debug Just-In-Time funziona per le app desktop di Windows. Non funziona per le app di Windows universale o per il codice gestito ospitato in un'applicazione nativa, ad esempio visualizzatori.

> [!TIP]
> Se si desidera semplicemente arrestare la finestra di dialogo Debugger JIT venga visualizzato, ma non è installato Visual Studio, vedere [disabilitare il Debugger JIT](../debugger/just-in-time-debugging-in-visual-studio.md). Se si dispone di una volta installato Visual Studio, potrebbe essere necessario [Just-In-Time di disabilitare il debug dal Registro di sistema Windows](#disable-just-in-time-debugging-from-the-windows-registry).

##  <a name="BKMK_Enabling"></a> Abilitare o disabilitare il debug in Visual Studio Just-In-Time

>[!NOTE]
>Per abilitare o disabilitare il debug Just-In-Time, è necessario eseguire Visual Studio come amministratore. Abilitare o disabilitare Just-In-Time debug imposta una chiave del Registro di sistema e dei privilegi di amministratore potrebbero essere necessario modificare tale chiave. Per aprire Visual Studio come amministratore, fare doppio clic all'app di Visual Studio e scegli **Esegui come amministratore**.

È possibile configurare il debug da Visual Studio Just-In-Time **degli strumenti** > **opzioni** (o **Debug** > **opzioni**) finestra di dialogo.

**Per abilitare o disabilitare il debug JIT:**

1. Nel **degli strumenti** o **Debug** dal menu **opzioni** > **debug**  >   **Just-In-Time**.

   ![Abilitare o disabilitare il debug JIT](../debugger/media/dbg-jit-enable-or-disable.png "abilitare o disabilitare il debug JIT")

1. Nel **Abilita debug JIT per questi tipi di codice** , selezionare i tipi di codice da debug per eseguire il debug Just-In-Time: **gestito**, **Native**, e/o  **Script**.

1. Scegliere **OK**.

Se si Abilita Just-In-Time debugger, ma non si apre quando un'app si blocca o errori, vedere [debug JIT di risolvere i problemi](#jit_errors).

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Disabilitare il debug dal Registro di sistema Windows Just-In-Time

Il debug JIT può comunque essere abilitato anche se Visual Studio non è più presente nel computer. Se Visual Studio non viene più installato, è possibile disabilitare il debug modificando il Registro di sistema Windows Just-In-Time.

**Per disabilitare il debug JIT modificando il Registro di sistema:**

1.  Dalla finestra di Windows **avviare** menu, eseguire il **dell'Editor del Registro di sistema** (*regedit.exe*).

2.  Nel **dell'Editor del Registro di sistema** finestra, individuare ed eliminare le voci del Registro di sistema seguenti:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![Chiave del Registro di sistema JIT](../debugger/media/dbg-jit-registry.png "chiave del Registro di sistema JIT")

3.  Se il computer è in esecuzione un sistema operativo a 64 bit, anche eliminare le voci del Registro di sistema seguenti:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Assicurarsi di non eliminare o modificare qualsiasi altra chiave del Registro di sistema.

5.  Chiudi il **dell'Editor del Registro di sistema** finestra.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Abilitare Just-In-Time di debug di un Windows Form

Per impostazione predefinita, le app di Windows Form hanno un gestore di eccezioni di livello superiore che consente all'app di continuare l'esecuzione se è possibile un ripristino. Se un'app Windows Form genera un'eccezione non gestita, viene visualizzato la finestra di dialogo seguente:

![Eccezione non gestita di Windows Form](../debugger/media/windowsformsunhandledexception.png "eccezione non gestita di Windows Form")

Per abilitare il debug anziché la gestione degli errori di Windows Form standard Just-In-Time, aggiungere queste impostazioni:

-  Nel `system.windows.forms` sezione del *Machine. config* o  *\<nome app >. exe* file, impostare il `jitDebugging` valore `true`:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

-  In un'applicazione C++ Windows Form, impostare anche `DebuggableAttribute` al `true` in un *config* file o nel codice. Se si esegue la compilazione con [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) e senza [/Og](/cpp/build/reference/og-global-optimizations), il compilatore imposta automaticamente questo attributo. Se si desidera eseguire il debug di una build di rilascio non ottimizzata, tuttavia, è necessario impostare `DebuggableAttribute` aggiungendo la riga seguente dell'app *AssemblyInfo* file:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Per ulteriori informazioni, vedere <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="BKMK_Using_JIT"></a>Usare Just-In-Time di debug
 In questo esempio illustra quando un'app genera un errore di debug Just-In-Time.

 - È necessario disporre di Visual Studio è installato per eseguire la procedura seguente. Se non hai Visual Studio, è possibile scaricare la versione gratuita [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

 - Assicurarsi che Just-In-Time debug è [abilitata](#BKMK_Enabling) in **Tools** > **opzioni** > **debug**  >  **Just-In-Time**.

Per questo esempio, si renderanno un C# app console in Visual Studio che genera una [NullReferenceException](/dotnet/api/system.nullreferenceexception).

1. In Visual Studio, creare un C# app console (**File** > **New** > **progetto** > **C#**  >  **Applicazione console**) denominato *ThrowsNullException*. Per altre informazioni sulla creazione di progetti in Visual Studio, vedere [procedura dettagliata: creare una semplice applicazione](/visualstudio/get-started/csharp/tutorial-wpf).

1. Quando si apre il progetto in Visual Studio, aprire il *Program.cs* file. Sostituire il metodo Main () con il codice seguente, che stampa una riga nella console e quindi genera un'eccezione NullReferenceException:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Per compilare la soluzione, scegliere il **Debug** (impostazione predefinita) o **Release** configuration e quindi selezionare **compilare** > **Ricompila soluzione** .

   > [!NOTE]
   > - Scegli **Debug** configurazione per l'esperienza di debug completo.
   > - Se si seleziona [Release](../debugger/how-to-set-debug-and-release-configurations.md) la configurazione, è necessario disattivare [Just My Code](../debugger/just-my-code.md) per eseguire questa procedura. Sotto **degli strumenti** > **opzioni** > **debug**, deselezionare **Abilita Just My Code**.

   Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).

1. Aprire l'app compilata *ThrowsNullException.exe* nel C# cartella di progetto (*...\ThrowsNullException\ThrowsNullException\bin\Debug* oppure *...\ThrowsNullException\ ThrowsNullException\bin\Release*).

   Si verrà visualizzata la finestra di comando seguente:

   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

1. Il **Scegli Debugger JIT** verrà visualizzata la finestra di dialogo.

   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

   Sotto **debugger disponibili**, selezionare **nuova istanza \<la versione/edizione di Visual Studio preferita >**, se non è già selezionata.

1. Scegliere **OK**.

   Il progetto ThrowsNullException viene aperto in una nuova istanza di Visual Studio, con esecuzione interrotta alla riga che ha generato l'eccezione:

   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

È possibile avviare il debug a questo punto. Se si esegue il debug di una vera app, è necessario scoprire il motivo per cui il codice che genera l'eccezione.

> [!CAUTION]
> Se l'app contiene codice non attendibile, viene visualizzata una finestra di dialogo Avviso di sicurezza, che consente di decidere se eseguire il debug. Prima di continuare il debug, decidere se si considera affidabile il codice. Se il codice è stato scritto da altri, Se l'applicazione è in esecuzione in un computer remoto, assicurarsi di riconoscere il nome del processo. Se l'app è in esecuzione in locale, prendere in considerazione la possibilità di codice dannoso in esecuzione nel computer. Se si decide il codice è considerato attendibile, selezionare **OK**. In alternativa selezionare **Annulla**.

## <a name="jit_errors"></a> Risolvere i problemi di Just-In-Time di debug

Se Just-In-Time di debug non viene avviato durante l'arresto anomalo di un'app, anche se è abilitato in Visual Studio:

- Segnalazione errori Windows è stato possibile assumere la gestione degli errori nei computer in uso.

  Per risolvere questo problema, usare l'Editor del Registro di sistema per aggiungere un **valore DWORD** dei **disabilitato**, con **dati valore** del **1**, chiavi del Registro di sistema seguenti:

  - **Segnalazione errori HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows**

  - (Per computer a 64 bit): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows segnalazione errori**

  Per altre informazioni, vedere [. Le impostazioni di segnalazione errori Windows](https://docs.microsoft.com/windows/desktop/wer/wer-settings).

- Un problema noto di Windows potrebbe aver provocato Just-In-Time debugger esito negativo.

  La correzione consiste nell'aggiungere un **valore DWORD** dei **automatico**, con **dati valore** di **1**, chiavi del Registro di sistema seguenti:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (Per computer a 64 bit): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Si potrebbero vedere i messaggi di errore seguente durante Just-In-Time di debug:

- **Impossibile connettersi al processo bloccato. Il programma specificato non è un programma Windows o MS-DOS.**

    Il debugger ha tentato di connettersi a un processo in esecuzione in un altro utente.

    Per risolvere questo problema, in Visual Studio, aprire **Debug** > **Connetti a processo**e trovare il processo a cui si desidera eseguire il debug nel **processi disponibili** elenco. Se non si conosce il nome del processo, trovare l'ID del processo nel **Debugger JIT di Visual Studio** finestra di dialogo. Selezionare il processo nel **processi disponibili** elencare e selezionare **Attach**. Selezionare **No** per ignorare il Just-In-Time della finestra del debugger.

- **Impossibile avviare il debugger perché nessun utente è connesso.**

    Nessun utente è connesso alla console, pertanto non presenta alcuna sessione utente per visualizzare Just-In-Time della finestra di debug.

    Per correggere questo problema, connettersi al computer.

- **Classe non registrata.**

    Il debugger ha tentato di creare una classe COM che non è registrata, probabilmente a causa di un problema di installazione.

    Per risolvere questo problema, usare l'installazione di Visual Studio per reinstallare o riparare l'installazione di Visual Studio.

## <a name="see-also"></a>Vedere anche

- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Opzioni, debug, Just-In-Time nella finestra di dialogo](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Avviso di sicurezza: la connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti sono sospette o non si è certi della loro provenienza e del loro stato, non connettersi al processo.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
