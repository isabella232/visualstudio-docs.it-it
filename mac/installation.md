---
title: Installare Visual Studio 2019 per Mac
description: Istruzioni su come installare Visual Studio 2019 per Mac e i componenti aggiuntivi necessari per lo sviluppo multipiattaforma.
author: asb3993
ms.author: amburns
ms.date: 09/18/2019
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: 3e4a41567b02807dce280426daf59e30ed1876eb
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211453"
---
# <a name="install-visual-studio-2019-for-mac"></a>Installare Visual Studio 2019 per Mac

Per iniziare a sviluppare app .NET native e multipiattaforma in macOS, installare Visual Studio 2019 per Mac seguendo i passaggi indicati di seguito.

 > [!div class="button"]
 > [Download di Visual Studio per Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=navigation+cta&utm_content=download+vsmac2019)

## <a name="requirements"></a>Requisiti

- Mac con macOS High Sierra 10.12 o versione successiva.

Per compilare app Xamarin per iOS o macOS, è anche necessario:

- Xcode 10.0 o versione successiva. È in genere consigliabile usare la versione stabile più recente.
- ID Apple. Se non si ha ancora un ID Apple, è possibile crearne uno nuovo all'indirizzo https://appleid.apple.com. L'ID Apple è necessario per installare Xcode e accedervi.

## <a name="installation-instructions"></a>Istruzioni di installazione

1. Scaricare il programma di installazione dalla [pagina di download di Visual Studio per Mac](https://aka.ms/vsmac).
2. Al termine del download, fare clic su **VisualStudioforMacInstaller.dmg** per montare il programma di installazione, quindi eseguirlo facendo doppio clic sul logo a forma di freccia:

    [![Fare clic sulla freccia grande per iniziare l'installazione](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. È possibile che venga visualizzato un avviso relativo al download dell'applicazione da Internet. Fare clic su **Apri**.
4. Attendere mentre il programma di installazione verifica il sistema:

    [![Il programma di installazione verifica i componenti installati nel sistema](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Verrà visualizzato un avviso che chiede di accettare le condizioni di licenza e l'informativa sulla privacy. Seguire i collegamenti per leggerle e quindi premere **Continua** se si accettano:

    [![Seguire i collegamenti per la privacy e le condizioni, quindi continuare se si accettano](media/install-privacy.png)](media/install-privacy.png#lightbox)

6. Verrà visualizzato l'elenco dei carichi di lavoro disponibili. Selezionare i componenti da usare:

    [![Scegliere le funzionalità facoltative per i carichi di lavoro da installare](media/install-selection.png)](media/install-selection.png#lightbox)

   Se non si desidera installare tutte le piattaforme, usare la guida seguente per decidere quali piattaforme installare:


|Tipo di app  |destinazione  |Selection  |Note  |
|---------|---------|---------|---------|
|**App che usano Novell**| Xamarin.Forms|Selezionare le piattaforme **Android** e **iOS** |È necessario installare [ **Xcode**](https://developer.apple.com/xcode/) |
||solo iOS|Selezionare la piattaforma **iOS**|È necessario installare [ **Xcode**](https://developer.apple.com/xcode/)|
||Solo Android|Seleziona piattaforma **Android**|Si noti che è necessario selezionare anche le dipendenze rilevanti|
||Solo Mac|Seleziona piattaforma **MacOS (Cocoa)**|È necessario installare [ **Xcode**](https://developer.apple.com/xcode/)|
|**Applicazioni .NET Core**|         |Selezionare piattaforma **.NET Core** .|         |
|**Applicazioni Web ASP.NET Core**|         |Selezionare piattaforma **.NET Core** .|         |
|**Funzioni di Azure**|         |Selezionare piattaforma **.NET Core** .|         |
|**Sviluppo di Giochi Unity multipiattaforma**|         |Non è necessario installare altre piattaforme oltre Visual Studio per Mac.| Fare riferimento alla [guida all'installazione di Unity](/visualstudio/mac/setup-vsmac-tools-unity) per altre informazioni sull'installazione dell'estensione di Unity.|


7. Dopo aver effettuato le selezioni, premere il pulsante **Installa**.
8. Il programma di installazione visualizzerà lo stato di avanzamento del download e dell'installazione di Visual Studio per Mac e dei carichi di lavoro selezionati. Verrà richiesto di immettere la password per concedere i privilegi necessari per l'installazione:

    [![Scegliere le funzionalità facoltative per i carichi di lavoro da installare](media/installation-progress.png)](media/installation-progress.png#lightbox)

9. Una volta installato, Visual Studio per Mac chiederà di personalizzare l'installazione effettuando l'accesso e selezionando i tasti di scelta rapida che si vuole usare:

    [![Accedere all'IDE](media/ide-tour-2019-start-signin.png)](media/ide-tour-2019-start-signin.png#lightbox)

    [![Scegliere i tasti di scelta rapida da usare](media/ide-tour-2019-keyboard-shortcut.png)](media/ide-tour-2019-keyboard-shortcut.png#lightbox)

Se si riscontrano problemi di rete durante l'installazione in un ambiente aziendale, rivedere le istruzioni per l'[installazione di Visual Studio per Mac protetto da un firewall o un proxy](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server).

Altre informazioni sulle modifiche sono disponibili nelle [note sulla versione](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-relnotes).

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

1. [Using the Xamarin Android SDK Manager](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs) (Uso di Xamarin Android SDK Manager)
2. [Android SDK Emulator](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/) (Emulatore di Android SDK)
4. [Set Up Device for Development](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/) (Configurare il dispositivo per lo sviluppo)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>app .NET core, app Web ASP.NET Core, sviluppo di giochi Unity

Per altri carichi di lavoro, vedere la pagina [Carichi di lavoro](workloads.md).

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Vedere anche

- [Installare Visual Studio (in Windows)](/visualstudio/install/install-visual-studio)
