---
title: Installare lo sviluppo di app per dispositivi C++ mobili multipiattaforma con | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
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
ms.openlocfilehash: 25bd88886b6bed447ec7d091543fccdb478db9c5
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588874"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>Installare lo sviluppo di app per dispositivi mobili multipiattaforma conC++

È possibile usare C++ in Visual Studio per compilare app desktop di Windows, app UWP (Universal Windows Platform), app di Linux e ora anche app per Android e iOS. Il carico di lavoro **Sviluppo di applicazioni per dispositivi mobili con C++** è un set di componenti installabili in Visual Studio che include modelli di Visual Studio multipiattaforma per iOS, Android e UWP. Questo carico di lavoro installa gli SDK e gli strumenti multipiattaforma necessari per iniziare rapidamente, senza doverli individuare, scaricare e configurare manualmente. Con questi strumenti di Visual Studio è possibile creare, modificare, eseguire il debug e testare facilmente i progetti multipiattaforma. Questo articolo descrive come installare gli strumenti e il software di terze parti necessari per sviluppare app multipiattaforma in C++ usando Visual Studio. Per una panoramica, vedere [Visual C++ per lo sviluppo di codice per dispositivi mobili multipiattaforma](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)

## <a name="requirements"></a>Requisiti

::: moniker range="vs-2017"

- Per i requisiti di installazione, vedere [Requisiti di sistema per la famiglia di prodotti Visual Studio 2017](/visualstudio/productinfo/vs2017-system-requirements-vs).

   > [!IMPORTANT]
   > Se si usa Windows 7 o Windows Server 2008 R2, è possibile sviluppare codice per le applicazioni desktop di Windows, le app e le librerie Android Native Activity, nonché le app e le librerie di codice per iOS, ma non le app di Windows Store o UWP.

::: moniker-end
::: moniker range=">=vs-2019"

- Per i requisiti di installazione, vedere [Requisiti di sistema per la famiglia di prodotti Visual Studio 2017](/visualstudio/releases/2019/system-requirements).

   > [!IMPORTANT]
   > Se si usa Windows 7 o Windows Server 2008 R2, è possibile sviluppare codice per applicazioni desktop di Windows classiche, librerie e app Android NativeActivity, nonché librerie di codice e app per iOS, ma non app di Windows Phone o UWP.

::: moniker-end

Per compilare le app per specifiche piattaforme del dispositivo sono necessari alcuni requisiti aggiuntivi:

- Gli emulatori Android x86 inclusi nel Android SDK funzionano meglio nei computer che possono usare l'accelerazione hardware, ad esempio Intel Hardware Accelerated Execution Manager (HAXM). Per ulteriori informazioni, vedere [accelerazione hardware per le prestazioni dell'emulatore (Hyper-V & HAXM)](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin&pivots=windows).

- La compilazione di codice per iOS richiede un ID Apple, un account iOS Developer Program e un computer Mac in grado di eseguire [Xcode](https://developer.apple.com/xcode/) versione 10,2 o successiva in OS X Mavericks (versione 10,9) o versioni successive. Per un collegamento alla procedura di installazione, vedere [Installare gli strumenti per iOS](#install-tools-for-ios).

- Gli emulatori Windows Phone richiedono un computer in grado di eseguire Hyper-V. Per poter installare ed eseguire gli emulatori, è prima necessario abilitare la funzionalità Hyper-V in Windows. Per altre informazioni, vedere i [requisiti di sistema](system-requirements-for-the-visual-studio-emulator-for-android.md)dell'emulatore.

## <a name="get-the-tools"></a>Ottenere gli strumenti

Il carico di lavoro Sviluppo di applicazioni per dispositivi mobili con C++ è disponibile nelle edizioni Community, Professional ed Enterprise di Visual Studio. Per ottenere Visual Studio, passare alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/). Gli strumenti di sviluppo per dispositivi mobili multipiattaforma sono disponibili a partire da Visual Studio 2015.

## <a name="install-the-tools"></a>Installare gli strumenti

Il programma di installazione di Visual Studio include uno **sviluppo per dispositivi C++ mobili con carico di** lavoro. Questo carico di lavoro C++ consente di installare gli strumenti, i modelli e i componenti del linguaggio richiesti per lo sviluppo di Android e iOS in Visual Studio. Include i set di strumenti GCC e clang necessari per le compilazioni e il debug di Android, il Android SDK e i componenti per comunicare con un Mac per lo sviluppo di iOS. Installa anche tutti gli altri strumenti di terze parti e Software Development Kit necessari per supportare lo sviluppo di app iOS e Android. Molti di questi strumenti di terze parti sono software open source necessari per il supporto della piattaforma Android.

- Android Native Development Kit (NDK), Apache Ant e gli C++ strumenti di sviluppo di Android sono necessari per C++ compilare il codice destinato alla piattaforma Android.

- Google emulatore Android e Intel Hardware Accelerated Execution Manager (HAXM) sono componenti facoltativi, ma consigliati. I driver Intel HAXM funzionano solo con processori Intel e sono incompatibili con alcune macchine virtuali, incluso Hyper-V. È possibile sviluppare ed eseguire il debug direttamente su un dispositivo Android, ma spesso è più semplice usare un emulatore sul desktop per il debug.

- C++gli strumenti di sviluppo iOS sono necessari C++ per compilare il codice destinato alla piattaforma iOS.

> [!NOTE]
> Se si usa Visual Studio 2015, vedere [Installare Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma (Visual Studio 2015)](install-visual-cpp-for-cross-platform-mobile-development.md?view=vs-2015)

### <a name="install-the-mobile-development-with-c-workload"></a>Installare il carico di lavoro Sviluppo di applicazioni per dispositivi mobili con C++

