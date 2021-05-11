---
title: Eseguire il debug usando il debugger JUST-In-Time | Microsoft Docs
description: Eseguire il debug usando il debugger JUST-In-Time in Visual Studio. Il debug JIT può essere avviato automaticamente Visual Studio quando si verificano errori o arresti anomali di un'app.
ms.custom: SEO-VS-2020
ms.date: 09/24/2018
ms.topic: how-to
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3bdd35056706491ace6e5e6b2f7c3f6a45464d2e
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729247"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Eseguire il debug usando il debugger JUST-In-Time in Visual Studio

Il debug JIT può essere avviato automaticamente Visual Studio quando un'app in esecuzione all'esterno di Visual Studio o si arresta in modo anomalo. Con il debug JIT, è possibile testare le app all'esterno di Visual Studio e aprire Visual Studio per avviare il debug quando si verifica un problema.

Il debug JIT funziona per le app desktop di Windows. Non funziona per le app di Windows universali o per il codice gestito ospitato in un'applicazione nativa, ad esempio i visualizzatori.

> [!TIP]
> Se si vuole semplicemente arrestare la visualizzazione della finestra di dialogo Debugger JUST-In-Time, ma non è installato Visual Studio, vedere Disabilitare il debugger [JUST-In-Time.](../debugger/just-in-time-debugging-in-visual-studio.md) Se è stato installato Visual Studio, potrebbe essere necessario disabilitare il debug [JIT dal Registro di sistema di Windows.](#disable-just-in-time-debugging-from-the-windows-registry)

## <a name="enable-or-disable-just-in-time-debugging-in-visual-studio"></a><a name="BKMK_Enabling"></a> Abilitare o disabilitare il debug JIT in Visual Studio

>[!NOTE]
>Per abilitare o disabilitare il debug JIT, è necessario eseguire Visual Studio come amministratore. L'abilitazione o la disabilitazione del debug JIT imposta una chiave del Registro di sistema e potrebbero essere necessari privilegi di amministratore per modificare tale chiave. Per aprire la Visual Studio come amministratore, fare clic con il pulsante destro del mouse sull'app Visual Studio e **scegliere Esegui come amministratore.**

È possibile configurare il debug JIT dalla finestra di dialogo Visual Studio **Strumenti** di sviluppo (o Opzioni  >     >  **di** debug).

**Per abilitare o disabilitare il debug JIT:**

1. Scegliere **Opzioni debug** **JIT** dal menu   >    >  **Strumenti o Debug**.

   ![Abilitare o disabilitare il debug JIT](../debugger/media/dbg-jit-enable-or-disable.png "Abilitare o disabilitare il debug JIT")

1. Nella casella Abilita debug **JIT** per questi tipi di codice selezionare i tipi di codice di cui eseguire il debug **JIT:** Gestito **,** Nativo e/o **Script**.

1. Selezionare **OK**.

Se si abilita il debugger JIT, ma non si apre quando un'app si arresta in modo anomalo o si verifica un errore, vedere Risolvere i problemi relativi al [debug JIT.](#jit_errors)

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Disabilitare il debug JIT dal Registro di sistema di Windows

Il debug JIT può comunque essere abilitato anche se Visual Studio non è più presente nel computer. Se Visual Studio non è più installato, è possibile disabilitare il debug JIT modificando il Registro di sistema di Windows.

**Per disabilitare il debug JIT modificando il Registro di sistema:**

1. Dal menu **Start di** Windows eseguire l'editor del **Registro** di sistema (*regedit.exe*).

2. Nella finestra **Editor del Registro di** sistema individuare ed eliminare le voci del Registro di sistema seguenti:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![Chiave del Registro di sistema JIT](../debugger/media/dbg-jit-registry.png "Chiave del Registro di sistema JIT")

3. Se il computer esegue un sistema operativo a 64 bit, eliminare anche le voci del Registro di sistema seguenti:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    Assicurarsi di non eliminare o modificare altre chiavi del Registro di sistema.

5. Chiudere la finestra **Editor del Registro di sistema**.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Abilitare il debug JIT di un Windows Form

Per impostazione predefinita, le app Windows Form dispongono di un gestore eccezioni di primo livello che consente all'app di continuare a essere eseguita se è in grado di eseguire il ripristino. Se un Windows Forms app genera un'eccezione non gestita, viene visualizzata la finestra di dialogo seguente:

![Eccezione non gestita di Windows Form](../debugger/media/windowsformsunhandledexception.png "Eccezione non gestita di Windows Form")

Per abilitare il debug JIT anziché la gestione standard degli errori di Windows Form, aggiungere queste impostazioni:

- Nella sezione `system.windows.forms` del file *machine.config* *\<app name> o.exe.config* impostare il valore su `jitDebugging` `true` :

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- In un'applicazione Windows Form C++ impostare `DebuggableAttribute` anche su in un file con estensione `true` *config* o nel codice. Se si esegue la compilazione con [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) e senza [/Og](/cpp/build/reference/og-global-optimizations), il compilatore imposta automaticamente questo attributo. Se tuttavia si vuole eseguire il debug di una build di versione non ottimizzata, è necessario impostare aggiungendo la riga seguente nel `DebuggableAttribute` file *AssemblyInfo.cpp* dell'app:

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   Per altre informazioni, vedere <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="use-just-in-time-debugging"></a><a name="BKMK_Using_JIT"></a>Usare il debug JIT
Questo esempio illustra il debug JIT quando un'app genera un errore.

- È necessario aver installato Visual Studio per seguire questa procedura. Se non si dispone di Visual Studio, è possibile scaricare la versione [Visual Studio Community Edition.](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)

- Assicurarsi che il debug JIT sia abilitato [in](#BKMK_Enabling) **Strumenti**  >  **Opzioni**  >  **Debug**  >  **JIT.**

Per questo esempio si crea un'app console C# in Visual Studio genera [un'eccezione NullReferenceException.](/dotnet/api/system.nullreferenceexception)

1. In Visual Studio creare un'app console C# (**File**  >  **New**  >  **Project**  >  **Visual C#** Console  >  **Application**) denominata *ThrowsNullException*. Per altre informazioni sulla creazione di progetti in Visual Studio, vedere [Procedura dettagliata: Creare un'applicazione semplice.](../get-started/csharp/tutorial-wpf.md)

