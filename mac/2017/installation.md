---
title: Installare Visual Studio 2017 per Mac
description: Istruzioni su come installare Visual Studio per Mac e i componenti aggiuntivi necessari per lo sviluppo multipiattaforma.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: b89a778b2ff1044ad788673337d7cea9fb37c8abe4620216387413f87372c1f7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121423162"
---
# <a name="install-visual-studio-2017-for-mac"></a>Installare Visual Studio 2017 per Mac

> [!NOTE]
> Visual Studio 2019 per Mac [è ora disponibile](installation.md?view=vsmac-2019&preserve-view=true). Per le versioni precedenti di Visual Studio per Mac, vedere la [pagina dei download](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac) di Visual Studio.

## <a name="downgrading-from-visual-studio-2019-for-mac"></a>Downgrade da Visual Studio 2019 per Mac

Per risultati ottimali, prima di effettuare il downgrade è necessario assicurarsi di avere [disinstallato](uninstall.md) Visual Studio 2019 per Mac. In caso di problemi che causano il download, informare Microsoft [segnalando il problema](report-a-problem.md).
 
## <a name="requirements"></a>Requisiti

Per iniziare a sviluppare app native multipiattaforma quando si scarica Visual Studio per Mac, è necessario eseguire alcune operazioni di installazione e configurazione di preparazione.

Per l'uso di iOS in Visual Studio è necessario quanto segue:

- Mac con macOS High Sierra 10.13 o versione successiva.
- Xcode 9.3 o versione successiva. È in genere consigliabile usare la versione stabile più recente.
- ID Apple. Se non si ha ancora un ID Apple, è possibile crearne uno nuovo all'indirizzo https://appleid.apple.com. L'ID Apple è necessario per installare Xcode e accedervi.

## <a name="install"></a>Installazione

1. Scaricare Visual Studio per Mac da [my.visualstudio.com](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac)

2. Dopo aver scaricato il pacchetto di installazione, fare clic sul file **VisualStudioForMacInstaller.dmg** per montare il programma di installazione e quindi eseguirlo facendo doppio clic sul logo, come illustrato nell'immagine seguente:

   ![Finestra di dialogo del programma di installazione](media/installer-image1.png)

3. Potrebbe venire visualizzata una finestra di dialogo di avviso simile a quella dell'immagine seguente. In questo caso, fare clic su **Apri**:

   ![Finestra di dialogo di avviso](media/installer-image2.png)

4. Il programma di installazione controlla il sistema per verificare quali componenti devono essere installati o aggiornati:

   ![Valutazione del sistema](media/installer-image3.png)

5. Verrà quindi visualizzata una finestra di dialogo di avviso che chiede di accettare le condizioni di licenza e privacy. Fare clic su **Continua** per accettare le condizioni:

   ![Finestra di dialogo relativa alla licenza](media/installer-image4.png)

6. Il programma di installazione visualizza un elenco dei componenti necessari che non sono presenti e che devono essere scaricati e installati. Selezionare i prodotti da scaricare:

   ![Selezionare gli elementi](media/installer-image5.png)

   Se non si desidera installare tutte le piattaforme, usare la guida seguente per decidere quali piattaforme installare:

   * **App con Xamarin**:
      - Xamarin.Forms - Selezionare le piattaforme **Android** e **iOS**.
      - Solo iOS - Selezionare la piattaforma **iOS** (si noti che sarà necessario installare [**Xcode**](https://developer.apple.com/xcode/)).
      - Solo Android - Selezionare la piattaforma **Android** (si noti che è necessario selezionare anche le dipendenze rilevanti).
      - Solo Mac - Selezionare la piattaforma **macOS** (si noti che sarà necessario installare [**Xcode**](https://developer.apple.com/xcode/)).
      - App Xamarin completamente multipiattaforma - Selezionare le piattaforme **Android**, **iOS** e **macOS**.
   * **Applicazioni .NET Core** - Selezionare la piattaforma **.NET Core**.
   * **Applicazioni Web ASP.NET Core** - Selezionare la piattaforma **.NET Core**.
   * **Sviluppo di giochi Unity multipiattaforma** - Non è necessario installare alcuna piattaforma aggiuntiva oltre a Visual Studio per Mac. Fare riferimento alla [guida all'installazione di Unity](./setup-vsmac-tools-unity.md) per altre informazioni sull'installazione dell'estensione di Unity.

   Questa schermata di installazione mostra la versione e le dimensioni di ogni singolo componente. È possibile fare clic su ogni componente per visualizzare un elenco delle relative dipendenze (per Android), visualizzare altri pacchetti scaricati (per .NET Core) o visualizzare le applicazioni aggiuntive necessarie (per iOS e macOS):

   ![Dipendenze aggiuntive di Android](media/installer-image6.png)

7. Una volta selezionate le opzioni desiderate, fare clic su **Installa e aggiorna** per avviare il processo di installazione.

8. Il programma di installazione avvia il processo di download e installazione degli elementi selezionati:

   ![Avvio dell'installazione](media/installer-image7.png)

   ![Download di Xamarin.Mac](media/installer-image8.png)

   ![Completamento dell'installazione](media/installer-image9.png)

9. Potrebbe essere necessario elevare le autorizzazioni necessarie per i singoli componenti richiesti per il completamento dell'installazione. Immettere le credenziali di amministratore in questa posizione per continuare il processo di installazione:

   ![Immettere le autorizzazioni per continuare l'installazione](media/installer-image10.png)

10. Una volta completata l'installazione, è possibile iniziare a sviluppare app in Visual Studio premendo **Avvia**:

    ![Aprire Visual Studio.](media/installer-image11.png)

> [!NOTE]
> Se si sceglie di non installare una piattaforma o uno strumento durante l'installazione originale (deselezionandolo nel passaggio 6), è necessario eseguire di nuovo il [programma di installazione](https://visualstudio.microsoft.com/vs/) se si vuole aggiungere i componenti in un secondo momento.

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

Per altri carichi di lavoro, vedere la pagina [Carichi di lavoro](./workloads.md).

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Vedi anche

- [Installare Visual Studio 2017 (in Windows)](/visualstudio/install/install-visual-studio)