---
title: Installare Visual Studio 2019 per Mac
description: Istruzioni su come installare Visual Studio 2019 per Mac e i componenti aggiuntivi necessari per lo sviluppo multipiattaforma.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: 45f9756607cbb638d1f69f77bdf8cd2ee30953c5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "75851945"
---
# <a name="install-visual-studio-2019-for-mac"></a>Installare Visual Studio 2019 per Mac

Per iniziare a sviluppare app .NET native e multipiattaforma in macOS, installare Visual Studio 2019 per Mac seguendo i passaggi indicati di seguito.

 > [!div class="button"]
 > [Download di Visual Studio per Mac](https://visualstudio.microsoft.com/vs/mac/)

## <a name="requirements"></a>Requisiti

- Mac con macOS High Sierra 10.12 o versione successiva.

Per compilare app Xamarin per iOS o macOS, è anche necessario:

- Xcode 10.0 o versione successiva. È in genere consigliabile usare la versione stabile più recente.
- ID Apple. Se non si ha ancora un ID Apple, è possibile crearne uno nuovo all'indirizzo https://appleid.apple.com. L'ID Apple è necessario per installare Xcode e accedervi.

## <a name="installation-instructions"></a>Istruzioni per l'installazione

1. Scaricare il programma di installazione dalla [pagina di download di Visual Studio per Mac](https://visualstudio.microsoft.com/vs/mac/).
2. Al termine del download, fare clic su **VisualStudioforMacInstaller.dmg** per montare il programma di installazione, quindi eseguirlo facendo doppio clic sul logo a forma di freccia:

    [![Fare clic sulla freccia grande per avviare l'installazione](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. È possibile che venga visualizzato un avviso relativo al download dell'applicazione da Internet. Fare clic su **Apri**.
4. Attendere mentre il programma di installazione verifica il sistema:

    [![Il programma di installazione verifica la presenza di componenti installati nel sistema](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Verrà visualizzato un avviso che chiede di accettare le condizioni di licenza e l'informativa sulla privacy. Seguire i collegamenti per leggerle e quindi premere **Continua** se si accettano:

    [![Segui i link alla privacy e ai termini, quindi continua se accetti](media/install-privacy.png)](media/install-privacy.png#lightbox)

6. Verrà visualizzato l'elenco dei carichi di lavoro disponibili. Selezionare i componenti da usare:

    [![Scegliere le funzionalità facoltative del carico di lavoro da installare](media/install-selection.png)](media/install-selection.png#lightbox)

   Se non si desidera installare tutte le piattaforme, usare la guida seguente per decidere quali piattaforme installare:


|Tipo di app  |Destinazione  |Selezione  |Note  |
|---------|---------|---------|---------|
|**App che utilizzano Xamarin**| Xamarin.Forms|Selezionare **Piattaforme Android** e **iOS** |Sarà necessario installare [ **Xcode**](https://developer.apple.com/xcode/) |
||Solo iOS|Seleziona la piattaforma **iOS**|Sarà necessario installare [ **Xcode**](https://developer.apple.com/xcode/)|
||Solo Android|Seleziona la piattaforma **Android**|Si noti che è necessario selezionare anche le relative dipendenze|
||Solo Mac|Selezionare la piattaforma **macOS (Cocoa)**|Sarà necessario installare [ **Xcode**](https://developer.apple.com/xcode/)|
|**Applicazioni .NET Core**|         |Selezionare la piattaforma **.NET Core.Select .NET Core** platform.|         |
|**Applicazioni Web ASP.NET Core**|         |Selezionare la piattaforma **.NET Core.Select .NET Core** platform.|         |
|**Funzioni di AzureAzure Functions**|         |Selezionare la piattaforma **.NET Core.Select .NET Core** platform.|         |
|**Sviluppo di giochi Unity multipiattaforma**|         |Non è necessario installare altre piattaforme oltre Visual Studio per Mac.No additional platforms need to be installed beyond Visual Studio for Mac.| Fare riferimento alla [guida all'installazione di Unity](/visualstudio/mac/setup-vsmac-tools-unity) per altre informazioni sull'installazione dell'estensione di Unity.|


7. Dopo aver effettuato le selezioni, premere il pulsante **Installa**.
8. Il programma di installazione visualizzerà lo stato di avanzamento del download e dell'installazione di Visual Studio per Mac e dei carichi di lavoro selezionati. Verrà richiesto di immettere la password per concedere i privilegi necessari per l'installazione.:

    [![Scegliere le funzionalità facoltative del carico di lavoro da installare](media/installation-progress.png)](media/installation-progress.png#lightbox)

9. Una volta installato, Visual Studio per Mac ti chiederà di personalizzare l'installazione effettuando l'accesso e selezionando i tasti di scelta rapida che vuoi usare:

    [![Accedere all'IDE](media/ide-tour-2019-start-signin.png)](media/ide-tour-2019-start-signin.png#lightbox)

    [![Scegliere le scelte rapide da tastiera da usare](media/ide-tour-2019-keyboard-shortcut.png)](media/ide-tour-2019-keyboard-shortcut.png#lightbox)

Se si riscontrano problemi di rete durante l'installazione in un ambiente aziendale, rivedere le istruzioni per l'[installazione di Visual Studio per Mac protetto da un firewall o un proxy](/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server).

Altre informazioni sulle modifiche sono disponibili nelle [note sulla versione](/visualstudio/releasenotes/vs2019-mac-relnotes).

> [!NOTE]
> Se si è scelto di non installare una piattaforma o uno strumento durante l'installazione originale (deselezionandolo nel passaggio 6), è necessario eseguire di nuovo il programma di installazione se si vogliono aggiungere i componenti in un secondo momento.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Installare Visual Studio per Mac protetto da un firewall o un server proxy

Per installare Visual Studio per Mac protetto da un firewall, determinati endpoint devono essere resi accessibili per consentire i download degli strumenti e degli aggiornamenti necessari per il software.

Configurare la rete per consentire l'accesso alle posizioni seguenti:

- [Endpoint di Visual Studio](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Passaggi successivi

L'installazione di Visual Studio per Mac consente di iniziare a scrivere codice per le app. Le guide seguenti vengono fornite per eseguire i passaggi successivi di scrittura e distribuzione dei progetti.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Provisioning di dispositivi](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning) (per eseguire l'applicazione nel dispositivo).

### <a name="android"></a>Android

1. [Using the Xamarin Android SDK Manager (Uso di Xamarin Android SDK Manager)](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Emulatore di Android SDK](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Configurare il dispositivo per lo sviluppo](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>app .NET core, app Web ASP.NET Core, sviluppo di giochi Unity

Per altri carichi di lavoro, vedere la pagina [Carichi di lavoro](workloads.md).

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Vedere anche

- [Installare Visual Studio (in Windows)](/visualstudio/install/install-visual-studio)
