---
title: Inserimento di un pacchetto NuGet nel progetto
description: Questo documento illustra come includere un pacchetto NuGet in un progetto usando Visual Studio per Mac. Illustra in modo dettagliato come trovare e scaricare un pacchetto e offre un'introduzione alle funzionalità di integrazione dell'IDE.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/18/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 55b4691a7adb03d4ee8fd5e05e7bd9d7daa28f13
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71213695"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Installare e gestire i pacchetti NuGet in Visual Studio per Mac

L'interfaccia utente di gestione pacchetti NuGet in Visual Studio per Mac consente di installare, disinstallare e aggiornare facilmente i pacchetti NuGet in progetti e soluzioni. È possibile cercare e aggiungere pacchetti ai progetti .NET Core, ASP.NET Core e Novell.

Questo articolo descrive come includere un pacchetto NuGet in un progetto e illustra la catena di strumenti che rende facile il processo.

Per un'introduzione all'uso di NuGet in Visual Studio per Mac, [vedere Guida introduttiva: Installare e usare un pacchetto in Visual Studio per Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>Trovare e installare un pacchetto

1. Con un progetto aperto in Visual Studio per Mac, fare clic con il pulsante destro del mouse sulla cartella **dipendenze** (cartella**pacchetti** se si usa un progetto Novell) nel **riquadro della soluzione** e selezionare **Gestisci pacchetti NuGet...** .

    ![Azione di contesto di aggiunta di un nuovo pacchetto NuGet](media/nuget-walkthrough-packages-menu.png)

2. Verrà avviata la finestra **Gestisci pacchetti NuGet** . Verificare che l'elenco a discesa di origine nell'angolo superiore sinistro della finestra di dialogo sia impostato `nuget.org`su.

    ![Elenco di pacchetti NuGet](media/nuget-walkthrough-add-packages1.png)

3. Usare la casella di ricerca nell'angolo superiore destro per trovare un pacchetto specifico, ad esempio `EntityFramework`. Dopo aver trovato un pacchetto da usare, selezionarlo e fare clic sul pulsante **Aggiungi pacchetto** per avviare l'installazione.

    ![Aggiungere il pacchetto NuGet EntityFramework](media/nuget-walkthrough-add-packages2.png)

4. Dopo essere stato scaricato, il pacchetto verrà aggiunto al progetto. La soluzione cambierà a seconda del tipo di progetto che si sta modificando:

    **Progetti Novell**
    * Il nodo **Riferimenti** conterrà un elenco di tutti gli assembly che fanno parte di un pacchetto NuGet.
    * Il nodo **Pacchetti** mostra ogni pacchetto NuGet scaricato. È possibile aggiornare o rimuovere un pacchetto dall'elenco.
    
    **Progetti .NET Core**

    * Il nodo **dipendenze > NuGet** Visualizza ogni pacchetto NuGet scaricato. È possibile aggiornare o rimuovere un pacchetto dall'elenco.

## <a name="using-nuget-packages"></a>Uso di pacchetti NuGet

Dopo che il pacchetto NuGet è stato aggiunto e i riferimenti del progetto sono stati aggiornati, è possibile programmare usando le API come si farebbe con qualsiasi riferimento del progetto.

Assicurarsi di aggiungere le direttive `using` necessarie all'inizio del file:

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Aggiornamento di pacchetti

Gli aggiornamenti dei pacchetti possono essere eseguiti contemporaneamente, facendo clic con il pulsante destro del mouse sul nodo **dipendenze** (nodo**pacchetti** per progetti Novell) o singolarmente in ogni pacchetto. Quando è disponibile una nuova versione di un pacchetto NuGet, viene visualizzata ![un'icona di aggiornamento con il cerchio.](media/nuget-walkthrough-update-icon.png)

Fare clic con il pulsante destro del mouse su **dipendenze** per accedere al menu di scelta rapida e scegliere **Aggiorna** per aggiornare tutti i pacchetti:

![Menu Pacchetti](media/nuget-walkthrough-packages-menu-update.png)

* **Gestisci pacchetti NuGet** : apre la finestra per aggiungere altri pacchetti al progetto.
* **Aggiorna** - Controlla il server di origine per ogni pacchetto e scarica le eventuali versioni più recenti.
* **Ripristina** - Scarica tutti i pacchetti mancanti (senza aggiornare i pacchetti esistenti alle versioni più recenti).

Le opzioni Aggiorna e Ripristina sono disponibili anche a livello di soluzione e influiscono su tutti i progetti nella soluzione.

Dal riquadro della soluzione è possibile visualizzare la versione di un pacchetto attualmente installata e fare clic con il pulsante destro del mouse sul pacchetto da aggiornare.

![Menu pacchetti con le opzioni per aggiornare, rimuovere, aggiornare](media/nuget-walkthrough-PackageMenu.png)

Verrà visualizzata anche una notifica accanto al nome del pacchetto quando sarà disponibile una nuova versione di un pacchetto, quindi è possibile decidere se è necessario aggiornarla.

![Notifica visualizzata quando è disponibile una nuova versione del pacchetto](media/nuget-walkthrough-package-update-available.png)

Nel menu visualizzato sono disponibili due opzioni:

* **Aggiorna** - Controlla il server di origine e scarica una versione più recente, se disponibile.
* **Rimuovi** - Rimuove il pacchetto dal progetto e gli assembly correlati dai riferimenti del progetto.

## <a name="adding-package-sources"></a>Aggiunta di origini dei pacchetti

I pacchetti disponibili per l'installazione vengono recuperati inizialmente da nuget.org. È tuttavia possibile aggiungere in Visual Studio per Mac altri percorsi dei pacchetti. Ciò può essere utile per testare i pacchetti NuGet in fase di sviluppo oppure per usare un server NuGet privato all'interno dell'azienda o dell'organizzazione.

In Visual Studio per Mac passare a **Visual Studio > Preferenze > NuGet > Origini** per visualizzare e modificare l'elenco di origini dei pacchetti. Si noti che le origini possono essere un server remoto (specificato da un URL) o una directory locale.

![Origini dei pacchetti](media/nuget-walkthrough-PackageSource.png)

Fare clic su **Aggiungi** per configurare una nuova origine. Immettere un nome descrittivo e l'URL (o il percorso file) dell'origine del pacchetto. Se l'origine è un server Web sicuro, immettere nome utente e password, in caso contrario lasciare vuote queste voci:

![Aggiungere origini dei pacchetti](media/nuget-walkthrough-PackageSource2.png)

Quando si cercano i pacchetti è quindi possibile selezionare origini diverse:

![Aggiungere origini dei pacchetti](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Controllo della versione

La documentazione di NuGet illustra come [usare NuGet senza eseguire il commit di pacchetti nel controllo del codice sorgente](/nuget/consume-packages/packages-and-source-control). Se si preferisce non archiviare i file binari e le informazioni non usate nel controllo del codice sorgente, è possibile configurare Visual Studio per Mac per il ripristino automatico dei pacchetti dal server. Ciò significa che quando uno sviluppatore recupera il progetto dal controllo del codice sorgente per la prima volta, Visual Studio per Mac scarica e installa automaticamente i pacchetti richiesti.

![Ripristino automatico dei pacchetti](media/nuget-walkthrough-AutoRestore.png)

Vedere la documentazione relativa al controllo del codice sorgente specifico per informazioni dettagliate su come escludere la directory `packages` dal controllo.

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Vedere anche

* [Installare e usare un pacchetto in Visual Studio (in Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
