---
title: Installare una versione di anteprima
description: Istruzioni per l'aggiornamento di Visual Studio per Mac e l'accesso alle versioni di anteprima, incluse quelle di Visual Studio 2019 per Mac.
zone_pivot_groups: mac-ide-version
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 0E1EF257-9DE4-4653-9DF4-805CE007A1A1
ms.openlocfilehash: b5eea8c2c894b7eeaa13c83ae6698d1297de9297
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896757"
---
# <a name="install-a-preview-release"></a>Installare una versione di anteprima

::: zone pivot="vsmac2019"

> [!TIP]
> L'anteprima di Visual Studio 2019 per Mac è ora disponibile e per la prima volta può essere installata side-by-side con la versione stabile più recente di Visual Studio per Mac.

## <a name="requirements-for-the-visual-studio-2019-for-mac-preview"></a>Requisiti per l'anteprima di Visual Studio 2019 per Mac

* Mac con macOS High Sierra 10.13 o versione successiva.

Per compilare app Xamarin per iOS o macOS, è anche necessario:

* Xcode 10.0 o versione successiva. È in genere consigliabile usare la versione stabile più recente.
* ID Apple. Se non si ha ancora un ID Apple, è possibile crearne uno nuovo all'indirizzo https://appleid.apple.com. L'ID Apple è necessario per installare Xcode e accedervi.

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

    Se la versione in uso di Visual Studio per Mac 2017 è precedente alla versione 7.7, verrà richiesto di approvare un aggiornamento alla versione stabile più recente (richiesta per supportare l'installazione side-by-side). Premere **Continua** per approvare l'aggiornamento:

    ![L'aggiornamento della versione stabile alla versione 7.7 è obbligatorio](media/install-preview-older-upgrade.png)

7. Dopo aver effettuato le selezioni, premere il pulsante **Installa**.
8. Il programma di installazione visualizzerà lo stato di avanzamento del download e dell'installazione di Visual Studio per Mac e dei carichi di lavoro selezionati. Potrebbe essere richiesto di immettere la password per concedere i privilegi necessari per l'installazione.
9. Usare **Visual Studio (Preview)** ogni volta che si vuole testare la versione di anteprima o tornare alla versione stabile più recente di Visual Studio per il lavoro di produzione. Le due icone sono rappresentate di seguito:

    ![Differenze tra le icone della versione stabile e di anteprima](media/install-preview-icons-sml.png)

Se si riscontrano problemi di rete durante l'installazione in un ambiente aziendale, rivedere le istruzioni per l'[installazione di Visual Studio per Mac protetto da un firewall o un proxy](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server).

Altre informazioni sulle modifiche sono disponibili nelle [note sulla versione](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-preview-relnotes).

::: zone-end
::: zone pivot="vsmac2017"

## <a name="install-an-update-for-visual-studio-2017-for-mac"></a>Installare un aggiornamento per Visual Studio 2017 per Mac

Prima del rilascio ufficiale di una nuova versione di Visual Studio per Mac, viene rilasciata un'anteprima. La versione di anteprima offre la possibilità di provare le nuove funzionalità e ricevere le correzioni dei bug più recenti prima che vengano completamente incorporati nel prodotto.

Le versioni di anteprima di Visual Studio per Mac vengono distribuite come aggiornamento anziché con un download separato. In Visual Studio per Mac sono presenti tre canali dello strumento di aggiornamento, come descritto nell'articolo sull'[aggiornamento](update.md): Stabile, Beta e Alfa.

La maggior parte delle versioni di anteprima sono disponibili attraverso i canali **Beta** e **Alfa**, ma consultare sempre le [Note sulla versione di anteprima](/visualstudio/releasenotes/vs2017-mac-preview-relnotes) per avere informazioni più precise.

Per installare l'anteprima di Visual Studio per Mac, usare la procedura seguente:

1. Accedere a **Visual Studio > Controlla la disponibilità di aggiornamenti**.
2. Nella casella combinata Canale di aggiornamento selezionare **Beta**.
3. Selezionare il pulsante **Switch channel** (Cambia canale) per attivare il canale selezionato e avviare il download dei nuovi aggiornamenti.
4. Per avviare l'installazione degli aggiornamenti, selezionare il pulsante **Riavvia e installa aggiornamenti**.

Per altre informazioni sull'aggiornamento in Visual Studio per Mac, vedere l'articolo relativo all'[aggiornamento](update.md).

::: zone-end