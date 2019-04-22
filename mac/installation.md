---
title: Installare Visual Studio 2019 per Mac
description: Istruzioni su come installare Visual Studio 2019 per Mac e i componenti aggiuntivi necessari per lo sviluppo multipiattaforma.
author: conceptdev
ms.author: crdun
ms.date: 04/02/2019
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: 52f9e5f5d21fe69cde613d8e05b365fc8d795dd8
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857320"
---
# <a name="install-visual-studio-2019-for-mac"></a>Installare Visual Studio 2019 per Mac

Per iniziare a sviluppare app .NET native e multipiattaforma in macOS, installare Visual Studio 2019 per Mac seguendo i passaggi indicati di seguito.

## <a name="requirements"></a>Requisiti

- Mac con macOS High Sierra 10.12 o versione successiva.

Per compilare app Xamarin per iOS o macOS, è anche necessario:

- Xcode 11.0 o versione successiva. È in genere consigliabile usare la versione stabile più recente.
- ID Apple. Se non si ha ancora un ID Apple, è possibile crearne uno nuovo all'indirizzo https://appleid.apple.com. L'ID Apple è necessario per installare Xcode e accedervi.

## <a name="installation-instructions"></a>Istruzioni di installazione

1. Scaricare il programma di installazione dalla [pagina di download di Visual Studio per Mac](https://aka.ms/vsmac).
2. Al termine del download, fare clic su **VisualStudioforMacInstaller.dmg** per montare il programma di installazione, quindi eseguirlo facendo doppio clic sul logo a forma di freccia:

    [![CFare clic sulla freccia grande per iniziare l'installazione(media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. È possibile che venga visualizzato un avviso relativo al download dell'applicazione da Internet. Fare clic su **Apri**.
4. Attendere mentre il programma di installazione verifica il sistema:

    [![TIl programma di installazione verifica i componenti installati nel sistema(media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Verrà visualizzato un avviso che chiede di accettare le condizioni di licenza e l'informativa sulla privacy. Seguire i collegamenti per leggerle e quindi premere **Continua** se si accettano:

    [![FSeguire i collegamenti per la privacy e le condizioni, quindi continuare se si accettano(media/install-privacy-sml.png)](media/install-privacy.png#lightbox)

6. Verrà visualizzato l'elenco dei carichi di lavoro disponibili. Selezionare quelli da usare:

    [![CScegliere le funzionalità facoltative per i carichi di lavoro da installare(media/install-selection-sml.png)](media/install-selection.png#lightbox)

7. Dopo aver effettuato le selezioni, premere il pulsante **Installa**.
8. Il programma di installazione visualizzerà lo stato di avanzamento del download e dell'installazione di Visual Studio per Mac e dei carichi di lavoro selezionati. Potrebbe essere richiesto di immettere la password per concedere i privilegi necessari per l'installazione.

Se si riscontrano problemi di rete durante l'installazione in un ambiente aziendale, rivedere le istruzioni per l'[installazione di Visual Studio per Mac protetto da un firewall o un proxy](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server).

Altre informazioni sulle modifiche sono disponibili nelle [note sulla versione](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-relnotes).

> [!NOTE]
> Se si è scelto di non installare una piattaforma o uno strumento durante l'installazione originale (deselezionandolo nel passaggio 6), è necessario eseguire di nuovo il programma di installazione se si vuole aggiungere i componenti in un secondo momento.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Installare Visual Studio per Mac protetto da un firewall o un server proxy

Per installare Visual Studio per Mac protetto da un firewall, determinati endpoint devono essere resi accessibili per consentire i download degli strumenti e degli aggiornamenti necessari per il software.

Configurare la rete per consentire l'accesso alle posizioni seguenti:

- [Endpoint di Visual Studio](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Passaggi successivi

L'installazione di Visual Studio per Mac consente di iniziare a scrivere codice per le app. Le guide seguenti vengono fornite per eseguire i passaggi successivi di scrittura e distribuzione dei progetti.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Provisioning di dispositivi](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning) (per eseguire l'applicazione nel dispositivo).

### <a name="android"></a>Android

1. [Using the Xamarin Android SDK Manager (Uso di Xamarin Android SDK Manager)](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Emulatore di Android SDK](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Set Up Device for Development (Configurare il dispositivo per lo sviluppo)](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>app .NET core, app Web ASP.NET Core, sviluppo di giochi Unity

Per altri carichi di lavoro, vedere la pagina [Carichi di lavoro](/visualstudio/mac/workloads).

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Vedere anche

- [Installare Visual Studio (in Windows)](/visualstudio/install/install-visual-studio)
