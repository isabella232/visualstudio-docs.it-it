---
title: Installare Visual Studio 2019 per Mac Preview
description: Istruzioni su come installare Visual Studio 2019 per Mac Preview e i componenti aggiuntivi necessari per lo sviluppo multipiattaforma.
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: acd8f3bc4f5fefa0a0c8b273856579067fb33c6a
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54315899"
---
# <a name="install-visual-studio-2019-for-mac-preview"></a>Installare Visual Studio 2019 per Mac Preview

> [!NOTE]
> La versione di anteprima di Visual Studio 2019 per Mac è disponibile e per la prima volta può essere installata side-by-side con la versione stabile più recente di Visual Studio per Mac. Durante l'installazione verrà richiesto di aggiornare la versione di Visual Studio esistente se non è la versione stabile più recente.

## <a name="requirements-for-the-visual-studio-2019-for-mac-preview"></a>Requisiti per l'anteprima di Visual Studio 2019 per Mac

- Mac con macOS High Sierra 10.13 o versione successiva.

Per compilare app Xamarin per iOS o macOS, è anche necessario:

- Xcode 10.0 o versione successiva. È in genere consigliabile usare la versione stabile più recente.
- ID Apple. Se non si ha ancora un ID Apple, è possibile crearne uno nuovo all'indirizzo https://appleid.apple.com. L'ID Apple è necessario per installare Xcode e accedervi.

## <a name="installing-the-preview"></a>Installazione dell'anteprima

1. Scaricare il programma di installazione dell'anteprima dalla [pagina dell'anteprima di Visual Studio per Mac](https://aka.ms/vs4mac-preview).
2. Al termine del download, fare clic su **VisualStudioforMacPreviewInstaller.dmg** per montare il programma di installazione, quindi eseguirlo facendo doppio clic sul logo a forma di freccia:

    [![Fare clic sulla freccia grande per iniziare l'installazione](media/install-preview-installer-sml.png)](media/install-preview-installer.png#lightbox)

3. È possibile che venga visualizzato un avviso relativo al download dell'applicazione da Internet. Fare clic su **Apri**.
4. Attendere mentre il programma di installazione verifica il sistema:

    [![Il programma di installazione verifica i componenti installati nel sistema](media/install-preview-checking-sml.png)](media/install-preview-checking.png#lightbox)

5. Verrà visualizzato un avviso che chiede di accettare le condizioni di licenza e l'informativa sulla privacy. Seguire i collegamenti per leggerle e quindi premere **Continua** se si accettano:

    [![Seguire i collegamenti per la privacy e le condizioni, quindi continuare se si accettano](media/install-preview-privacy-sml.png)](media/install-preview-privacy.png#lightbox)

6. Verrà visualizzato l'elenco dei carichi di lavoro disponibili. Selezionare quelli da usare:

    [![Scegliere le funzionalità facoltative per i carichi di lavoro da installare](media/install-preview-selection-sml.png)](media/install-preview-selection.png#lightbox)

    Se la versione in uso di Visual Studio 2017 per Mac è precedente alla versione 7.7, verrà richiesto di approvare un aggiornamento alla versione stabile più recente (richiesta per supportare l'installazione side-by-side). Premere **Continua** per approvare l'aggiornamento:

    ![L'aggiornamento della versione stabile alla versione 7.7 è obbligatorio](media/install-preview-older-upgrade.png)

7. Dopo aver effettuato le selezioni, premere il pulsante **Installa**.
8. Il programma di installazione visualizzerà lo stato di avanzamento del download e dell'installazione di Visual Studio per Mac e dei carichi di lavoro selezionati. Potrebbe essere richiesto di immettere la password per concedere i privilegi necessari per l'installazione.
9. Usare **Visual Studio (Preview)** ogni volta che si vuole testare la versione di anteprima o tornare alla versione stabile più recente di Visual Studio per il lavoro di produzione. Le due icone sono rappresentate di seguito:

    ![Differenze tra le icone della versione stabile e di anteprima](media/install-preview-icons-sml.png)

Se si riscontrano problemi di rete durante l'installazione in un ambiente aziendale, rivedere le istruzioni per l'[installazione di Visual Studio per Mac protetto da un firewall o un proxy](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server).

Altre informazioni sulle modifiche sono disponibili nelle [note sulla versione](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-preview-relnotes).

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

1. [Using the Xamarin Android SDK Manager](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs) (Uso di Xamarin Android SDK Manager)
2. [Android SDK Emulator](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/) (Emulatore di Android SDK)
4. [Set Up Device for Development](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/) (Configurare il dispositivo per lo sviluppo)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>app .NET core, app Web ASP.NET Core, sviluppo di giochi Unity

Per altri carichi di lavoro, vedere la pagina [Carichi di lavoro](/visualstudio/mac/workloads).

## <a name="see-also"></a>Vedere anche

- [Installare Visual Studio 2017 (in Windows)](/visualstudio/install/install-visual-studio)