1. Eseguire il **programma di installazione di Visual Studio** dal menu **Start**.

1. Se è già stato installato Visual Studio, scegliere il pulsante **Modifica** per la versione installata di Visual Studio che si vuole modificare. In caso contrario, scegliere **Installa** per installare Visual Studio.

1. Con la scheda **Carichi di lavoro** selezionata, scorrere verso il basso e selezionare il carico di lavoro **Sviluppo di applicazioni per dispositivi mobili con C++** nel programma di installazione di Visual Studio. Quando questo carico di lavoro è selezionato, verranno selezionati anche altri componenti necessari per lo sviluppo C++. È anche possibile scegliere altri carichi di lavoro e singoli componenti da installare contemporaneamente. Per compilare codice multipiattaforma destinato anche a UWP, selezionare il carico di lavoro **Sviluppo di app per la piattaforma UWP (Universal Windows Platform)** .

1. Nel riquadro **Dettagli di installazione** espandere **Sviluppo di applicazioni per dispositivi mobili con C++** . Nella sezione **Facoltativo** è possibile scegliere altre versioni di NDK, l'emulatore Android di Google, Intel Hardware Accelerated Execution Manager e lo strumento di accelerazione per le build IncrediBuild.

1. Per impostazione predefinita, nel carico di lavoro sono inclusi uno o più componenti di installazione di Android SDK. Sono disponibili altre versioni di Android SDK. Per aggiungerne una all'installazione, scegliere la scheda **Singoli componenti** e quindi scorrere verso il basso fino alla sezione **SDK, librerie e framework** per effettuare la selezione.

1. Scegliere il pulsante **Modifica** o **Installa** per installare il carico di lavoro **Sviluppo di applicazioni per dispositivi mobili con C++** e gli altri carichi di lavoro e componenti facoltativi selezionati.

   Al termine dell'installazione, chiudere il programma di installazione e riavviare il computer. Alcune azioni di installazione per i componenti di terze parti non hanno effetto finché il computer non viene riavviato.

   > [!IMPORTANT]
   > Il riavvio è necessario per assicurare la corretta installazione di tutti i componenti.

1. Aprire Visual Studio.

## <a name="install-tools-for-ios"></a>Install tools for iOS

È possibile usare Visual Studio per modificare, eseguire il debug e distribuire codice iOS al simulatore iOS o a un dispositivo iOS. Tuttavia, a causa delle restrizioni di licenza, il codice deve essere compilato in remoto su un Mac. Per compilare ed eseguire le app iOS usando Visual Studio, è necessario installare e configurare l'agente remoto sul Mac. Per istruzioni dettagliate sull'installazione, prerequisiti e le opzioni di configurazione, vedere [Installare e configurare strumenti per la compilazione con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Se non si compila per iOS, è possibile ignorare questo passaggio.

## <a name="install-or-update-dependencies-manually"></a>Installare o aggiornare manualmente le dipendenze

Se si decide di non installare una o più dipendenze di terze parti con il programma di installazione di Visual Studio quando si installa il carico di lavoro **Sviluppo di applicazioni per dispositivi mobili con C++** (oppure in Visual Studio 2015 l'opzione Sviluppo di app per dispositivi mobili in Visual C++), è possibile installarle in un secondo momento usando la procedura descritta in [Installare gli strumenti](#install-the-tools). Il programma di installazione di Visual Studio viene aggiornato regolarmente per installare i componenti di terze parti più recenti. È possibile usarlo per l'installazione di SDK e NDK aggiornati. Possono anche essere installate a aggiornate in modo indipendente da Visual Studio.

È possibile eseguire di nuovo l'app SDK Manager nella directory Android SDK per aggiornare l'SDK e installare strumenti facoltativi e livelli API aggiuntivi. L'installazione degli aggiornamenti potrebbe non riuscire se non si usa **Esegui come amministratore** per eseguire l'app SDK Manager. In caso di problemi durante la compilazione di un'app Android, in SDK Manager verificare la disponibilità di aggiornamenti per gli SDK installati.

Per usare alcuni degli emulatori Android disponibili con il Android SDK, potrebbe essere necessario configurare l'accelerazione hardware. Per ulteriori informazioni, vedere [accelerazione hardware per le prestazioni dell'emulatore (Hyper-V & HAXM)](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

Nella maggior parte dei casi, Visual Studio è in grado di rilevare le configurazioni per il software di terze parti installato e mantiene i percorsi di installazione in variabili di ambiente interne. È possibile eseguire l'override dei percorsi predefiniti di questi strumenti di sviluppo multipiattaforma nell'IDE di Visual Studio.

#### <a name="to-set-the-paths-for-third-party-tools"></a>Per impostare i percorsi per gli strumenti di terze parti

1. Sulla barra dei menu di Visual Studio scegliere **Strumenti** > **Opzioni**.

1. Nella finestra di dialogo **Opzioni** selezionare **Multipiattaforma** > **C++**  > **Android**.

   ![Opzioni di percorso dello strumento Android](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. Per modificare il percorso usato da uno strumento, selezionare la casella di controllo accanto al percorso e modificare il percorso della cartella nella casella di testo. È anche possibile usare il pulsante Sfoglia ( **...** ) per aprire una finestra di dialogo **Selezionare il percorso** in cui scegliere la cartella.

1. Scegliere **OK** per salvare i percorsi personalizzati delle cartelle degli strumenti.

## <a name="see-also"></a>Vedere anche

- [Install And Configure Tools to Build using iOS](install-and-configure-tools-to-build-using-ios.md) (Installare e configurare strumenti per compilare con iOS)
- [Visual C++ per lo sviluppo di codice per dispositivi mobili multipiattaforma](https://go.microsoft.com/fwlink/p/?LinkId=536383)
