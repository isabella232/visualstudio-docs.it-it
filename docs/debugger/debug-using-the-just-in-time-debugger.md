---
title: Eseguire il debug con il Debugger JIT | Microsoft Docs
ms.custom: ''
ms.date: 09/24/18
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: ee4d79a5-a1d2-4418-a93f-dd57a53e1836
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7a2e6cfbd6d26d575bab5d7592f320779ffd8888
ms.sourcegitcommit: 000cdd1e95dd02e99a7c7c1a34c2f8fba6a632af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2018
ms.locfileid: "47168396"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Eseguire il debug con il Debugger JIT in Visual Studio
Debug Just-In-Time avvia Visual Studio automaticamente quando si verifica un'eccezione o un arresto anomalo del sistema in un'applicazione eseguita esternamente a Visual Studio. In questo modo è possibile testare l'applicazione quando Visual Studio non è in esecuzione e avviare il debug con Visual Studio quando si verifica un problema.

Il debug Just-In-Time funziona per le app desktop di Windows. Non funziona per le app universali di Windows e non funziona per il codice gestito ospitato in un'applicazione nativa, ad esempio visualizzatori.

> [!TIP]
> Se si desidera semplicemente sapere come rispondere a Just-in-Time nella finestra di dialogo del debugger, vedere [in questo argomento](../debugger/just-in-time-debugging-in-visual-studio.md).

##  <a name="BKMK_Enabling"></a> Abilitare o disabilitare Just-In-Time il debug
È possibile abilitare o disabilitare il debug da Visual Studio Just-In-Time **strumenti > Opzioni** nella finestra di dialogo.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Per abilitare o disabilitare il debug JIT

1.  Aprire Visual Studio con privilegi di amministratore (pulsante destro del mouse e scegliere **Esegui come amministratore**).

    Abilitare o disabilitare Just-In-Time debug imposta una chiave del Registro di sistema e dei privilegi di amministratore potrebbero essere necessario modificare tale chiave.

2. Scegliere **Opzioni** dal menu **Strumenti**.

2.  Nel **le opzioni** finestra di dialogo espandere il **debug** nodo.

3.  Nel **Debugging** nodo, seleziona **Just-In-Time**.

    ![Abilitare o disabilitare il debug JIT](../debugger/media/dbg-jit-enable-or-disable.png "abilitare o disabilitare il debug JIT")

4.  Nel **Attiva debug JIT per questi tipi di codice** , selezionare o deselezionare i tipi di programma relativi: **gestito**, **Native**, o **Script**.

