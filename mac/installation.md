---
title: Installare Visual Studio 2019 per Mac
description: Istruzioni su come installare Visual Studio 2019 per Mac e i componenti aggiuntivi necessari per lo sviluppo multipiattaforma.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 03/04/2021
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: a8d1d17e78a0141530f984442eec07205e106857708744cd0e55e1ea033be4f7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121407584"
---
# <a name="install-visual-studio-2019-for-mac"></a>Installare Visual Studio 2019 per Mac

Per iniziare a sviluppare app .NET native e multipiattaforma in macOS, installare Visual Studio 2019 per Mac seguendo i passaggi indicati di seguito.

 > [!div class="button"]
 > [Scaricare Visual Studio per Mac](https://visualstudio.microsoft.com/vs/mac/)

## <a name="requirements"></a>Requisiti

- Mac con macOS High Sierra 10.13 o versione successiva.

Per compilare app Xamarin per iOS o macOS, è anche necessario:

- Un Mac compatibile con la versione più recente di Xcode. Vedere la documentazione dei [requisiti minimi di Apple](https://developer.apple.com/support/xcode/)
- La versione più recente di [Xcode.](https://developer.apple.com/xcode) Se il Mac non è compatibile con la versione più recente, potrebbe essere possibile usare una versione precedente di [Xcode.](https://docs.microsoft.com/xamarin/ios/troubleshooting/questions/old-version-xcode)
- ID Apple. Se non si ha ancora un ID Apple, è possibile crearne uno nuovo all'indirizzo https://appleid.apple.com. L'ID Apple è necessario per installare Xcode e accedervi.

## <a name="installation-instructions"></a>Istruzioni per l'installazione

1. Scaricare il programma di installazione dalla [pagina di download di Visual Studio per Mac](https://visualstudio.microsoft.com/vs/mac/).
2. Al termine del download, fare clic su **VisualStudioforMacInstaller.dmg** per montare il programma di installazione, quindi eseguirlo facendo doppio clic sul logo a forma di freccia:

    [![Fare clic sulla freccia grande per avviare l'installazione](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. È possibile che venga visualizzato un avviso relativo al download dell'applicazione da Internet. Fare clic su **Apri**.
4. Attendere mentre il programma di installazione verifica il sistema:

    [![Il programma di installazione verifica la presenza di componenti installati nel sistema](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Verrà visualizzato un avviso che chiede di accettare le condizioni di licenza e l'informativa sulla privacy. Seguire i collegamenti per leggerle e quindi premere **Continua** se si accettano:

    [![Seguire i collegamenti alla privacy e alle condizioni, quindi continuare se si accetta](media/install-privacy.png)](media/install-privacy.png#lightbox)

6. Verrà visualizzato l'elenco dei carichi di lavoro disponibili. Selezionare i componenti da usare:

    [![Screenshot della schermata "Cosa si vuole installare?" nel programma di installazione di Visual Studio Mac, che mostra un elenco di componenti disponibili per l'installazione.](media/install-selection.png)](media/install-selection.png#lightbox)

   Se non si desidera installare tutte le piattaforme, usare la guida seguente per decidere quali piattaforme installare:

   |Tipo di app  |Destinazione  |Selezione  |Note  |
   |---------|---------|---------|---------|
   |**App che usano Xamarin**| Xamarin.Forms|Selezionare **le piattaforme Android** e **iOS** |È necessario installare [ **Xcode**](https://developer.apple.com/xcode/) |
   ||Solo iOS|Selezionare **la piattaforma iOS**|È necessario installare [ **Xcode**](https://developer.apple.com/xcode/)|
   ||Solo Android|Selezionare **la piattaforma Android**|Si noti che è necessario selezionare anche le dipendenze pertinenti|
   ||Solo Mac|Selezionare **la piattaforma macOS (Cocoa)**|È necessario installare [ **Xcode**](https://developer.apple.com/xcode/)|
   |**Applicazioni .NET Core**|         |Selezionare **Piattaforma .NET Core.**|         |
   |**Applicazioni Web ASP.NET Core**|         |Selezionare **Piattaforma .NET Core.**|         |
   |**Funzioni di Azure**|         |Selezionare **Piattaforma .NET Core.**|         |
   |**Sviluppo di giochi Unity multipiattaforma**|         |Non è necessario installare piattaforme aggiuntive oltre Visual Studio per Mac.| Fare riferimento alla [guida all'installazione di Unity](./setup-vsmac-tools-unity.md) per altre informazioni sull'installazione dell'estensione di Unity.|

7. Dopo aver effettuato le selezioni, premere il pulsante **Installa**.
8. Il programma di installazione visualizzerà lo stato di avanzamento del download e dell'installazione di Visual Studio per Mac e dei carichi di lavoro selezionati. Verrà richiesto di immettere la password per concedere i privilegi necessari per l'installazione:

    [![Screenshot del programma di installazione Visual Studio Mac che mostra una schermata di stato dell'installazione per .NET Developer Toolkit per Mac.](media/installation-progress.png)](media/installation-progress.png#lightbox)

9. Dopo l'Visual Studio per Mac, verrà richiesto di personalizzare l'installazione accedendo e selezionando i tasti di scelta che si desidera usare:

    [![Accedere all'IDE](media/ide-tour-2019-start-signin.png)](media/ide-tour-2019-start-signin.png#lightbox)

    [![Scegliere i tasti di scelta rapida da usare](media/ide-tour-2019-keyboard-shortcut.png)](media/ide-tour-2019-keyboard-shortcut.png#lightbox)

Se si riscontrano problemi di rete durante l'installazione in un ambiente aziendale, rivedere le istruzioni per l'[installazione di Visual Studio per Mac protetto da un firewall o un proxy](#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server).

Altre informazioni sulle modifiche sono disponibili nelle [note sulla versione](/visualstudio/releasenotes/vs2019-mac-relnotes).

> [!NOTE]
> Se si è scelto di non installare una piattaforma o uno strumento durante l'installazione originale (deselezionandolo nel passaggio 6), è necessario eseguire di nuovo il programma di installazione se si vogliono aggiungere i componenti in un secondo momento.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Installare Visual Studio per Mac protetto da un firewall o un server proxy

Per installare Visual Studio per Mac protetto da un firewall, determinati endpoint devono essere resi accessibili per consentire i download degli strumenti e degli aggiornamenti necessari per il software.

Configurare la rete per consentire l'accesso alle posizioni seguenti:

- [Endpoint di Visual Studio](./install-behind-a-firewall-or-proxy-server.md)

## <a name="next-steps"></a>Passaggi successivi

L'installazione di Visual Studio per Mac consente di iniziare a scrivere codice per le app. Le guide seguenti vengono fornite per eseguire i passaggi successivi di scrittura e distribuzione dei progetti.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://docs.microsoft.com//xamarin/ios/get-started/hello-ios/)
2. [Provisioning di dispositivi](https://docs.microsoft.com/xamarin/ios/get-started/installation/device-provisioning/) (per eseguire l'applicazione nel dispositivo).

### <a name="android"></a>Android

1. [Hello, Android](https://docs.microsoft.com/xamarin/android/get-started/hello-android/)
2. [Using the Xamarin Android SDK Manager (Uso di Xamarin Android SDK Manager)](https://docs.microsoft.com/xamarin/android/get-started/installation/android-sdk?tabs=macos)
3. [Emulatore di Android SDK](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/)
4. [Set Up Device for Development (Configurare il dispositivo per lo sviluppo)](https://docs.microsoft.com/xamarin/android/get-started/installation/set-up-device-for-development)

### <a name="xamarinforms"></a>Xamarin.Forms

Creare applicazioni multipiattaforma native con Xamarin.Forms:

1. [Guide introduttive di Xamarin.Forms](https://docs.microsoft.com/xamarin/get-started/quickstarts/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>app .NET core, app Web ASP.NET Core, sviluppo di giochi Unity

Per altri carichi di lavoro, vedere la pagina [Carichi di lavoro](workloads.md).

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Vedi anche

- [Installare Visual Studio (in Windows)](/visualstudio/install/install-visual-studio)
