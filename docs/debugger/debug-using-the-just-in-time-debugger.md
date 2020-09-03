---
title: Eseguire il debug con il debugger JIT | Microsoft Docs
ms.date: 09/24/2018
ms.topic: how-to
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40b6a0e43a8d0980615087c946e5dd14deef1b0b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350576"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Eseguire il debug con il debugger JIT in Visual Studio

Il debug JIT può avviare automaticamente Visual Studio quando un'app in esecuzione all'esterno di errori o arresti anomali di Visual Studio. Con il debug JIT è possibile testare le app al di fuori di Visual Studio e aprire Visual Studio per avviare il debug quando si verifica un problema.

Il debug JIT funziona per le applicazioni desktop di Windows. Non funziona per le app di Windows universale o per il codice gestito ospitato in un'applicazione nativa, ad esempio i visualizzatori.

> [!TIP]
> Se si vuole semplicemente arrestare la visualizzazione della finestra di dialogo del debugger JIT, ma non è installato Visual Studio, vedere [disabilitare il debugger JIT](../debugger/just-in-time-debugging-in-visual-studio.md). Se è stato installato Visual Studio, potrebbe essere necessario [disabilitare il debug JIT dal registro di sistema di Windows](#disable-just-in-time-debugging-from-the-windows-registry).

## <a name="enable-or-disable-just-in-time-debugging-in-visual-studio"></a><a name="BKMK_Enabling"></a> Abilitare o disabilitare il debug JIT in Visual Studio

>[!NOTE]
>Per abilitare o disabilitare il debug JIT, è necessario eseguire Visual Studio come amministratore. L'abilitazione o la disabilitazione del debug just-in-Time imposta una chiave del registro di sistema e i privilegi di amministratore potrebbero essere necessari per modificare tale chiave. Per aprire Visual Studio come amministratore, fare clic con il pulsante destro del mouse sull'app Visual Studio e scegliere **Esegui come amministratore**.

È possibile configurare il debug JIT dalla finestra di dialogo Opzioni di Visual Studio **Tools**  >  **Options** (o **Debug**  >  **Opzioni**di debug).

**Per abilitare o disabilitare il debug JIT:**

1. Nel menu **strumenti** o **debug** Selezionare **Opzioni**  >  **debug JIT**  >  **(just-in-Time**).

   ![Abilitare o disabilitare il debug JIT](../debugger/media/dbg-jit-enable-or-disable.png "Abilitare o disabilitare il debug JIT")

1. Nella casella **Abilita debug JIT per questi tipi di codice** selezionare i tipi di codice per cui si vuole eseguire il debug JIT: **gestito**, **nativo**e/o **script**.

1. Selezionare **OK**.

Se si Abilita il debugger JIT, ma non si apre quando si verifica un arresto anomalo o un errore dell'app, vedere [risolvere i problemi relativi al debug](#jit_errors)JIT.

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Disabilitare il debug JIT dal registro di sistema di Windows

Il debug JIT può comunque essere abilitato anche se Visual Studio non è più presente nel computer. Se Visual Studio non è più installato, è possibile disabilitare il debug JIT modificando il registro di sistema di Windows.

**Per disabilitare il debug JIT modificando il registro di sistema:**

1. Dal menu **Start** di Windows eseguire l' **Editor del registro di sistema** (*regedit.exe*).

2. Nella finestra dell' **Editor del registro di sistema** individuare ed eliminare le voci del registro di sistema seguenti:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![Chiave del registro di sistema JIT](../debugger/media/dbg-jit-registry.png "Chiave del registro di sistema JIT")

3. Se nel computer è in esecuzione un sistema operativo a 64 bit, eliminare anche le voci del registro di sistema seguenti:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Assicurarsi di non eliminare o modificare altre chiavi del registro di sistema.

5. Chiudere la finestra **Editor del Registro di sistema**.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Abilitare il debug JIT di un Windows Form

Per impostazione predefinita, le app Windows Form dispongono di un gestore di eccezioni di primo livello che consente l'esecuzione dell'app se può essere ripristinata. Se un'app Windows Forms genera un'eccezione non gestita, viene visualizzata la finestra di dialogo seguente:

![Eccezione non gestita di Windows Form](../debugger/media/windowsformsunhandledexception.png "Eccezione non gestita di Windows Form")

Per abilitare il debug JIT invece della gestione degli errori standard di Windows Form, aggiungere le impostazioni seguenti:

- Nella `system.windows.forms` sezione del file *machine.config* o * \<app name>.exe.config* , impostare il `jitDebugging` valore su `true` :

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- In un'applicazione Windows Form C++, impostare anche `DebuggableAttribute` su `true` in un file con *estensione config* o nel codice. Se si esegue la compilazione con [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) e senza [/Og](/cpp/build/reference/og-global-optimizations), il compilatore imposta automaticamente questo attributo. Se si vuole eseguire il debug di una build di rilascio non ottimizzata, tuttavia, è necessario impostare `DebuggableAttribute` aggiungendo la riga seguente nel file *AssemblyInfo. cpp* dell'applicazione:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Per altre informazioni, vedere <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="use-just-in-time-debugging"></a><a name="BKMK_Using_JIT"></a>Usare il debug JIT
Questo esempio illustra l'esecuzione del debug JIT quando un'app genera un errore.

- Per eseguire questa procedura, è necessario che Visual Studio sia installato. Se non si dispone di Visual Studio, è possibile scaricare la [versione gratuita di Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

- Verificare che il debug JIT sia [abilitato](#BKMK_Enabling) in **strumenti**  >  **Opzioni**  >  **debug JIT**(  >  **just-in-Time**).

Per questo esempio, si renderà un'app console C# in Visual Studio che genera un' [eccezione NullReferenceException](/dotnet/api/system.nullreferenceexception).

1. In Visual Studio creare un'app console c# (**file**  >  **nuovo**  >  **progetto**  >  **Visual c#**  >  **applicazione console**) denominata *ThrowsNullException*. Per ulteriori informazioni sulla creazione di progetti in Visual Studio, vedere [procedura dettagliata: creare un'applicazione semplice](../get-started/csharp/tutorial-wpf.md).

1. Quando si apre il progetto in Visual Studio, aprire il file *Program.cs* . Sostituire il metodo Main () con il codice seguente, che stampa una riga nella console e quindi genera un'eccezione NullReferenceException:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Per compilare la soluzione, scegliere la configurazione **debug** (impostazione predefinita) o **versione** , quindi selezionare **Compila compilazione**  >  **soluzione**.

   > [!NOTE]
   > - Scegliere **debug** configurazione per l'esperienza di debug completa.
   > - Se si seleziona [Release](../debugger/how-to-set-debug-and-release-configurations.md) Configuration (configurazione versione), è necessario disattivare [Just My Code](../debugger/just-my-code.md) affinché questa procedura funzioni. In **strumenti**  >  **Opzioni**  >  **debug**deselezionare **Abilita Just My Code**.

   Per ulteriori informazioni sulle configurazioni della build, vedere [informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).

1. Aprire l'app compilata *ThrowsNullException.exe* nella cartella del progetto C# (con*estensione ..\ThrowsNullException\ThrowsNullException\bin\Debug* o *..\ThrowsNullException\ThrowsNullException\bin\Release*).

   Verrà visualizzata la finestra di comando seguente:

   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

1. Verrà visualizzata la finestra **di dialogo Scegli debugger JIT** .

   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

   In **debugger disponibili**selezionare **nuova istanza di \<your preferred Visual Studio version/edition> **, se non è già selezionata.

1. Selezionare **OK**.

   Il progetto ThrowsNullException viene aperto in una nuova istanza di Visual Studio, con l'esecuzione arrestata alla riga che ha generato l'eccezione:

   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

A questo punto è possibile avviare il debug. Se si esegue il debug di un'app reale, è necessario individuare il motivo per cui il codice genera l'eccezione.

> [!CAUTION]
> Se l'app contiene codice non attendibile, viene visualizzata una finestra di dialogo di avviso di sicurezza che consente di decidere se procedere con il debug. Prima di continuare il debug, decidere se considerare attendibile il codice. Se il codice è stato scritto da altri, Se l'applicazione è in esecuzione in un computer remoto, assicurarsi di riconoscere il nome del processo. Se l'app è in esecuzione localmente, prendere in considerazione la possibilità di eseguire codice dannoso nel computer. Se si decide che il codice è attendibile, fare clic su **OK**. In caso contrario, selezionare **Annulla**.

## <a name="troubleshoot-just-in-time-debugging"></a><a name="jit_errors"></a> Risolvere i problemi di debug just-in-Time

Se il debug JIT non viene avviato quando un'app si arresta in modo anomalo, anche se è abilitata in Visual Studio:

- Segnalazione errori Windows possibile eseguire la gestione degli errori nel computer.

  Per risolvere questo problema, utilizzare l'editor del registro di sistema per aggiungere un **valore DWORD** **disabilitato**, con **dati di valore** pari a **1**, alle chiavi del registro di sistema seguenti:

  - **Segnalazione errori HKEY_LOCAL_MACHINE \Software\Microsoft\Windows\Windows**

  - (Per computer a 64 bit): **HKEY_LOCAL_MACHINE segnalazione errori \software\wow6432node\microsoft\windows\windows**

  Per ulteriori informazioni, vedere [. Impostazioni WER](/windows/desktop/wer/wer-settings).

- Un problema noto di Windows potrebbe causare l'esito negativo del debugger JIT.

  La correzione consiste nell'aggiungere un **valore DWORD** di **auto**, con i **dati di valore** **1**, alle chiavi del registro di sistema seguenti:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (Per computer a 64 bit): **HKEY_LOCAL_MACHINE \Software\wow6432node\microsoft\windows NT\CurrentVersion\AeDebug**

Durante il debug JIT potrebbero essere visualizzati i messaggi di errore seguenti:

- **Impossibile connettersi al processo bloccato. Il programma specificato non è un programma Windows o MS-DOS.**

    Il debugger ha tentato di connettersi a un processo in esecuzione con un altro utente.

    Per risolvere questo problema, in Visual Studio aprire **debug**  >  **Connetti a processo**e individuare il processo di cui si vuole eseguire il debug nell'elenco **processi disponibili** . Se non si conosce il nome del processo, trovare l'ID del processo nella finestra di dialogo **debugger JIT di Visual Studio** . Selezionare il processo nell'elenco **processi disponibili** e selezionare **Connetti**. Selezionare **No** per chiudere la finestra di dialogo debugger JIT.

- **Impossibile avviare il debugger perché nessun utente è connesso.**

    Nessun utente è connesso alla console, pertanto non è presente alcuna sessione utente per visualizzare la finestra di dialogo di debug just-in-time.

    Per correggere questo problema, connettersi al computer.

- **Classe non registrata.**

    Il debugger ha tentato di creare una classe COM non registrata, probabilmente a causa di un problema di installazione.

    Per risolvere il problema, usare la Programma di installazione di Visual Studio per reinstallare o ripristinare l'installazione di Visual Studio.

## <a name="see-also"></a>Vedere anche

- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Opzioni, debug, finestra di dialogo JIT](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Avviso di sicurezza: può essere pericoloso connettersi a un processo appartenente a un account utente non attendibile. Se le seguenti sottostanti risultano sospette o non sicure, non stabilire la connessione al processo.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