1. Quando il progetto viene aperto in Visual Studio, aprire il file *Program.cs.* Sostituire il metodo Main() con il codice seguente, che stampa una riga nella console e quindi genera un'eccezione NullReferenceException:

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. Per compilare la soluzione, scegliere la **configurazione Debug** (impostazione predefinita) **o** Versione e quindi selezionare **Compila**  >  **ricompila soluzione.**

   > [!NOTE]
   > - Scegliere **Configurazione di** debug per l'esperienza di debug completa.
   > - Se si seleziona Release configuration [(Configurazione](../debugger/how-to-set-debug-and-release-configurations.md) versione), è necessario [disattivare Just My Code](../debugger/just-my-code.md) per il funzionamento di questa procedura. In **Strumenti**  >  **Opzioni**  >  **debug** deselezionare **Abilita Just My Code**.

   Per altre informazioni sulle configurazioni della build, vedere Informazioni [sulle configurazioni della build.](../ide/understanding-build-configurations.md)

1. Aprire l'app *ThrowsNullException.exe* nella cartella del progetto C# (*...\ThrowsNullException\ThrowsNullException\bin\Debug* o *...\ThrowsNullException\ThrowsNullException\bin\Release*).

   Verrà visualizzata la finestra di comando seguente:

   ![Screenshot della console per ThrowsNullException.exe, che genera un'eccezione di riferimento Null non gestita (System.NullReferenceException).](../debugger/media/throwsnullexceptionconsole.png)

1. Verrà visualizzata la finestra di dialogo Choose **Just-In-Time Debugger (Scegli debugger JUST-In-Time).**

   ![Screenshot della finestra di dialogo Scegli debugger JUST-In-Time, che viene visualizzata dopo l'eccezione nella ThrowsNullException.exe della console.](../debugger/media/justintimedialog.png)

   In **Debugger disponibili** selezionare Nuova istanza **di \<your preferred Visual Studio version/edition>**, se non è già selezionata.

1. Selezionare **OK**.

   Il progetto ThrowsNullException viene aperto in una nuova istanza di Visual Studio, con l'esecuzione arrestata nella riga che ha generato l'eccezione:

   ![Screenshot del progetto ThrowsNullException in Visual Studio, con l'evidenziazione della riga di codice sorgente che ha generato l'eccezione.](../debugger/media/nullreferencesecondinstance.png)

A questo punto è possibile avviare il debug. Se si esegue il debug di un'app reale, è necessario scoprire perché il codice genera l'eccezione.

> [!CAUTION]
> Se l'app contiene codice non attendibile, viene visualizzata una finestra di dialogo di avviso di sicurezza che consente di decidere se procedere con il debug. Prima di continuare il debug, decidere se si considera attendibile il codice. Se il codice è stato scritto da altri, Se l'applicazione è in esecuzione in un computer remoto, assicurarsi di riconoscere il nome del processo. Se l'app è in esecuzione in locale, considerare la possibilità che nel computer sia in esecuzione codice dannoso. Se si decide che il codice è attendibile, selezionare **OK.** In caso contrario, selezionare **Annulla**.

## <a name="troubleshoot-just-in-time-debugging"></a><a name="jit_errors"></a> Risolvere i problemi di debug JIT

Se il debug JIT non viene avviato quando un'app si arresta in modo anomalo, anche se è abilitata in Visual Studio:

- Segnalazione errori Windows potrebbe assumere la gestione degli errori nel computer.

  Per risolvere questo problema, usare l'editor del Registro di sistema per aggiungere un valore **DWORD** **disabilitato,** con dati **valore** **1,** alle chiavi del Registro di sistema seguenti:

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows Error Reporting**

  - (Per i computer a 64 bit): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows Error Reporting**

  Per altre informazioni, vedere [. Impostazioni di WeR](/windows/desktop/wer/wer-settings).

- Un problema noto di Windows potrebbe causare l'esito negativo del debugger JUST-In-Time.

  La correzione è l'aggiunta di **un valore DWORD** **auto**, con dati **valore** **1,** alle chiavi del Registro di sistema seguenti:

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (Per i computer a 64 bit): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Durante il debug JIT potrebbero essere visualizzati i messaggi di errore seguenti:

- **Impossibile connettersi al processo che si arresta in modo anomalo. Il programma specificato non è un programma Windows o MS-DOS.**

    Il debugger ha tentato di connettersi a un processo in esecuzione con un altro utente.

    Per risolvere questo problema, in Visual Studio aprire Debug Attach to Process (Esegui debug connessione a processo) o premere CTRL ALT P ) e trovare il processo di cui si vuole eseguire il  >   debug   +    +   **nell'elenco Processi** disponibili . Se non si conosce il nome del processo, trovare l'ID processo nella finestra di dialogo Visual Studio debugger **JUST-In-Time.** Selezionare il processo **nell'elenco Processi disponibili** e selezionare **Collega.** Selezionare **No per** chiudere la finestra di dialogo del debugger JUST-In-Time.

- **Impossibile avviare il debugger perché nessun utente è connesso.**

    Non è presente alcun utente connesso alla console, quindi non esiste alcuna sessione utente per visualizzare la finestra di dialogo di debug JIT.

    Per correggere questo problema, connettersi al computer.

- **Classe non registrata.**

    Il debugger ha tentato di creare una classe COM non registrata, probabilmente a causa di un problema di installazione.

    Per risolvere il problema, usare il Programma di installazione di Visual Studio per reinstallare o ripristinare l Visual Studio installazione.

## <a name="see-also"></a>Vedi anche

- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Opzioni, Debug, finestra di dialogo JIT](../debugger/just-in-time-debugging-options-dialog-box.md)
- [Avviso di sicurezza: può essere pericoloso connettersi a un processo appartenente a un account utente non attendibile. Se le seguenti sottostanti risultano sospette o non sicure, non stabilire la connessione al processo.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
