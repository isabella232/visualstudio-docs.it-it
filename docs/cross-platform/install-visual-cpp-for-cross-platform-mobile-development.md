---
title: Installare Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma | Microsoft Docs
ms.custom: ''
ms.date: 05/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: c46644b18188475bd6389a795625209f74a7d9b5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021988"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>Installare Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma

È possibile usare C++ in Visual Studio per compilare app desktop di Windows, app UWP (Universal Windows Platform), app di Linux e ora anche app per Android e iOS. Il carico di lavoro **Sviluppo di applicazioni per dispositivi mobili con C++** è un set di componenti installabili in Visual Studio che include modelli di Visual Studio multipiattaforma per iOS, Android e UWP. Questo carico di lavoro installa gli SDK e gli strumenti multipiattaforma necessari per iniziare rapidamente, senza doverli individuare, scaricare e configurare manualmente. Con questi strumenti di Visual Studio è possibile creare, modificare, eseguire il debug e testare facilmente i progetti multipiattaforma. Questo argomento descrive come installare gli strumenti e il software di terze parti necessari per sviluppare app multipiattaforma in C++ mediante Visual Studio. Per una panoramica, vedere [Visual C++ per lo sviluppo di codice per dispositivi mobili multipiattaforma](https://go.microsoft.com/fwlink/p/?LinkId=536383)

## <a name="requirements"></a>Requisiti

- Per i requisiti di installazione, vedere [Requisiti di sistema per la famiglia di prodotti Visual Studio 2017](/visualstudio/productinfo/vs2017-system-requirements-vs).

   > [!IMPORTANT]
   > Se si usa Windows 7 o Windows Server 2008 R2, è possibile sviluppare codice per applicazioni desktop di Windows classiche, librerie e app Android NativeActivity, nonché librerie di codice e app per iOS, ma non app di Windows Phone o UWP.

Per compilare le app per specifiche piattaforme del dispositivo sono necessari alcuni requisiti aggiuntivi:

- Gli emulatori Windows Phone e l'emulatore di Microsoft Visual Studio per Android richiedono un computer in grado di eseguire Hyper-V. Per poter installare ed eseguire gli emulatori, è prima necessario abilitare la funzionalità Hyper-V in Windows. Per altre informazioni, vedere i [requisiti di sistema](system-requirements-for-the-visual-studio-emulator-for-android.md) dell'emulatore.

- Gli emulatori Android x86 inclusi in Android SDK offrono i risultati migliori nei computer in grado di eseguire il driver HAXM Intel. A questo scopo è necessario un processore Intel x64 con supporto di VT-x e della funzionalità del bit di disattivazione dell'esecuzione (XD, Execute Disable Bit). Per altre informazioni, vedere [Intel® Hardware Accelerated Execution Manager (Intel® HAXM)](https://go.microsoft.com/fwlink/p/?LinkId=536385).

- La compilazione di codice per iOS richiede un ID Apple, un account iOS Developer Program e un computer Mac in grado di eseguire [Xcode](https://go.microsoft.com/fwlink/p/?LinkId=536387) versione 6 o versioni successive su OS X Mavericks (versione 10.9) o versioni successive. Per un collegamento alla procedura di installazione, vedere [Installare gli strumenti per iOS](#install-tools-for-ios).

## <a name="get-the-tools"></a>Ottenere gli strumenti

Il carico di lavoro Sviluppo di applicazioni per dispositivi mobili con C++ è disponibile nelle edizioni Community, Professional ed Enterprise di Visual Studio. Per ottenere Visual Studio, passare alla pagina [Download di Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=517106). Gli strumenti di sviluppo per dispositivi mobili multipiattaforma sono disponibili a partire da Visual Studio 2015 Update 2 o versioni successive.

## <a name="install-the-tools"></a>Installare gli strumenti

Il programma di installazione di Visual Studio per Visual Studio 2017 include un carico di lavoro **Sviluppo di applicazioni per dispositivi mobili con C++** che installa gli strumenti, i modelli e i componenti del linguaggio C++ necessari per lo sviluppo per Android e iOS in Visual Studio. Vengono installati i set di strumenti GCC e Clang necessari per le compilazioni e il debug di Android e i componenti per comunicare con un Mac per lo sviluppo iOS. Vengono anche installati tutti gli strumenti e gli SDK di terze parti necessari per supportare lo sviluppo di app per iOS e Android. Molti di questi strumenti di terze parti sono software open source necessari per il supporto della piattaforma Android.

- Android Native Development Kit (NDK) è richiesto per compilare codice C++ per la piattaforma Android.

- Android SDK, Apache Ant e Java SE Development Kit sono richiesti per il processo di compilazione Android.

- L'emulatore Android di Google e Intel Hardware Accelerated Execution Manager sono componenti facoltativi, ma consigliati. È possibile sviluppare ed eseguire il debug direttamente in un dispositivo Android, ma risulta spesso più facile usare un emulatore sul desktop per il debug. Microsoft offre anche un emulatore di Visual Studio per Android che può essere installato separatamente.

#### <a name="to-install-the-mobile-development-with-c-workload-in-visual-studio-2017"></a>Per installare il carico di lavoro Sviluppo di applicazioni per dispositivi mobili con C++ in Visual Studio 2017

1. Eseguire il **programma di installazione di Visual Studio** dal menu **Start**.

1. Se è già stato installato Visual Studio, scegliere il pulsante **Modifica** per la versione installata di Visual Studio che si vuole modificare. In caso contrario, scegliere **Installa** per installare Visual Studio.

1. Con la scheda **Carichi di lavoro** selezionata, scorrere verso il basso e selezionare il carico di lavoro **Sviluppo di applicazioni per dispositivi mobili con C++** nel programma di installazione di Visual Studio. Quando questo carico di lavoro è selezionato, verranno selezionati anche altri componenti necessari per lo sviluppo C++. È anche possibile scegliere altri carichi di lavoro e singoli componenti da installare contemporaneamente. Per compilare codice multipiattaforma destinato anche a UWP, selezionare il carico di lavoro **Sviluppo di app per la piattaforma UWP (Universal Windows Platform)**.

1. Nel riquadro **Dettagli di installazione** espandere **Sviluppo di applicazioni per dispositivi mobili con C++**. Nella sezione **Facoltativo** è possibile scegliere altre versioni di NDK, l'emulatore Android di Google, Intel Hardware Accelerated Execution Manager e lo strumento di accelerazione per le build IncrediBuild.

1. Per impostazione predefinita, nel carico di lavoro sono inclusi uno o più componenti di installazione di Android SDK. Sono disponibili altre versioni di Android SDK. Per aggiungerne una all'installazione, scegliere la scheda **Singoli componenti** e quindi scorrere verso il basso fino alla sezione **SDK, librerie e framework** per effettuare la selezione.

1. Scegliere il pulsante **Modifica** o **Installa** per installare il carico di lavoro **Sviluppo di applicazioni per dispositivi mobili con C++** e gli altri carichi di lavoro e componenti facoltativi selezionati.

   Al termine dell'installazione, chiudere il programma di installazione e riavviare il computer. Alcune azioni di installazione per i componenti di terze parti non hanno effetto finché il computer non viene riavviato.

   > [!IMPORTANT]
   > Il riavvio è necessario per assicurare la corretta installazione di tutti i componenti.

1. Aprire Visual Studio. Se è la prima volta che si esegue Visual Studio, la configurazione e l'accesso possono richiedere tempo. Quando Visual Studio è pronto, verificare la presenza di eventuali aggiornamenti e installarli.

#### <a name="to-install-the-mobile-development-component-and-third-party-tools-in-visual-studio-2015"></a>Per installare il componente di sviluppo per dispositivi mobili e strumenti di terze parti in Visual Studio 2015

Se si usa Visual Studio 2015, il programma di installazione include un'opzione per installare Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma, che consente di installare gli strumenti, i modelli e i componenti del linguaggio C++ necessari in Visual Studio 2015.

1. Eseguire il programma di installazione di Visual Studio 2015. Per installare i componenti facoltativi, scegliere **Personalizzata** come tipo di installazione. Scegliere **Avanti** per selezionare i componenti facoltativi da installare.

1. In **Selezione funzionalità** espandere **Sviluppo di app per dispositivi mobili multipiattaforma** e selezionare **Sviluppo di app per dispositivi mobili in Visual C++**.

   ![Selezionare Sviluppo di app per dispositivi mobili in Visual C&#43;&#43;](../cross-platform/media/cppmdd_install_vcmdd.png "CPPMDD_Install_VCMDD")

   Per impostazione predefinita, quando si seleziona **Sviluppo di app per dispositivi mobili in Visual C++**, l'opzione **Linguaggi di programmazione** viene impostata per installare **Visual C++** e le opzioni **Strumenti comuni e Software Development Kit** vengono impostate per installare i componenti di terze parti richiesti. Se necessario, è possibile scegliere componenti aggiuntivi. Per impostazione predefinita, è selezionato anche **Microsoft Visual Studio Emulator for Android**. I componenti già installati risultano inattivi nell'elenco.

   Per compilare app di Windows universale e condividere codice tra tali app e i progetti iOS e Android, in **Selezione funzionalità** espandere **Sviluppo per Windows e Web** e selezionare **Strumenti per lo sviluppo di app di Windows universale**. Se non si prevede di sviluppare app di Windows universale, è possibile ignorare questa opzione.

   Scegliere **Avanti** per continuare.

1. I componenti di terze parti hanno condizioni di licenza proprie. Per visualizzare le condizioni di licenza, scegliere il collegamento **Condizioni di licenza** accanto a ogni componente. Scegliere **Installa** per aggiungere i componenti e installare Visual Studio e Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma.

1. Al termine dell'installazione, chiudere il programma di installazione e riavviare il computer. Alcune azioni di installazione per i componenti di terze parti non hanno effetto finché il computer non viene riavviato.

   > [!IMPORTANT]
   > Il riavvio è necessario per assicurare la corretta installazione di tutti i componenti.

   Se non è possibile installare il componente Microsoft Visual Studio Emulator for Android, Hyper-V potrebbe non essere abilitato nel computer. Usare l'app **Attivazione o disattivazione delle funzionalità Windows** del Pannello di controllo per abilitare Hyper-V e quindi eseguire nuovamente il programma di installazione di Visual Studio.

   > [!NOTE]
   > Se il computer o la versione di Windows in uso non supporta Hyper-V, non è possibile usare il componente Microsoft Visual Studio Emulator for Android. L'edizione Home di Windows non include il supporto per Hyper-V.

1. Aprire Visual Studio. Se è la prima volta che si esegue Visual Studio, la configurazione e l'accesso possono richiedere tempo. Quando Visual Studio è pronto, nel menu **Strumenti** selezionare **Estensioni e aggiornamenti**, quindi **Aggiornamenti**. Se sono disponibili aggiornamenti di Visual Studio per Visual C++ per Sviluppo app per dispositivi mobili multipiattaforma o per Microsoft Visual Studio Emulator for Android, è necessario installarli.

## <a name="install-tools-for-ios"></a>Install tools for iOS

È possibile usare il componente Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma per modificare, eseguire il debug e distribuire codice iOS nel simulatore iOS o in un dispositivo iOS ma, a causa di restrizioni di licenza, il codice deve essere compilato in remoto su Mac. Per compilare ed eseguire le app iOS usando Visual Studio, è necessario installare e configurare l'agente remoto sul Mac. Per istruzioni dettagliate sull'installazione, prerequisiti e le opzioni di configurazione, vedere [Installare e configurare strumenti per la compilazione con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Se non si compila per iOS, è possibile ignorare questo passaggio.

## <a name="install-or-update-dependencies-manually"></a>Installare o aggiornare manualmente le dipendenze

Se si decide di non installare una o più dipendenze di terze parti con il programma di installazione di Visual Studio quando si installa il carico di lavoro **Sviluppo di applicazioni per dispositivi mobili con C++** (oppure in Visual Studio 2015 l'opzione Sviluppo di app per dispositivi mobili in Visual C++), è possibile installarle in un secondo momento usando la procedura descritta in [Installare gli strumenti](#install-the-tools). Il programma di installazione di Visual Studio viene aggiornato regolarmente per installare i componenti di terze parti più recenti. È possibile usarlo per l'installazione di SDK e NDK aggiornati. Possono anche essere installate a aggiornate in modo indipendente da Visual Studio.

> [!CAUTION]
> È possibile installare le dipendenze in qualsiasi ordine, ad eccezione di Java. È necessario installare e configurare il JDK prima di installare Android SDK.

Leggere le seguenti informazioni e usare questi collegamenti per installare manualmente le dipendenze.

- [Java SE Development Kit](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

   Per impostazione predefinita, il programma di installazione inserisce gli strumenti Java in *C:\Programmi (x86)\Java*.

- [Android SDK](https://developer.android.com/sdk/index.html#command-tools)

   Durante l'installazione, aggiornare le API come consigliato. Verificare che sia installato almeno l'SDK per Android 5.0 Lollipop (API livello 21). Per impostazione predefinita, il programma di installazione inserisce Android SDK in *C:\Programmi (x86)\Android\android-sdk*.

   È possibile eseguire di nuovo l'app SDK Manager nella directory Android SDK per aggiornare l'SDK e installare strumenti facoltativi e livelli API aggiuntivi. L'installazione degli aggiornamenti potrebbe non riuscire se non si usa **Esegui come amministratore** per eseguire l'app SDK Manager. In caso di problemi durante la compilazione di un'app Android, in SDK Manager verificare la disponibilità di aggiornamenti per gli SDK installati.

   Per usare alcuni degli emulatori Android forniti con Android SDK, è necessario installare i driver HAXM Intel facoltativi. Può essere necessario rimuovere la funzionalità Hyper-V da Windows per installare correttamente i driver HAXM di Intel. È necessario ripristinare la funzionalità Hyper-V per usare gli emulatori Windows Phone e l'emulatore di Visual Studio per Android. Per altre informazioni, vedere [Accelerazione hardware per le prestazioni dell'emulatore Android](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

- [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)

   Per impostazione predefinita, il programma di installazione inserisce Android NDK in *C:\ProgramData\Microsoft\AndroidNDK*. È possibile scaricare e installare di nuovo Android NDK per aggiornare l'installazione.

- [Apache Ant](https://ant.apache.org/bindownload.cgi)

   Per impostazione predefinita, il programma di installazione inserisce Apache Ant in *C:\Programmi (x86)\Microsoft Visual Studio 14.0\Apps*.

- [Microsoft Visual Studio Emulator for Android](https://aka.ms/vscomemudownload)

   Microsoft Visual Studio Emulator for Android è un emulatore facoltativo utile per il test e il debug del codice. Dopo il rilascio di Visual Studio Emulator for Android, Google ha aggiornato il suo emulatore Android per usare l'accelerazione hardware tramite Intel HAXM. È consigliabile usare l'emulatore accelerato di Google quando possibile, perché offre l'accesso alle immagini del sistema operativo Android più recenti e ai servizi Google Play.

Nella maggior parte dei casi, Visual Studio è in grado di rilevare le configurazioni per il software di terze parti installato e mantiene i percorsi di installazione in variabili di ambiente interne. È possibile eseguire l'override dei percorsi predefiniti di questi strumenti di sviluppo multipiattaforma nell'IDE di Visual Studio.

#### <a name="to-set-the-paths-for-third-party-tools"></a>Per impostare i percorsi per gli strumenti di terze parti

1. Sulla barra dei menu di Visual Studio scegliere **Strumenti** > **Opzioni**.

1. Nella finestra di dialogo **Opzioni** selezionare **Multipiattaforma** > **C++** > **Android**.

   ![Opzioni di percorso dello strumento Android](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. Per modificare il percorso usato da uno strumento, selezionare la casella di controllo accanto al percorso e modificare il percorso della cartella nella casella di testo. È anche possibile usare il pulsante Sfoglia (**...**) per aprire una finestra di dialogo **Selezionare il percorso** in cui scegliere la cartella.

1. Scegliere **OK** per salvare i percorsi personalizzati delle cartelle degli strumenti.

## <a name="see-also"></a>Vedere anche

- [Installare e configurare strumenti per la compilazione con iOS](install-and-configure-tools-to-build-using-ios.md)
- [Visual C++ per lo sviluppo di codice per dispositivi mobili multipiattaforma](https://go.microsoft.com/fwlink/p/?LinkId=536383)
