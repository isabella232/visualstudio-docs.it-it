---
title: Creare un'app NativeActivity per Android | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 884014b1-5208-45ec-b0da-ad0070d2c24d
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: fbe0942226e44e5ca2908f7c13f34595bef34887
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58069697"
---
# <a name="create-an-android-native-activity-app"></a>Creare un'app NativeActivity di Android

Quando si installa l'opzione Visual C++ per Sviluppo app per dispositivi mobili multipiattaforma, Visual Studio 2015 può essere usato per creare app completamente funzionali NativeActivity di Android. Android Native Development Kit (NDK) è un set di strumenti che consente di implementare la maggior parte dell'app Android usando codice C/C++ puro. Alcuni codici INI di Java fungono da collante per consentire al codice C/C++ di interagire con Android. Android NDK ha introdotto una funzionalità che consente di creare app NativeActivity con l'API Android di livello 9. Il codice NativeActivity è molto usato per creare app per giochi o con un elevato contenuto grafico che usano Unreal Engine o OpenGL. Questo argomento illustra la creazione di un'app NativeActivity semplice che usa OpenGL. Gli argomenti aggiuntivi illustrano il ciclo di vita di sviluppo relativo alla modifica, la compilazione, il debug e la distribuzione del codice NativeActivity.

## <a name="requirements"></a>Requisiti

Prima di creare un'app NativeActivity di Android, verificare che tutti i requisiti di sistema siano soddisfatti e che l'opzione Visual C++ Mobile Development sia installata in Visual Studio 2015. Per altre informazioni, vedere [Install Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Verificare che gli SDK e gli strumenti di terze parti richiesti siano inclusi nell'installazione e che sia installato Microsoft Visual Studio Emulator per Android.

## <a name="create-a-new-native-activity-project"></a>Creare un nuovo progetto NativeActivity

In questa esercitazione verrà creato un nuovo progetto Native Activity di Android, poi verrà compilata ed eseguita l'app predefinita in Visual Studio Emulator for Android.

1. In Visual Studio scegliere **File** > **Nuovo** > **Progetto**.

2. Nella finestra di dialogo **Nuovo progetto**, in **Modelli**, scegliere **Visual C++** > **Multipiattaforma** e quindi scegliere il modello **Applicazione NativeActivity (Android)**.

3. Assegnare all'app un nome come `MyAndroidApp`e fare clic su **OK**.

    ![Creare un progetto NativeActivity](../cross-platform/media/cppmdd_newproject.PNG "CppMDD_NewProject")

    Visual Studio crea la nuova soluzione e apre Esplora soluzioni.

    ![Progetto NativeActivity in Esplora soluzioni](../cross-platform/media/cppmdd_rc_na_solutionexp.PNG "CPPMDD_RC_NA_SolutionExp")

   La nuova soluzione per app NativeActivity di Android include due progetti:

-   `MyAndroidApp.NativeActivity`, che contiene i riferimenti e il codice glue per l'app da eseguire come NativeActivity in Android. L'implementazione dei punti di ingresso dal codice glue si trova nel file *main.cpp*. Le intestazioni precompilate sono in *pch.h*. Questo progetto di app NativeActivity viene compilato in un file di libreria condivisa con estensione *so* che viene selezionato dal progetto Packaging.

-   `MyAndroidApp.Packaging`, che crea il file con estensione *apk* per la distribuzione nei dispositivi o negli emulatori Android. Questo progetto contiene le risorse e il file *AndroidManifest.xml* in cui sono state impostate le proprietà del manifesto. Contiene anche il file *build.xml*, che controlla il processo di compilazione Ant. Per impostazione predefinita, è impostato come progetto di avvio in modo che possa essere distribuito ed eseguito direttamente da Visual Studio.

## <a name="build-and-run-the-default-android-native-activity-app"></a>Compilare ed eseguire l'app NativeActivity predefinita per Android

Compilare ed eseguire l'app generata dal modello per verificare l'installazione e la configurazione. Per questo test iniziale, eseguire l'app in uno dei profili del dispositivo installati da Visual Studio Emulator per Android. Se si preferisce testare l'app in un'altra destinazione, è possibile caricare l'emulatore di destinazione o connettere il dispositivo al computer.

## <a name="to-build-and-run-the-default-native-activity-app"></a>Per compilare ed eseguire l'app NativeActivity predefinita

1.  Se non è ancora selezionato, scegliere **x86** dall'elenco a discesa **Piattaforme soluzione** .

     ![Selezione di x86 dal menu a discesa Piattaforme soluzione](../cross-platform/media/cppmdd_rc_na_solution_x86.png "CPPMDD_RC_NA_Solution_x86")

     Se l'elenco **Piattaforme soluzione** non è visualizzato, scegliere **Piattaforme soluzione** dall'elenco a discesa **Aggiungi o rimuovi pulsanti** e scegliere la piattaforma.

2.  Nella barra dei menu scegliere **Compila** > **Compila soluzione**.

     La finestra di output visualizza l'output del processo di compilazione per i due progetti della soluzione.

3.  Scegliere uno dei profili di VS Emulator Android Phone (x86) come destinazione della distribuzione.

     Se sono stati installati altri emulatori o è stato connesso un dispositivo Android, è possibile selezionarli nell'elenco a discesa delle destinazioni della distribuzione.

4.  Premere **F5** per avviare il debug o MAIUSC+F5 per avviare senza eseguire il debug.

     Ecco come viene visualizzata l'app predefinita in Visual Studio Emulator for Android.

     ![L'emulatore che sta eseguendo l'app](../cross-platform/media/cppmdd_emulator_running_app.PNG "CppMDD_Emulator_Running_App")

     All'avvio dell'emulatore in Visual Studio, il processo di caricamento e distribuzione del codice richiede qualche istante. Una volta avviata l'app, è possibile impostare i punti di interruzione e usare il debugger per eseguire il codice un'istruzione alla volta, esaminare le variabili locali e controllare i valori.

5.  Premere **MAIUSC**+**F5** per interrompere il debug.

     L'emulatore è un processo separato che continua a essere eseguito. È possibile modificare, compilare e distribuire il codice più volte nello stesso emulatore.