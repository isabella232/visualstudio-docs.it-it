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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690604"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Debug JIT in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debug Just-In-Time avvia Visual Studio automaticamente quando si verifica un'eccezione o un arresto anomalo del sistema in un'applicazione eseguita esternamente a Visual Studio. In questo modo è possibile testare l'applicazione quando Visual Studio non è in esecuzione e avviare il debug con Visual Studio quando si verifica un problema.

Il debug Just-In-Time funziona per le app desktop di Windows. Non funziona per le app universali di Windows e non funziona per il codice gestito ospitato in un'applicazione nativa, ad esempio visualizzatori.

## <a name="BKMK_Scenario"></a> Non è stato Just-in-Time del debugger, finestra di dialogo visualizzata quando si tenta di eseguire un'app?

L'attività da eseguire quando viene visualizzato il Visual Studio Just-in-Time nella finestra di dialogo debugger dipendono da ciò che si sta tentando di eseguire:

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>Se si desidera eliminare la finestra di dialogo e solo esegue normalmente l'app

1. (Per utenti esperti) Se si è installato Visual Studio (o è stato installato in precedenza e rimosso), [Just-in-Time di disabilitare il debug](#BKMK_Enabling) e provare a eseguire nuovamente l'app.

2. Se si esegue un'app web in Internet Explorer, disabilitare il debug degli script.

    Disabilita debug degli script nella finestra di dialogo Opzioni Internet. È possibile accedere con l'impostazione corrente di **Pannello di controllo** / **rete e Internet** / **Opzioni Internet** (i passaggi esatti dipendono dalla versione di Windows e Internet Explorer).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. Riaprire la pagina web in cui è stato trovato l'errore. Se non viene risolto il problema, contattare il proprietario dell'app web per risolvere il problema.

4. Se si esegue un altro tipo di app di Windows, è necessario contattare il proprietario dell'app per correggere l'errore e quindi reinstallare la versione corretta dell'app.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>Se si desidera risolvere o eseguire il debug dell'errore (utenti esperti)

- È necessario disporre [installato Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) per visualizzare le informazioni dettagliate sull'errore e provare a eseguirne il debug. Visualizzare [tramite JIT](#BKMK_Using_JIT) per istruzioni dettagliate. Se è Impossibile risolvere l'errore e correggere l'app, contattare il proprietario dell'app per risolvere l'errore.

## <a name="BKMK_Enabling"></a> Abilitare o disabilitare Just-In-Time il debug
 È possibile abilitare o disabilitare il debug da Visual Studio Just-In-Time **Strumenti / opzioni** nella finestra di dialogo.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Per abilitare o disabilitare il debug JIT

1. Aprire Visual Studio. Scegliere **Opzioni** dal menu **Strumenti**.

2. Nel **le opzioni** finestra di dialogo, seleziona la **debug** cartella.

3. Nel **Debugging** cartella, selezionare la **Just-In-Time** pagina.

4. Nel **Attiva debug JIT per questi tipi di codice** selezionare o deselezionare i tipi di programma relativi: **Managed**, **nativo**, o **Script**.

    Per disabilitare il debug JIT, è necessario disporre dei privilegi di amministratore. L'attivazione del debug JIT richiede la modifica di una chiave del Registro di sistema e per eseguire tale operazione sono necessari i privilegi di amministratore.

5. Fare clic su **OK**.

   Il debug JIT può comunque essere abilitato anche se Visual Studio non è più presente nel computer. Quando non è installato Visual Studio, è possibile disabilitare il debug da Visual Studio Just-In-Time **opzioni** nella finestra di dialogo. In questo caso, è possibile disabilitare il debug JIT modificando il Registro di sistema di Windows.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Per disabilitare il debug JIT modificando il Registro di sistema

1. Nel **avviare** menu, cercare ed eseguire `regedit.exe`

2. Nel **dell'Editor del Registro di sistema** finestra, individuare ed eliminare le voci del Registro di sistema seguenti:

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger

3. Se il computer è in esecuzione un sistema operativo a 64 bit, eliminare anche le voci del Registro di sistema seguenti:

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger

4. Fare attenzione a non eliminare o modificare altre chiavi del Registro di sistema.

5. Chiudi il **dell'Editor del Registro di sistema** finestra.

> [!NOTE]
> Se si sta tentando di disabilitare il debug per un'app sul lato server Just-In-Time e questi passaggi non consentono di risolvere il problema, disattivare il debug sul lato server nelle impostazioni dell'applicazione IIS e riprovare.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Per attivare il debug JIT di Windows Form

1. Per impostazione predefinita, le applicazioni Windows Forms dispongono di un gestore eccezioni di livello superiore che consente al programma di proseguire l'esecuzione quando è possibile un ripristino. Ad esempio, se l'applicazione Windows Form genera un'eccezione non gestita, verrà visualizzato una finestra di dialogo simile alla seguente:

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Per abilitare Just-In-Time il debug di un'applicazione Windows Forms, è necessario eseguire i passaggi aggiuntivi seguenti:

2. Impostare il `jitDebugging` valore per `true` nel `system.windows.form` sezione Machine. config o  *\<nome applicazione >* . file exe. config:

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

## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Usare il debug Just-In-Time
 Questa sezione illustra cosa accade quando un file eseguibile genera un'eccezione.

 È necessario disporre di Visual Studio è installato per eseguire la procedura seguente. Se non hai Visual Studio, è possibile scaricare la versione gratuita [Visual Studio 2015 Community Edition](https://visualstudio.microsoft.com/vs/older-downloads/).

 Quando si installa Visual Studio, il debug JIT è abilitato per impostazione predefinita.

 Ai fini di questa sezione, ci assicureremo un'app console c# in Visual Studio che genera un <xref:System.NullReferenceException>.

 In Visual Studio, creare un'app console c# (**File / nuovo / progetto / Visual c# / applicazione Console**) denominata **ThrowsNullException**. Per altre informazioni sulla creazione di progetti in Visual Studio, vedere [procedura dettagliata: Creare una semplice applicazione](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Quando si apre il progetto in Visual Studio, aprire il file Program.cs. Sostituire il metodo Main () con il codice seguente, che stampa una riga nella console e quindi genera un'eccezione NullReferenceException:

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
> Affinché questa procedura per lavorare in un [configurazione di rilascio](../debugger/how-to-set-debug-and-release-configurations.md), è necessario disattivare [Just My Code](../debugger/just-my-code.md). In Visual Studio, fare clic su **Strumenti / opzioni**. Nel **le opzioni** finestra di dialogo, seleziona **debug**. Rimuovere il segno di spunta dalla **Abilita Just My Code**.

 Compilare la soluzione (in Visual Studio, scegliere **Build / Ricompila soluzione**). È possibile scegliere il Debug o la configurazione di rilascio. Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).

 Il processo di compilazione crea un ThrowsNullException.exe eseguibile. È possibile trovarlo nella cartella in cui la creazione del progetto c#: **...\ThrowsNullException\ThrowsNullException\bin\Debug** oppure **...\ThrowsNullException\ThrowsNullException\bin\Release**.

 Fare doppio clic il ThrowsNullException.exe. Si dovrebbe essere una finestra di comando simile al seguente:

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 Dopo alcuni secondi, viene visualizzata una finestra di errore:

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 Non fare clic **annullare**! Dopo alcuni secondi, verranno visualizzati due pulsanti, **Debug** e **Chiudi programma**. Fare clic su **Debug**.

> [!CAUTION]
> Se l'applicazione contiene codice non attendibile, viene visualizzata una finestra di dialogo con un avviso di sicurezza. Questa finestra di dialogo consente di decidere se procedere o meno con il debug. Prima di continuare con il debug, decidere se ritenere attendibile o meno il codice. Se il codice è stato scritto da altri, decidere se ritenere attendibile o meno l'autore. Se l'applicazione è in esecuzione in un computer remoto, assicurarsi di riconoscere il nome del processo. Anche se l'applicazione è in esecuzione in un computer locale, non significa che possa essere ritenuta attendibile. Prendere in considerazione la possibilità di codice dannoso in esecuzione nel computer. Se si decide che il codice si sta per il debug è attendibile, fare clic su **Debug**. In caso contrario, fare clic su **non eseguire il Debug**.

 Il **Debugger JIT di Visual Studio** verrà visualizzata la finestra:

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 Sotto **debugger disponibili**, si noterà che il **nuova istanza di Microsoft Visual Studio 2015** riga è selezionata. Se si non è già selezionato, selezionarla.

 Nella parte inferiore della finestra, sotto **si desidera eseguire il debug usando il debugger selezionato?** , fare clic su **Yes**.

 Il progetto ThrowsNullException viene aperto in una nuova istanza di Visual Studio, con esecuzione interrotta alla riga che genera l'eccezione:

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 È possibile avviare il debug a questo punto. Se si trattasse di un'applicazione reale, è necessario scoprire il motivo per cui il codice che genera l'eccezione.

## <a name="just-in-time-debugging-errors"></a>Errori del debug JIT
 Se non viene visualizzata la finestra di dialogo quando il programma si blocca, questo potrebbe verificarsi a causa delle impostazioni di segnalazione errori Windows nel computer. Per altre informazioni, vedere [. Le impostazioni di segnalazione errori Windows](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).

 I messaggi di errore elencati di seguito sono associati al debug JIT.

- **Impossibile connettersi al processo bloccato. Il programma specificato non è un programma Windows o MS-DOS.**

     Questo errore si verifica quando si prova a connettersi a un processo in esecuzione come utente diverso.

     Per risolvere questo problema, avviare Visual Studio, aprire il **Connetti a processo** dalla finestra di dialogo il **Debug** menu e trovare il processo che si desidera eseguire il debug nel **processi disponibili**elenco. Se non si conosce il nome del processo, esaminare i **Debugger JIT di Visual Studio** finestra di dialogo e annotare l'ID del processo. Selezionare il processo nel **processi disponibili** elenco e fare clic su **Attach**. Nel **Debugger JIT di Visual Studio** finestra di dialogo, fare clic su **No** per chiudere la finestra di dialogo.

- **Impossibile avviare il debugger perché nessun utente è connesso.**

     Questo errore si verifica quando il debug JIT tenta di avviare Visual Studio in un computer in cui nessun utente è connesso alla console. Poiché nessun utente è connesso, non esiste una sessione utente nella quale visualizzare la finestra di dialogo del debug JIT.

     Per correggere questo problema, connettersi al computer.

- **Classe non registrata.**

     Questo errore indica che il debugger ha tentato di creare una classe COM non registrata, probabilmente a causa di un problema di installazione.

     Per risolvere questo problema, usare il disco di installazione per reinstallare o riparare l'installazione di Visual Studio.

## <a name="see-also"></a>Vedere anche
 [Sicurezza del debugger](../debugger/debugger-security.md) [nozioni di base del Debugger](../debugger/debugger-basics.md) [Just-In-Time, debug, finestra di dialogo Opzioni](../debugger/just-in-time-debugging-options-dialog-box.md) [avviso di sicurezza: La connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti sono sospette o non si è certi della loro provenienza e del loro stato, non connettersi al processo.](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)
