---
title: Risoluzione dei problemi e problemi noti (Visual Studio Tools per Unity) | Microsoft Docs
ms.custom: ''
ms.date: 04/10/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: cb1da2ec2c41fcbec78864868d116bcd1684a5b2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Risoluzione dei problemi e problemi noti (Visual Studio Tools per Unity)
In questa sezione verranno illustrate le soluzioni a problemi comuni relativi a Visual Studio Tools per Unity. Oltre alla descrizione dei problemi noti, verrà spiegato come contribuire al miglioramento di Visual Studio Tools per Unity segnalando gli errori.

## <a name="troubleshooting"></a>Risoluzione dei problemi
Per risolvere alcuni problemi comuni relativi a Visual Studio Tools per Unity, vedere le sezioni seguenti.

### <a name="visual-studio-crashes"></a>Visual Studio si arresta in modo anomalo
Questo problema può essere dovuto al danneggiamento della cache MEF di Visual Studio.

Rimuovere la cartella seguente per reimpostare la cache MEF. Prima di eseguire questa operazione, chiudere Visual Studio:

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Questo dovrebbe risolvere il problema. Nel caso in cui il problema si verifichi ancora, eseguire un prompt dei comandi per gli sviluppatori per Visual Studio come amministratore e usare il comando seguente:

```batch
 devenv /setup
```

### <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Problemi con Visual Studio 2015 e IntelliSense o con la colorazione del codice.
Eseguire l'aggiornamento a Visual Studio 2015 Update 3.

### <a name="shader-files-without-code-coloration-when-using-visual-studio-2017"></a>File di shader senza colorazione del codice quando si usa Visual Studio 2017
Verificare che il carico di lavoro "Sviluppo di applicazioni desktop con C++" sia installato nell'istanza di Visual Studio 2017. Il parser C/C++ usato per la colorazione del codice è aggregato in questo carico di lavoro.

### <a name="visual-studio-hangs"></a>Visual Studio si blocca
Alcuni plug-in Unity come Parse, FMOD, UMP (Universal Media Player), ZFBrowser o Embedded Browser usano thread nativi. Il problema si verifica quando un plug-in tenta di collegare un thread nativo al runtime, causando il blocco delle chiamate al sistema operativo. Ciò significa che Unity non può interrompere il thread per il debugger, o per ricaricare il dominio, e si blocca.

Per FMOD, è disponibile una soluzione alternativa che consiste nel passare il [flag](https://www.fmod.org/docs/content/generated/FMOD_STUDIO_INITFLAGS.html) di inizializzazione FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE per disabilitare l'elaborazione asincrona ed eseguire tutte le elaborazioni nel thread principale.

### <a name="incompatible-project-in-visual-studio"></a>Progetto incompatibile in Visual Studio
In primo luogo, verificare che Visual Studio sia impostato come editor di script esterno in Unity da Modifica/Preferenze/Strumenti esterni. Quindi verificare che il plug-in di Visual Studio sia installato in Unity controllando che in Informazioni su, nella parte in basso della pagina, venga visualizzato un messaggio che indica che Microsoft Visual Studio Tools per Unity è abilitato. Controllare che l'estensione sia installata correttamente in Visual Studio da Informazioni su.

### <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Ricarichi aggiuntivi o perdita di tutte le finestre aperte di Visual Studio
Verificare di non toccare mai i file di progetto direttamente da un processore di risorse o qualsiasi altro strumento. Se è necessario modificare il file di progetto, è disponibile un'API. Controllare la [sezione relativa ai problemi dei riferimenti degli assembly](#Assembly-reference-issues).

Se si verificano ricaricamenti aggiuntivi o se Visual Studio perde tutte le finestre aperte durante il ricaricamento, verificare di aver installato i .NET Targeting Pack appropriati. Per altre informazioni, controllare la sezione seguente sui framework.

###  <a name="the-debugger-does-not-break-on-exceptions"></a>Il debugger non si interrompe in caso di eccezioni
Quando si usa il runtime di Unity legacy (equivalente a .NET 3.5), il debugger si interrompe sempre quando un'eccezione non viene gestita (= all'esterno di un blocco try/catch). Se l'eccezione viene gestita, il debugger usa la finestra Impostazioni eccezioni per determinare se è necessaria o meno un'interruzione.

