---
title: Debug JIT
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad2814dffa75809a318dc7cebe7831b5ecec7d29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690604"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Debug JIT in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debug JIT avvia Visual Studio automaticamente quando si verifica un'eccezione o un arresto anomalo in un'applicazione in esecuzione all'esterno di Visual Studio. In questo modo è possibile testare l'applicazione quando Visual Studio non è in esecuzione e avviare il debug con Visual Studio quando si verifica un problema.

Il debug JIT funziona per le applicazioni desktop di Windows. Non funziona per le app universali di Windows e non per il codice gestito ospitato in un'applicazione nativa, ad esempio i visualizzatori.

## <a name="did-the-just-in-time-debugger-dialog-box-appear-when-trying-to-run-an-app"></a><a name="BKMK_Scenario"></a> Quando si tenta di eseguire un'app, viene visualizzata la finestra di dialogo debugger JIT?

Le azioni da intraprendere quando viene visualizzata la finestra di dialogo debugger JIT di Visual Studio dipendono da ciò che si sta tentando di eseguire:

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>Se si vuole eliminare la finestra di dialogo ed eseguire l'app normalmente

1. (Utenti avanzati) Se Visual Studio è installato (oppure è stato installato in precedenza e rimosso), disabilitare il [debug](#BKMK_Enabling) JIT e provare a eseguire di nuovo l'app.

2. Se si esegue un'app Web in Internet Explorer, disabilitare il debug degli script.

    Disabilitare il debug degli script nella finestra di dialogo Opzioni Internet. È possibile accedere a questa opzione dalla rete del **Pannello di controllo**  /  **e**da Internet  /  **Internet Options** (la procedura esatta dipende dalla versione di Windows e da Internet Explorer).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. Aprire nuovamente la pagina Web in cui è stato rilevato l'errore. Se il problema persiste, contattare il proprietario dell'app Web per risolvere il problema.

4. Se si esegue un altro tipo di app di Windows, sarà necessario contattare il proprietario dell'app per correggere l'errore, quindi reinstallare la versione fissa dell'app.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>Se si vuole correggere o eseguire il debug dell'errore (utenti avanzati)

- Per visualizzare le informazioni dettagliate sull'errore e provare a eseguirne il debug, è necessario che [Visual Studio sia installato](https://visualstudio.microsoft.com/vs/older-downloads/) . Per istruzioni dettagliate, vedere [uso di JIT](#BKMK_Using_JIT) . Se non è possibile risolvere l'errore e correggere l'app, contattare il proprietario dell'app per risolvere l'errore.

## <a name="enable-or-disable-just-in-time-debugging"></a><a name="BKMK_Enabling"></a> Abilitare o disabilitare il debug JIT
 È possibile abilitare o disabilitare il debug JIT dalla finestra di dialogo **Strumenti/Opzioni** di Visual Studio.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Per abilitare o disabilitare il debug JIT

1. Aprire Visual Studio. Scegliere **Opzioni** dal menu **Strumenti**.

2. Nella finestra di dialogo **Opzioni** selezionare la cartella **debug** .

3. Nella cartella **debug** selezionare la pagina **just-in-Time** .

4. Nella casella **Abilita debug JIT di questi tipi di codice** selezionare o deselezionare i tipi di programma pertinenti: **gestito**, **nativo**o **script**.

    Per disabilitare il debug JIT, è necessario disporre dei privilegi di amministratore. L'attivazione del debug JIT richiede la modifica di una chiave del Registro di sistema e per eseguire tale operazione sono necessari i privilegi di amministratore.

5. Fare clic su **OK**.

   Il debug JIT può comunque essere abilitato anche se Visual Studio non è più presente nel computer. Quando Visual Studio non è installato, non è possibile disabilitare il debug JIT dalla finestra di dialogo **Opzioni** di Visual Studio. In questo caso, è possibile disabilitare il debug JIT modificando il Registro di sistema di Windows.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Per disabilitare il debug JIT modificando il Registro di sistema

1. Nel menu **Start** cercare ed eseguire `regedit.exe`

2. Nella finestra dell' **Editor del registro di sistema** individuare ed eliminare le voci del registro di sistema seguenti:

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger

3. Se nel computer è in esecuzione un sistema operativo a 64 bit, eliminare anche le seguenti voci del registro di sistema:

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger

4. Fare attenzione a non eliminare o modificare altre chiavi del Registro di sistema.

5. Chiudere la finestra **Editor del Registro di sistema**.

> [!NOTE]
> Se si sta tentando di disabilitare il debug JIT per un'app sul lato server e questi passaggi non consentono di risolvere il problema, disattivare il debug sul lato server nelle impostazioni dell'applicazione IIS e riprovare.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Per attivare il debug JIT di Windows Form

1. Per impostazione predefinita, le applicazioni Windows Forms dispongono di un gestore eccezioni di livello superiore che consente al programma di proseguire l'esecuzione quando è possibile un ripristino. Se, ad esempio, il Windows Forms Application genera un'eccezione non gestita, verrà visualizzata una finestra di dialogo simile alla seguente:

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Per abilitare il debug JIT di una Windows Forms Application, è necessario eseguire i passaggi aggiuntivi seguenti:

2. Impostare il `jitDebugging` valore su `true` nella `system.windows.form` sezione del file machine.config o *\<application name>*.exe.config:

    ```
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3. In un'applicazione Windows Form C++ è anche necessario impostare `DebuggableAttribute` in un file con estensione config o nel codice. Se si esegue la compilazione con [/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) e senza [/Og](https://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435), il compilatore imposta automaticamente questo attributo. Se si desidera eseguire il debug di una build di rilascio non ottimizzata, tuttavia, è necessario procedere alla configurazione. A tale scopo, è possibile aggiungere la riga seguente al file AssemblyInfo.cpp dell'applicazione:

    ```
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Per altre informazioni, vedere <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmk_using_jituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Usare il debug JIT
 In questa sezione viene illustrato cosa accade quando un eseguibile genera un'eccezione.

 Per eseguire questa procedura, è necessario che Visual Studio sia installato. Se non si dispone di Visual Studio, è possibile scaricare la [versione gratuita di Visual studio 2015 Community Edition](https://visualstudio.microsoft.com/vs/older-downloads/).

 Quando si installa Visual Studio, il debug JIT è abilitato per impostazione predefinita.

 Ai fini di questa sezione, si renderà un'app console C# in Visual Studio che genera un'eccezione <xref:System.NullReferenceException> .

 In Visual Studio creare un'app console C# (**file/nuovo/progetto/Visual c#/applicazione console**) denominata **ThrowsNullException**. Per ulteriori informazioni sulla creazione di progetti in Visual Studio, vedere [procedura dettagliata: creare un'applicazione semplice](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Quando si apre il progetto in Visual Studio, aprire il file Program.cs. Sostituire il metodo Main () con il codice seguente, che stampa una riga nella console e quindi genera un'eccezione NullReferenceException:

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
> Affinché questa procedura funzioni in una [configurazione di versione](../debugger/how-to-set-debug-and-release-configurations.md), è necessario disattivare [Just My Code](../debugger/just-my-code.md). In Visual Studio fare clic su **Strumenti/Opzioni**. Nella finestra di dialogo **Opzioni** selezionare **debug**. Rimuovere il segno di spunta da **Enable Just My Code**.

 Compilare la soluzione (in Visual Studio scegliere **Compila/Ricompila soluzione**). È possibile scegliere la configurazione di debug o di rilascio. Per ulteriori informazioni sulle configurazioni della build, vedere [informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).

 Il processo di compilazione crea un ThrowsNullException.exe eseguibile. È possibile trovarlo nella cartella in cui è stato creato il progetto C#: **. ..\ThrowsNullException\ThrowsNullException\bin\Debug** o **. ..\ThrowsNullException\ThrowsNullException\bin\Release**.

 Fare doppio clic sul ThrowsNullException.exe. Verrà visualizzata una finestra di comando simile alla seguente:

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 Dopo alcuni secondi, viene visualizzata una finestra di errore:

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 Non fare clic su **Annulla**. Dopo alcuni secondi, dovrebbero essere visualizzati due pulsanti, **debug** e **Chiudi programma**. Fare clic su **debug**.

> [!CAUTION]
> Se l'applicazione contiene codice non attendibile, viene visualizzata una finestra di dialogo con un avviso di sicurezza. Questa finestra di dialogo consente di decidere se procedere o meno con il debug. Prima di continuare con il debug, decidere se ritenere attendibile o meno il codice. Se il codice è stato scritto da altri, decidere se ritenere attendibile o meno l'autore. Se l'applicazione è in esecuzione in un computer remoto, assicurarsi di riconoscere il nome del processo. Anche se l'applicazione è in esecuzione in un computer locale, non significa che possa essere ritenuta attendibile. Prendere in considerazione la possibilità di esecuzione di codice dannoso nel computer. Se si decide che il codice di cui si sta per eseguire il debug è attendibile, fare clic su **debug**. In caso contrario, fare clic su **non eseguire il debug**.

 Viene visualizzata la finestra **debugger JIT di Visual Studio** :

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 Nei **debugger possibili**, si noterà che la **nuova istanza di Microsoft Visual Studio riga 2015** è selezionata. Se non è già selezionato, selezionarlo ora.

 Nella parte inferiore della finestra, in **si desidera eseguire il debug utilizzando il debugger selezionato?**, fare clic su **Sì**.

 Il progetto ThrowsNullException viene aperto in una nuova istanza di Visual Studio, con l'esecuzione arrestata alla riga che genera l'eccezione:

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 A questo punto è possibile avviare il debug. Se si trattasse di un'applicazione reale, è necessario individuare il motivo per cui il codice genera l'eccezione.

## <a name="just-in-time-debugging-errors"></a>Errori del debug JIT
 Se la finestra di dialogo non viene visualizzata quando il programma si arresta in modo anomalo, il problema potrebbe essere dovuto a Segnalazione errori Windows impostazioni del computer. Per ulteriori informazioni, vedere [. Impostazioni WER](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).

 I messaggi di errore elencati di seguito sono associati al debug JIT.

- **Impossibile connettersi al processo bloccato. Il programma specificato non è un programma Windows o MS-DOS.**

     Questo errore si verifica quando si tenta di connettersi a un processo in esecuzione con un altro utente.

     Per risolvere il problema, avviare Visual Studio, aprire la finestra di dialogo **Connetti a processo** dal menu **debug** e individuare il processo di cui si desidera eseguire il debug nell'elenco **processi disponibili** . Se non si conosce il nome del processo, esaminare la finestra di dialogo **debugger JIT di Visual Studio** e prendere nota dell'ID del processo. Selezionare il processo nell'elenco **processi disponibili** e fare clic su **Connetti**. Nella finestra di dialogo **debugger JIT di Visual Studio** fare clic su **No** per chiudere la finestra di dialogo.

- **Impossibile avviare il debugger perché nessun utente è connesso.**

     Questo errore si verifica quando il debug JIT tenta di avviare Visual Studio in un computer in cui nessun utente è connesso alla console. Poiché nessun utente è connesso, non esiste una sessione utente nella quale visualizzare la finestra di dialogo del debug JIT.

     Per correggere questo problema, connettersi al computer.

- **Classe non registrata.**

     Questo errore indica che il debugger ha tentato di creare una classe COM non registrata, probabilmente a causa di un problema di installazione.

     Per risolvere questo problema, usare il disco di installazione per reinstallare o riparare l'installazione di Visual Studio.

## <a name="see-also"></a>Vedere anche
 Debugger [sicurezza debugger](../debugger/debugger-security.md) [nozioni di base](../debugger/debugger-basics.md) [JIT, debug, finestra di dialogo Opzioni](../debugger/just-in-time-debugging-options-dialog-box.md) [avviso di sicurezza: la connessione a un processo di proprietà di un utente non attendibile può essere pericolosa. Se le informazioni seguenti sono sospette o non sono sicure, non connettersi a questo processo](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)