5.  Fare clic su **OK**.

    Se si Abilita Just-in-Time debugger, ma non visualizzato in un arresto anomalo dell'applicazione o un'eccezione, vedere [gli errori di debug Just-In-Time](#jit_errors).

Il debug JIT può comunque essere abilitato anche se Visual Studio non è più presente nel computer. Quando non è installato Visual Studio, è possibile disabilitare il debug da Visual Studio Just-In-Time **opzioni** nella finestra di dialogo. In questo caso, è possibile disabilitare il debug JIT modificando il Registro di sistema di Windows.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Per disabilitare il debug JIT modificando il Registro di sistema

1.  Nel **avviare** menu, cercare ed eseguire `regedit.exe`

2.  Nel **dell'Editor del Registro di sistema** finestra, individuare ed eliminare le voci del Registro di sistema seguenti:

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\DbgManagedDebugger

    ![Chiave del Registro di sistema JIT](../debugger/media/dbg-jit-registry.png "chiave del Registro di sistema JIT")

3.  Se il computer è in esecuzione un sistema operativo a 64 bit, eliminare anche le voci del Registro di sistema seguenti:

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger

4.  Fare attenzione a non eliminare o modificare altre chiavi del Registro di sistema.

5.  Chiudi il **dell'Editor del Registro di sistema** finestra.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Per attivare il debug JIT di Windows Form

1.  Per impostazione predefinita, le applicazioni Windows Forms dispongono di un gestore eccezioni di livello superiore che consente al programma di proseguire l'esecuzione quando è possibile un ripristino. Ad esempio, se l'applicazione Windows Form genera un'eccezione non gestita, verrà visualizzato una finestra di dialogo simile alla seguente:

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Per abilitare Just-In-Time il debug di un'applicazione Windows Forms, è necessario eseguire i passaggi aggiuntivi seguenti:

2.  Impostare il `jitDebugging` valore per `true` nel `system.windows.form` sezione Machine. config o  *\<nome applicazione >*. file exe. config:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3.  In un'applicazione Windows Form C++ è anche necessario impostare `DebuggableAttribute` in un file con estensione config o nel codice. Se esegue la compilazione con [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) e senza [/Og](/cpp/build/reference/og-global-optimizations), il compilatore imposta questo attributo per l'utente. Se si desidera eseguire il debug di una build di rilascio non ottimizzata, tuttavia, è necessario procedere alla configurazione. A tale scopo, è possibile aggiungere la riga seguente al file AssemblyInfo.cpp dell'applicazione:

    ```cpp
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Per altre informazioni, vedere <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Usare il debug Just-In-Time
 Questa sezione illustra cosa accade quando un file eseguibile genera un'eccezione.

 È necessario disporre di Visual Studio è installato per eseguire la procedura seguente. Se non hai Visual Studio, è possibile scaricare la versione gratuita [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

 Assicurarsi che tale Just-In-Time di debug viene [abilitato](#BKMK_Enabling).

 Ai fini di questa sezione, ci assicureremo un'app console c# in Visual Studio che genera una [NullReferenceException](/dotnet/api/system.nullreferenceexception).

 In Visual Studio, creare un'app console c# (**File > Nuovo > progetto > Visual c# > applicazione Console**) denominata **ThrowsNullException**. Per altre informazioni sulla creazione di progetti in Visual Studio, vedere [procedura dettagliata: creare una semplice applicazione](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Quando si apre il progetto in Visual Studio, aprire il file Program.cs. Sostituire il metodo Main () con il codice seguente, che stampa una riga nella console e quindi genera un'eccezione NullReferenceException:

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
>  Affinché questa procedura per lavorare in un [configurazione di rilascio](../debugger/how-to-set-debug-and-release-configurations.md), è necessario disattivare [Just My Code](../debugger/just-my-code.md). In Visual Studio, fare clic su **strumenti > Opzioni**. Nel **le opzioni** finestra di dialogo, seleziona **debug**. Rimuovere il segno di spunta dalla **Abilita Just My Code**.

 Compilare la soluzione (in Visual Studio, scegliere **compilazione > Ricompila soluzione**). È possibile scegliere il Debug o la configurazione di rilascio (Scegli **Debug** per l'esperienza di debug completa). Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).

 Il processo di compilazione crea un ThrowsNullException.exe eseguibile. È possibile trovarlo nella cartella in cui la creazione del progetto c#: **...\ThrowsNullException\ThrowsNullException\bin\Debug** oppure **...\ThrowsNullException\ThrowsNullException\bin\Release**.

 Fare doppio clic il ThrowsNullException.exe. Si dovrebbe essere una finestra di comando simile al seguente:

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 Dopo alcuni secondi, viene visualizzata una finestra di errore:

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 Non fare clic **annullare**! Dopo alcuni secondi, verranno visualizzati due pulsanti, **Debug** e **Chiudi programma**. Fare clic su **Debug**.

> [!CAUTION]
>  Se l'applicazione contiene codice non attendibile, viene visualizzata una finestra di dialogo con un avviso di sicurezza. Questa finestra di dialogo consente di decidere se procedere o meno con il debug. Prima di continuare con il debug, decidere se ritenere attendibile o meno il codice. Se il codice è stato scritto da altri, decidere se ritenere attendibile o meno l'autore. Se l'applicazione è in esecuzione in un computer remoto, assicurarsi di riconoscere il nome del processo. Anche se l'applicazione è in esecuzione in un computer locale, non significa che possa essere ritenuta attendibile. Prendere in considerazione la possibilità di codice dannoso in esecuzione nel computer. Se si decide che il codice si sta per il debug è attendibile, fare clic su **Debug**. In caso contrario, fare clic su **non eseguire il Debug**.

 Il **Debugger JIT di Visual Studio** verrà visualizzata la finestra:

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 Sotto **debugger disponibili**, si noterà che il **nuova istanza di Microsoft Visual Studio <available version>**  riga è selezionata. Se si non è già selezionato, selezionarla.

 Nella parte inferiore della finestra, sotto **si desidera eseguire il debug usando il debugger selezionato?**, fare clic su **Yes**.

 Il progetto ThrowsNullException viene aperto in una nuova istanza di Visual Studio, con esecuzione interrotta alla riga che genera l'eccezione:

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 È possibile avviare il debug a questo punto. Se si trattasse di un'applicazione reale, è necessario scoprire il motivo per cui il codice che genera l'eccezione.

## <a name="jit_errors"></a> Errori di debug Just-In-Time
 Se non viene visualizzata la finestra di dialogo quando il programma di arresto anomalo ed è necessario abilitare la funzionalità, ciò potrebbe verificarsi a causa delle impostazioni di segnalazione errori Windows nel computer. Assicurarsi di aggiungere un **disabilitato** valore alle chiavi del Registro di sistema seguente e impostare il valore su 1:

* Segnalazione errori HKLM\Software\Microsoft\Windows\Windows
* Segnalazione errori HKLM\Software\WOW6432Node\Microsoft\Windows\Windows
 
Per altre informazioni su queste impostazioni, vedere [. Le impostazioni di segnalazione errori Windows](https://docs.microsoft.com/windows/desktop/wer/wer-settings).

Inoltre, si potrebbero visualizzare messaggi di errore seguenti che sono associati a Just-In-Time di debug.

- **Impossibile connettersi al processo bloccato. Il programma specificato non è un programma Windows o MS-DOS.**

    Questo errore si verifica quando si prova a connettersi a un processo in esecuzione come utente diverso.

    Per risolvere questo problema, avviare Visual Studio, aprire il **Connetti a processo** dalla finestra di dialogo il **Debug** menu e trovare il processo che si desidera eseguire il debug nel **processi disponibili**elenco. Se non si conosce il nome del processo, esaminare i **Debugger JIT di Visual Studio** finestra di dialogo e annotare l'ID del processo. Selezionare il processo nel **processi disponibili** elenco e fare clic su **Attach**. Nel **Debugger JIT di Visual Studio** finestra di dialogo, fare clic su **No** per chiudere la finestra di dialogo.

- **È stato possibile avviare il debugger perché nessun utente è connesso.**

    Questo errore si verifica quando il debug JIT tenta di avviare Visual Studio in un computer in cui nessun utente è connesso alla console. Poiché nessun utente è connesso, non esiste una sessione utente nella quale visualizzare la finestra di dialogo del debug JIT.

    Per correggere questo problema, connettersi al computer.

- **Classe non registrata.**

    Questo errore indica che il debugger ha tentato di creare una classe COM non registrata, probabilmente a causa di un problema di installazione.

    Per risolvere questo problema, usare il disco di installazione per reinstallare o riparare l'installazione di Visual Studio.

## <a name="see-also"></a>Vedere anche
 [Sicurezza del debugger](../debugger/debugger-security.md) [nozioni fondamentali di debug](../debugger/getting-started-with-the-debugger.md) [Just-In-Time, debug, finestra di dialogo Opzioni](../debugger/just-in-time-debugging-options-dialog-box.md) [avviso di sicurezza: connessione a un processo appartenente a un utente non attendibile può essere pericolosi. Se le informazioni seguenti sono sospette o non si è certi della loro provenienza e del loro stato, non connettersi al processo.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