Con il nuovo runtime (equivalente a .NET 4.6), Unity ha introdotto un nuovo modo per gestire le eccezioni utente e, di conseguenza, tutte le eccezioni vengono interpretate come "gestite dall'utente", anche se si trovano all'esterno di un blocco try/catch. Ecco perché è ora necessario controllarle in modo esplicito nella finestra Impostazioni eccezioni se si vuole che il debugger si interrompa.

Nella finestra Impostazioni eccezioni (Debug > Windows > Impostazioni eccezioni) espandere il nodo per una categoria di eccezioni (ad esempio, eccezioni Common Language Runtime, vale a dire eccezioni .NET) e selezionare la casella di controllo per l'eccezione specifica all'interno di tale categoria (ad esempio System.NullReferenceException). È inoltre possibile selezionare un'intera categoria di eccezioni.

### <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>In Windows Visual Studio chiede di scaricare il framework di destinazione Unity
Visual Studio Tools per Unity richiede .NET Framework 3.5, che in Windows 8 o 10 non è installato per impostazione predefinita. Per risolvere questo problema, seguire le istruzioni per scaricare e installare .NET Framework 3.5.

Quando si usa il nuovo runtime di Unity, sono anche necessari .NET Targeting Pack versione 4.6 e 4.7.1. È possibile usare il programma di installazione di VS2017 per installarli rapidamente (modificare l'installazione di VS2017, i singoli componenti, la categoria .NET, selezionare tutti i Targeting Pack 4.x).

### <a name="assembly-reference-issues"></a>Problemi di riferimento all'assembly
Se il progetto si basa su riferimenti complessi o se si vuole controllare meglio questo passaggio di generazione, è possibile usare l'[API](../cross-platform/customize-project-files-created-by-vstu.md) di Visual Studio per la modifica del contenuto della soluzione o del progetto generati. È anche possibile usare [file di risposta](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) nel progetto Unity perché venga elaborato.

### <a name="breakpoints-with-a-warning"></a>Punti di interruzione con avviso
Se Visual Studio non riesce a trovare un percorso di origine per un punto di interruzione specifico, verrà visualizzato un avviso per il punto di interruzione. Verificare che il comportamento in uso sia caricato/usato correttamente nella scena Unity corrente.

### <a name="breakpoints-not-hit"></a>Mancato accesso ai punti di interruzione
Verificare che il comportamento in uso sia caricato/usato correttamente nella scena Unity corrente. Chiudere Visual Studio e Unity, eliminare tutti i file generati, con estensione csproj e sln, e l'intera cartella della raccolta.

### <a name="unable-to-attach"></a>Non è possibile connettersi
-   Provare a disabilitare temporaneamente il programma antivirus o a creare regole di esclusione per Visual Studio e Unity.
-   Provare a disattivare temporaneamente il firewall o a creare regole per consentire la connettività di rete TCP/UDP tra Visual Studio e Unity.
-   Alcuni programmi come Team Viewer interferiscono con il rilevamento del processo. È possibile provare a interrompere temporaneamente qualsiasi software aggiuntivo e verificare gli effetti.
-   Non rinominare il file eseguibile principale di Unity, perché Visual Studio Tools per Unity esegue il monitoraggio solo dei processi "Unity.exe".

### <a name="unable-to-debug-android-players"></a>Impossibile eseguire il debug dei lettori Android
Per il rilevamento dei lettori viene usato il multicast, che è il meccanismo predefinito usato da Unity, ma in seguito viene usata una connessione TCP normale per collegare il debugger. La fase di rilevamento è il problema principale per i dispositivi Android.

Il Wi-Fi è versatile ma è molto lento rispetto alla connessione USB a causa della latenza. Alcuni router o dispositivi non supportano il multicast: è il caso, ad esempio, della serie Nexus.

La connessione USB è ultra rapida per il debug e Visual Studio Tools per Unity è ora in grado di rilevare i dispositivi USB e comunicare con il server adb per inoltrare in modo appropriato le porte per il debug.

### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Migrazione da UnityVS a Visual Studio Tools per Unity
 Se si intende eseguire la migrazione da UnityVS a Visual Studio Tools per Unity, è necessario generare nuove soluzioni Visual Studio per i progetti Unity.

##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Per eseguire la migrazione del progetto Unity da UnityVS 1.8 a Visual Studio Tools per Unity 1.9

1.  Eliminare i vecchi file della soluzione e del progetto dal progetto Unity. Nella directory radice del progetto Unity individuare i file con estensione sln di Visual Studio e i file * proj, quindi eliminarli tutti.

2.  Importare il pacchetto di Visual Studio Tools per Unity nel progetto Unity. Per informazioni su come importare il pacchetto VSTU, vedere Configurare Visual Studio Tools per Unity nella pagina [Introduzione](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) .

3.  Generare i nuovi file della soluzione e del progetto. Per generarli subito, nel menu principale dell'editor di Unity scegliere **Visual Studio Tools**, **Generate Project Files**. In caso contrario, è possibile ignorare questo passaggio. Visual Studio Tools per Unity genererà i nuovi file automaticamente quando si sceglie **Visual Studio Tools**, **Open in Visual Studio**.

## <a name="known-issues"></a>Problemi noti
 In Visual Studio Tools per Unity sono presenti problemi noti derivanti dall'interazione tra il debugger e la versione precedente del compilatore C# inclusa in Unity. Microsoft sta lavorando per risolvere questi problemi, ma nel frattempo potrebbe verificarsi quanto segue:

-   Durante il debug si verifica talvolta un arresto anomalo di Unity.

-   Durante il debug si verifica talvolta un blocco di Unity.

-   Durante l'esecuzione o l'uscita da istruzioni o metodi vengono riscontrati comportamenti errati, in particolare negli iteratori o all'interno di istruzioni switch.

## <a name="reporting-errors"></a>Segnalazione di errori
 È possibile contribuire a migliorare la qualità di Visual Studio Tools per Unity inviando apposite segnalazioni quando si riscontrano arresti anomali, blocchi o errori di altro tipo. In questo modo Microsoft potrà esaminare e correggere i problemi relativi a Visual Studio Tools per Unity. Microsoft ringrazia per il contributo.

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Come segnalare un errore in caso di blocco di Visual Studio
 Sono stati segnalati alcuni casi di blocco di Visual Studio durante il debug con Visual Studio Tools per Unity, ma sono necessari maggiori dati per analizzare questo problema. Per contribuire alla risoluzione del problema, eseguire le operazioni descritte di seguito.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Per segnalare un blocco di Visual Studio durante il debug con Visual Studio Tools per Unity

*In Windows:*

1.  Aprire una nuova istanza di Visual Studio.

2.  Aprire la finestra di dialogo Connetti a processo. Nel menu principale della nuova istanza di Visual Studio scegliere **Debug**, **Connetti a processo**.

3.  Connettere il debugger all'istanza bloccata di Visual Studio. Nella finestra di dialogo **Connetti a processo** selezionare l'istanza bloccata di Visual Studio dalla tabella **Processi disponibili** e quindi fare clic sul pulsante **Connetti** .

4.  Sospendere l'esecuzione del debugger. Nel menu principale della nuova istanza di Visual Studio scegliere **Debug**, **Interrompi tutto** oppure premere **CTRL+ALT+INTERR**.

5.  Creare un dump del thread. Nella finestra Comando immettere il seguente comando e premere **INVIO**:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Potrebbe essere necessario rendere prima visibile la finestra **Comando** . Nel menu principale di Visual Studio scegliere **Visualizza**, **Altre finestre**, **Finestra di comando**.

*In Mac:*

1. Aprire un terminale e ottenere il PID di Visual Studio per Mac:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Avviare il debugger lldb:

    ```shell
    lldb
    ```

1. Collegarsi all'istanza di Visual Studio per Mac usando PID:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Recuperare l'analisi StackTrace per tutti i thread:

    ```shell
    bt all
    ```

Inviare infine il dump del thread all'indirizzo [vstusp@microsoft.com](mailto:vstusp@microsoft.com), insieme a una descrizione dell'operazione in corso quando si è verificato il blocco di Visual Studio.
