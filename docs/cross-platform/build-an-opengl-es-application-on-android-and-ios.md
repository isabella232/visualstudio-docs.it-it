---
title: Compilare un'applicazione OpenGL ES in Android e iOS | Microsoft Docs
ms.custom: ''
ms.date: 05/16/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: aa8ffe308f8a1181ed18af52ba7537c46007de94
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317642"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Compilare un'applicazione OpenGL ES in Android e iOS

È possibile creare soluzioni di Visual Studio e progetti per le app iOS e Android che condividono codice comune. Questo articolo descrive un modello di soluzione che crea un'app iOS semplice e un'app NativeActivity di Android. Le app hanno un codice C++ in comune che usa OpenGL ES per visualizzare lo stesso cubo rotante animato in tutte le piattaforme. OpenGL ES (OpenGL for Embedded Systems o GLES) è un'API grafica 2D e 3D supportata in molti dispositivi mobili.

## <a name="requirements"></a>Requisiti

Prima di creare un'app OpenGL ES per iOS e Android, verificare che tutti i requisiti di sistema siano soddisfatti. Se non è già stato fatto, installare il carico di lavoro Sviluppo di applicazioni per dispositivi mobili con C++ nel programma di installazione di Visual Studio. Per sviluppare per iOS, includere gli strumenti di sviluppo per app iOS in C++ facoltativi. Per sviluppare per Android, installare gli strumenti di sviluppo per app Android in C++ e gli strumenti di terze parti richiesti: Android NDK, Apache Ant, l'emulatore Android di Google e Intel Hardware Accelerated Execution Manager. Configurare poi Intel HAXM e l'emulatore Android per l'esecuzione nel sistema. Per altre informazioni e istruzioni dettagliate, vedere [Installare Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Per compilare e testare l'app iOS, è necessario un computer Mac, configurato in base alle istruzioni di installazione. Per altre informazioni sulla configurazione per lo sviluppo per iOS, vedere [Installare e configurare gli strumenti per la compilazione con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)

## <a name="create-a-new-opengles-application-project"></a>Creare un nuovo progetto di applicazione OpenGLES

In questa esercitazione verrà creato un nuovo progetto di applicazione OpenGL ES, quindi verrà compilata ed eseguita l'app predefinita in Visual Studio Emulator per Android. Quindi, l'app per iOS verrà compilata ed eseguita in un dispositivo iOS.

1. In Visual Studio scegliere **File** > **Nuovo** > **Progetto**.

1. Nella finestra di dialogo **Nuovo progetto** in **Modelli**scegliere **Visual C++**  > **Multipiattaforma**, quindi scegliere il modello **Applicazione OpenGLES (Android, iOS)** .

1. Assegnare all'app un nome come `MyOpenGLESApp`e fare clic su **OK**.

   ![Nuovo progetto applicazione OpenGLES](../cross-platform/media/cppmdd_opengles_newproj.PNG "CPPMDD_OpenGLES_NewProj")

   Visual Studio crea la nuova soluzione e apre Esplora soluzioni.

   ![MyOpenGLESApp in Esplora soluzioni](../cross-platform/media/cppmdd_opengles_solexpl.PNG "CPPMDD_OpenGLES_SolExpl")

   La nuova soluzione di applicazione OpenGL ES include tre progetti di libreria e due progetti di applicazione. La cartella Librerie include un progetto di codice condiviso e due progetti specifici per la piattaforma che fanno riferimento al codice condiviso:

- `MyOpenGLESApp.Android.NativeActivity`, che contiene i riferimenti e il codice glue che implementa l'app come NativeActivity in Android. I punti di ingresso dal codice glue vengono implementati in *main.cpp*, che include il codice condiviso comune in `MyOpenGLESApp.Shared`. Le intestazioni precompilate sono in *pch.h*. Questo progetto di app NativeActivity viene compilato in un file di libreria condivisa (con estensione *so*), selezionato dal progetto `MyOpenGLESApp.Android.Packaging`.

- `MyOpenGLESApp.iOS.StaticLibrary` crea un file di libreria statica iOS (con estensione *a*) contenente il codice condiviso in `MyOpenGLESApp.Shared`. È collegato all'app creata dal progetto `MyOpenGLESApp.iOS.Application`.

- `MyOpenGLESApp.Shared` contiene il codice condiviso multipiattaforma. Usa le macro del preprocessore per la compilazione condizionale del codice specifico per la piattaforma. Il codice condiviso viene selezionato per riferimento al progetto sia in `MyOpenGLESApp.Android.NativeActivity` che in `MyOpenGLESApp.iOS.StaticLibrary`.

La soluzione contiene due progetti per compilare le app per le piattaforme Android e iOS:

- `MyOpenGLESApp.Android.Packaging`, che crea il file con estensione *apk* per la distribuzione nei dispositivi o negli emulatori Android. Questo file contiene le risorse e il file AndroidManifest.xml in cui sono state impostate le proprietà del manifesto. Contiene anche il file *build.xml*, che controlla il processo di compilazione Ant. Per impostazione predefinita, è impostato come progetto di avvio in modo che possa essere distribuito ed eseguito direttamente da Visual Studio.

- **MyOpenGLESApp.iOS.Application** contiene le risorse e il codice glue Objective-C per creare un'app iOS che collega il codice della libreria statica C++ in `MyOpenGLESApp.iOS.StaticLibrary`. Questo progetto crea un pacchetto di compilazione che viene trasferito al Mac da Visual Studio e dall'agente remoto. Quando si compila questo progetto, Visual Studio invia i file e i comandi per compilare e distribuire l'app nel Mac.

## <a name="build-and-run-the-android-app"></a>Compilare ed eseguire l'app Android

La soluzione creata dal modello imposta l'app Android come progetto predefinito.  È possibile compilare ed eseguire l'app per verificare l'installazione e la configurazione. Per un test iniziale, eseguire l'app in uno dei profili del dispositivo installati dall'emulatore per Android. Se si preferisce testare l'app in un'altra destinazione, è possibile caricare l'emulatore di destinazione o connettere il dispositivo al computer.

### <a name="to-build-and-run-the-android-native-activity-app"></a>Per compilare ed eseguire l'app NativeActivity di Android

1. Se non è ancora selezionato, scegliere **x86** dall'elenco a discesa **Piattaforme soluzione**.

   ![Impostare la piattaforma soluzione su x86](../cross-platform/media/cppmdd_opengles_solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")

   Usare x86 per fare riferimento all'emulatore. Per impostare un dispositivo come destinazione, scegliere la piattaforma soluzione basata sul processore del dispositivo. Se l'elenco **Piattaforme soluzione** non è visualizzato, scegliere **Piattaforme soluzione** dall'elenco **Aggiungi o rimuovi pulsanti** e quindi scegliere la piattaforma.

1. In **Esplora soluzioni** aprire il menu di scelta rapida del progetto `MyOpenGLESApp.Android.Packaging` e scegliere **Compila**.

   ![Compilare il progetto di pacchetti Android](../cross-platform/media/cppmdd_opengles_andbuild.png "CPPMDD_OpenGLES_AndBuild")

   La finestra di output visualizza l'output del processo di compilazione per la libreria condivisa e l'app di Android.

   ![Output di compilazione per progetti Android](../cross-platform/media/cppmdd_opengles_andoutput.png "CPPMDD_OpenGLES_AndOutput")

1. Scegliere uno dei profili di dispositivo emulato Android come destinazione della distribuzione.

   ![Scegliere la destinazione di distribuzione](../cross-platform/media/cppmdd_opengles_pickemulator.png "CPPMDD_OpenGLES_PickEmulator")

   Se sono installati altri emulatori o è connesso un dispositivo Android, è possibile sceglierli nell'elenco a discesa delle destinazioni della distribuzione. Per eseguire l'app, la piattaforma soluzione compilata deve corrispondere alla piattaforma del dispositivo di destinazione.

1. Premere F5 per avviare il debug o MAIUSC+F5 per avviare senza eseguire il debug.

   Visual Studio avvia l'emulatore, che richiede alcuni secondi per caricare e distribuire il codice. Ecco come viene visualizzata l'app nell'emulatore:

   ![App in esecuzione nell'emulatore per Android](../cross-platform/media/cppmdd_opengles_andemulator.png "CPPMDD_OpenGLES_AndEmulator")

   Una volta avviata l'app, è possibile impostare i punti di interruzione e usare il debugger per eseguire il codice un'istruzione alla volta, esaminare le variabili locali e controllare i valori.

1. Premere **MAIUSC**+**F5** per interrompere il debug.

   L'emulatore è un processo separato che continua a essere eseguito. È possibile modificare, compilare e distribuire il codice più volte nello stesso emulatore. L'app viene visualizzata nella raccolta di app nell'emulatore e può essere avviata direttamente da questa posizione.

   I progetti della libreria e dell'app NativeActivity di Android generati inseriscono il codice condiviso C++ di una libreria dinamica che include il codice "glue" nell'interfaccia con la piattaforma Android. La maggior parte del codice dell'app si trova nella libreria e il manifesto, le risorse e le istruzioni di compilazione si trovano nel progetto di creazione del pacchetto. Il codice condiviso viene chiamato da main.cpp nel progetto NativeActivity. Per altre informazioni su come programmare NativeActivity di Android, vedere la pagina dei [concetti](https://developer.android.com/ndk/guides/concepts.html) di Android Developer NDK.

   Visual Studio compila i progetti NativeActivity di Android usando Android NDK, che usa Clang come set di strumenti della piattaforma. Visual Studio esegue il mapping delle proprietà del progetto NativeActivity alle opzioni usate per compilare, collegare ed eseguire il debug nella piattaforma di destinazione. Per dettagli, aprire la finestra di dialogo **Pagine delle proprietà** per il progetto MyOpenGLESApp.Android.NativeActivity. Per altre informazioni sulle opzioni della riga di comando, vedere [Clang Compiler User's Manual](http://clang.llvm.org/docs/UsersManual.html) (Manuale dell'utente del compilatore Clang).

## <a name="build-and-run-the-ios-app-on-an-ios-device"></a>Compilare ed eseguire l'app iOS in un dispositivo iOS

Il progetto dell'app iOS viene creato e modificato in Visual Studio, ma deve essere compilato e distribuito da un Mac a causa di restrizioni relative alla licenza. Visual Studio comunica con un agente remoto in esecuzione nel Mac per trasferire i file del progetto ed eseguire i comandi di compilazione, distribuzione e debug. Per compilare l'app iOS, impostare e configurare il Mac e Visual Studio per la comunicazione. Per istruzioni dettagliate, vedere [Installare e configurare gli strumenti per la compilazione con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Quando l'agente remoto è in esecuzione nel Mac e associato a Visual Studio, è possibile compilare ed eseguire l'app iOS per verificare l'installazione e la configurazione.

Per distribuire un'app iOS in un dispositivo iOS, è necessario anche configurare la firma automatica in Xcode nel Mac. La firma automatica gestisce automaticamente la firma delle app e crea un profilo di provisioning per firmare una compilazione dell'app.

### <a name="to-set-up-automatic-signing-on-xcode"></a>Per configurare la firma automatica in Xcode

1. Se non è già stato fatto, installare [Xcode](https://developer.apple.com/xcode/downloads/) versione 10.2.1 o successiva nel computer Mac.

1. Aprire l'app Xcode nel Mac.

1. Creare un nuovo progetto Xcode **Single View Application** (Applicazione a vista singola). Compilare i campi richiesti durante la creazione del progetto. I valori possono essere arbitrari, dato che il progetto viene usato solo per creare un profilo di provisioning che viene usato in un secondo momento per firmare una compilazione dell'app.

1. Aggiungere il proprio ID Apple registrato in un account [Apple Developer Program](https://developer.apple.com/programs/) in Xcode. L'ID Apple viene usato come identità di firma per firmare le app. Per aggiungere l'identità di firma in Xcode, aprire il menu **Xcode** e scegliere **Preferences** (Preferenze). Selezionare **Accounts** e fare clic sul pulsante Aggiungi (+) per aggiungere l'ID Apple. Per istruzioni dettagliate, vedere [Add your Apple ID account](https://help.apple.com/xcode/mac/current/#/devaf282080a) (Aggiungere l'account ID Apple).

1. Dalle impostazioni generali del progetto Xcode, modificare il valore di **Bundle Identifier** (Identificatore bundle) in `com.<NameOfVSProject>`, dove `<NameOfVSProject>` è lo stesso nome del progetto di soluzione di Visual Studio creato. Ad esempio, se è stato creato un progetto denominato `MyOpenGLESApp` in Visual Studio, impostare **Bundle Identifier** (Identificatore bundle) su `com.MyOpenGLESApp`

   ![Identificatore del bundle Xcode](../cross-platform/media/cppmdd-opengles-iosxcodeid.png "CPPMDD_OpenGLES_iOSXcodeId")

1. Per abilitare la firma automatica, selezionare Automatically manage signing (Gestisci automaticamente la firma)**.

   ![Firma automatica Xcode](../cross-platform/media/cppmdd-opengles-iosxcodesign.png "CPPMDD_OpenGLES_iOSXcodeSign")

1. Selezionare il nome del team dell'ID Apple come **Team** di sviluppo.

   ![Team di Xcode](../cross-platform/media/cppmdd-opengles-iosxcodeteam.png "CPPMDD_OpenGLES_iOSXcodeTeam")

### <a name="to-build-and-run-the-ios-app-on-an-ios-device"></a>Per compilare ed eseguire l'app iOS in un dispositivo iOS

1. Eseguire l'agente remoto nel Mac e verificare che Visual Studio sia associato all'agente remoto. Per avviare l'agente remoto, aprire una finestra dell'app terminale e immettere `vcremote`. Per altre informazioni, vedere [Configurare l'agente remoto in Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).

   ![Finestra del terminale Mac che esegue vcremote](../cross-platform/media/cppmdd_common_vcremote.png "CPPMDD_common_vcremote")

1. Collegare un dispositivo iOS al Mac. Quando si collega il dispositivo a un computer per la prima volta, un avviso richiede si considera attendibile il computer per l'accesso al dispositivo. Consentire al dispositivo di considerare attendibile il computer Mac.

1. In Visual Studio, se non è già selezionata, scegliere la piattaforma della soluzione nell'elenco a discesa **Piattaforme soluzione** in base al processore del dispositivo. In questo esempio si tratta di un processore **ARM64**.

   ![Impostare la piattaforma soluzione su ARM64](../cross-platform/media/cppmdd-opengles-pickplatformarm64.png "CPPMDD_OpenGLES_SolutionPlatARM64")

1. In Esplora soluzioni aprire il menu di scelta rapida per il progetto MyOpenGLESApp.iOS.Application e scegliere **Scarica progetto**.

1. Anche in questo caso, aprire il menu di scelta rapida per il progetto MyOpenGLESApp.iOS.Application scaricato e scegliere **Modifica project.pbxproj** per modificare il file di progetto. Nel file `project.pbxproj` cercare l'attributo `buildSettings` e aggiungere `DEVELOPMENT_TEAM` usando l'ID Apple del team. Lo screenshot seguente mostra il valore di esempio `123456ABC` per l'ID Apple del team. È possibile trovare il valore dell'ID Apple del team da Xcode. Passare a **Build Settings** (Impostazioni compilazione) e passare il mouse sul nome del team di sviluppo per visualizzare una descrizione comando. La descrizione comando indica l'ID del team.

   ![Impostare il team di sviluppo](../cross-platform/media/cppmdd-opengles-iosdevelopmentteam.png "CPPMDD_OpenGLES_iOSDevelopmentTeam")

1. Chiudere il file `project.pbxproj`, quindi aprire il menu di scelta rapida per il progetto MyOpenGLESApp.iOS.Application scaricato e scegliere **Ricarica progetto** per ricaricare il progetto.

1. A questo punto compilare il progetto MyOpenGLESApp.iOS.Application aprendo il menu di scelta rapida per il progetto e scegliendo **Compila**.

   ![Compilare il progetto applicazione iOS](../cross-platform/media/cppmdd_opengles_iosbuild.png "CPPMDD_OpenGLES_iOSBuild")

   La finestra di output visualizza l'output del processo di compilazione per la libreria statica e l'app di iOS. Nel Mac la finestra terminale che esegue l'agente remoto mostra il comando e l'attività di trasferimento dei file.

   Nel computer Mac potrebbe essere richiesto di consentire a codesign di accedere al keychain. Scegliere **Consenti** per continuare.

1. Scegliere il dispositivo iOS sulla barra degli strumenti per eseguire l'app nel dispositivo collegato al Mac. Se l'app non viene avviata, verificare che il dispositivo conceda l'autorizzazione di esecuzione nel dispositivo all'applicazione distribuita. Questa autorizzazione può essere impostata passando a **Impostazioni** > **Generali** > **Gestione dei dispositivi** nel dispositivo. Selezionare l'account Developer App (App sviluppatore), impostare come attendibile l'account e verificare l'app. Provare a eseguire nuovamente l'app da Visual Studio.

   ![App iOS nel dispositivo iOS](../cross-platform/media/cppmdd-opengles-iosdevice.png "CPPMDD_OpenGLES_iOSDevice")
   
   Una volta avviata l'app, è possibile impostare i punti di interruzione e usare il debugger di Visual Studio per esaminare le variabili locali, visualizzare lo stack di chiamate e controllare i valori.

   ![Debugger nel punto di interruzione nell'app iOS](../cross-platform/media/cppmdd_opengles_iosdebug.png "CPPMDD_OpenGLES_iOSDebug")

1. Premere **MAIUSC**+**F5** per interrompere il debug.

   I progetti della libreria e dell'app iOS generati inseriscono il codice C++ in una libreria statica che implementa solo il codice condiviso. La maggior parte del codice dell'applicazione si trova nel progetto `Application`. Le chiamate al codice della libreria condivisa in questo progetto di modello vengono eseguite nel file *GameViewController.m*. Per compilare l'app iOS, Visual Studio usa il set di strumenti della piattaforma Xcode, che richiede la comunicazione con un client remoto in esecuzione in un Mac.

   Visual Studio trasferisce i file del progetto e invia i comandi al client remoto per compilare l'app con Xcode. Il client remoto invia a sua volta le informazioni sullo stato della compilazione a Visual Studio. Dopo aver compilato l'app, è possibile usare Visual Studio per inviare i comandi per l'esecuzione e il debug dell'app. Il debugger di Visual Studio controlla l'esecuzione dell'app nel dispositivo iOS collegato al Mac. Visual Studio esegue il mapping delle proprietà del progetto StaticLibrary alle opzioni usate per compilare, collegare ed eseguire il debug nella piattaforma di destinazione iOS. Per dettagli sull'opzione della riga di comando del compilatore, aprire la pagina **Pagine delle proprietà** per il progetto MyOpenGLESApp.iOS.StaticLibrary.

## <a name="customize-your-apps"></a>Personalizzare le app

È possibile modificare il codice condiviso C++ per aggiungere o modificare le funzionalità comuni. È necessario modificare le chiamate al codice condiviso nei progetti `MyOpenGLESApp.Android.NativeActivity` e `MyOpenGLESApp.iOS.Application` in modo che corrispondano. È possibile usare le macro del preprocessore per specificare le sezioni specifiche per la piattaforma nel codice comune. La macro del preprocessore `__ANDROID__` è predefinita quando viene eseguita la compilazione per Android. La macro del preprocessore `__APPLE__` è predefinita quando viene eseguita la compilazione per iOS.

Per visualizzare IntelliSense per una specifica piattaforma del progetto, scegliere il progetto nell'elenco a discesa delle funzionalità di commutazione del contesto nella barra Navigazione nella parte superiore della finestra dell'editor.

![Elenco a discesa di selezione del tipo di contesto del progetto nell'editor](../cross-platform/media/cppmdd_opengles_contextswitcher.png)

I problemi di IntelliSense nel codice usato dal progetto corrente vengono contrassegnati con una riga rossa ondulata. I problemi negli altri progetti vengono contrassegnati con una riga viola ondulata. Visual Studio non supporta l'applicazione di colori al codice o IntelliSense per i file Java o Objective-C. Tuttavia, è possibile modificare i file di origine e modificare le risorse per impostare il nome dell'applicazione, l'icona e altri dettagli relativi all'implementazione.
