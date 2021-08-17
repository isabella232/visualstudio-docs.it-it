---
title: Inserimento di un pacchetto NuGet nel progetto
description: Questo documento illustra come includere un pacchetto NuGet in un progetto usando Visual Studio per Mac. Illustra in modo dettagliato come trovare e scaricare un pacchetto e offre un'introduzione alle funzionalità di integrazione dell'IDE.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 199644f6df8edf2a23681525ffd88917fe2099cd2ee1f1cd44500a574da1c76e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121439144"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Installare e gestire NuGet pacchetti in Visual Studio per Mac

L NuGet Gestione pacchetti'interfaccia utente di Visual Studio per Mac consente di installare, disinstallare e aggiornare facilmente i NuGet in progetti e soluzioni. È possibile cercare e aggiungere pacchetti ai progetti .NET Core, ASP.NET Core e Xamarin.

Questo articolo descrive come includere un pacchetto NuGet in un progetto e illustra la catena di strumenti che rende facile il processo.

Per un'introduzione all'NuGet in Visual Studio per Mac, vedere [Guida introduttiva: Installare](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac) e usare un pacchetto in Visual Studio per Mac

## <a name="find-and-install-a-package"></a>Trovare e installare un pacchetto

1. Con un progetto aperto in Visual Studio per Mac, fare  clic con il pulsante destro del mouse sulla  cartella Dipendenze **(cartella** Pacchetti se si usa un progetto Xamarin) nella finestra della soluzione e scegliere Gestisci pacchetti **NuGet...**.

    ![Azione di contesto di aggiunta di un nuovo pacchetto NuGet](media/nuget-walkthrough-packages-menu.png)

2. Verrà visualizzata la **finestra Gestisci NuGet pacchetti.** Assicurarsi che l'elenco a discesa Origine nell'angolo superiore sinistro della finestra di dialogo sia impostato su , in modo da eseguire la ricerca nel repository centrale `nuget.org` NuGet pacchetti.

    ![Elenco di pacchetti NuGet](media/nuget-walkthrough-add-packages1.png)

3. Usare la casella di ricerca nell'angolo superiore destro per trovare un pacchetto specifico, ad esempio `EntityFramework`. Dopo aver trovato un pacchetto da usare, selezionarlo e fare clic sul pulsante **Aggiungi pacchetto** per avviare l'installazione.

    ![Aggiungere il pacchetto di NuGet EntityFramework](media/nuget-walkthrough-add-packages2.png)

4. Dopo essere stato scaricato, il pacchetto verrà aggiunto al progetto. La soluzione cambierà a seconda del tipo di progetto che si sta modificando:

    **Progetti Xamarin**
    * Il nodo **Riferimenti** conterrà un elenco di tutti gli assembly che fanno parte di un pacchetto NuGet.
    * Il nodo **Pacchetti** mostra ogni pacchetto NuGet scaricato. È possibile aggiornare o rimuovere un pacchetto dall'elenco.
    
    **Progetti .NET Core**

    * Il **nodo > NuGet** dipendenze visualizza NuGet pacchetto scaricato. È possibile aggiornare o rimuovere un pacchetto dall'elenco.

## <a name="using-nuget-packages"></a>Uso di pacchetti NuGet

Dopo che il pacchetto NuGet è stato aggiunto e i riferimenti del progetto sono stati aggiornati, è possibile programmare usando le API come si farebbe con qualsiasi riferimento del progetto.

Assicurarsi di aggiungere le direttive `using` necessarie all'inizio del file:

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Aggiornamento dei pacchetti

È possibile eseguire tutti gli aggiornamenti dei pacchetti  contemporaneamente facendo clic con il pulsante destro del mouse sul nodo Dipendenze **(nodo** Pacchetti per i progetti Xamarin) o singolarmente in ogni pacchetto. Quando è disponibile una nuova versione di NuGet pacchetto, viene visualizzata un'icona di aggiornamento freccia ![ su con cerchio ](media/nuget-walkthrough-update-icon.png) .

Fare clic con il pulsante destro **del mouse su Dipendenze** per accedere al menu di scelta rapida **e scegliere Aggiorna** per aggiornare tutti i pacchetti:

![Menu di scelta rapida Dipendenze con il menu Aggiorna evidenziato](media/nuget-walkthrough-packages-menu-update.png)

* **Gestisci NuGet pacchetti:** apre la finestra per aggiungere altri pacchetti al progetto.
* **Aggiorna** - Controlla il server di origine per ogni pacchetto e scarica le eventuali versioni più recenti.
* **Ripristina** - Scarica tutti i pacchetti mancanti (senza aggiornare i pacchetti esistenti alle versioni più recenti).

Le opzioni Aggiorna e Ripristina sono disponibili anche a livello di soluzione e influiscono su tutti i progetti nella soluzione.

### <a name="updating-to-pre-release-versions-of-packages"></a>Aggiornamento alle versioni non definitiva dei pacchetti
Per eseguire l'aggiornamento a una versione **non definitiva** più  recente di un pacchetto, è possibile fare clic con il pulsante destro del mouse su Dipendenze per aprire il menu di scelta rapida e scegliere il menu Gestisci NuGet pacchetti.

![Menu di scelta rapida Dipendenze con Gestisci NuGet distribuzione... menu evidenziato](media/nuget-walkthrough-packages-menu-manage-nuget-packages.png)

Selezionare la **casella di controllo Mostra pacchetti di versioni non** definitiva nella parte inferiore della finestra di dialogo.

![Finestra NuGet gestione pacchetti aperta con l'opzione "Mostra pacchetti in versione non definitiva" selezionata](media/nuget-walkthrough-show-pre-release-packages.png)

Infine, nella scheda **Aggiornamenti** della finestra di dialogo selezionare il pacchetto che si  vuole aggiornare e scegliere la nuova versione non definitiva dall'elenco a discesa Nuova versione e fare clic su **Aggiorna pacchetto**.

![Finestra NuGet gestione pacchetti aperta nella scheda Installati, con un pacchetto selezionato e l'elenco a discesa Nuova versione aperto.](media/nuget-walkthrough-packages-nuget-dialog-update-installed-package.png)

### <a name="locating-outdated-packages"></a>Individuazione di pacchetti obsoleti
Nella finestra della soluzione è possibile visualizzare la versione di un pacchetto attualmente installata e fare clic con il pulsante destro del mouse sul pacchetto da aggiornare.

![Menu Pacchetti con le opzioni Aggiorna, Rimuovi, Aggiorna](media/nuget-walkthrough-PackageMenu.png)

Verrà visualizzata anche una notifica accanto al nome del pacchetto quando è disponibile una nuova versione di un pacchetto, pertanto è possibile decidere se è possibile aggiornarlo.

![Notifica visualizzata quando è disponibile una nuova versione del pacchetto](media/nuget-walkthrough-package-update-available.png)

Nel menu visualizzato sono disponibili due opzioni:

* **Aggiorna** - Controlla il server di origine e scarica una versione più recente, se disponibile.
* **Rimuovi** - Rimuove il pacchetto dal progetto e gli assembly correlati dai riferimenti del progetto.

## <a name="manage-packages-for-the-solution"></a>Gestisci i pacchetti per la soluzione

La gestione dei pacchetti per una soluzione è un metodo pratico per utilizzare più progetti contemporaneamente.

1. Fare clic con il pulsante destro del mouse sulla **soluzione e scegliere Gestisci NuGet pacchetti...**:

    ![Gestisci pacchetti NuGet per la soluzione](media/nuget-walkthrough-manage-packages-solution.png)

1. Quando si gestiscono i pacchetti per la soluzione, l'interfaccia utente consente di selezionare i progetti interessati dalle operazioni:

    ![Selettore di progetto durante la gestione dei pacchetti per la soluzione](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>Scheda Consolida

Quando si lavora in una soluzione con più progetti, è consigliabile assicurarsi che ovunque si usi lo stesso pacchetto NuGet in ogni progetto si usi anche lo stesso numero di versione del pacchetto. Visual Studio per Mac semplifica questa operazione fornendo una  scheda Consolida nell'interfaccia utente di Gestione pacchetti quando si sceglie di gestire i pacchetti per una soluzione. Questa scheda consente di vedere facilmente dove i pacchetti con numeri di versione distinti vengono usati da progetti diversi nella soluzione:

![Scheda Consolida dell'interfaccia utente di Gestione pacchetti](media/nuget-walkthrough-consolidate-tab.png)

In questo esempio il progetto NuGetDemo usa Microsoft.EntityFrameworkCore 2.20, mentre NuGetDemo.Shared usa Microsoft.EntityFrameworkCore 2.2.6. Per consolidare le versioni dei pacchetti, seguire questa procedura:

- Selezionare i progetti da aggiornare nell'elenco dei progetti.
- Selezionare la versione da usare in tutti i progetti nell'elenco **Nuova** versione, ad esempio Microsoft.EntityFrameworkCore 3.0.0.
- Selezionare il **pulsante Consolida** pacchetto.

Gestione pacchetti installa la versione del pacchetto selezionata in tutti i progetti selezionati e in seguito il pacchetto non compare più nella scheda **Consolida**.

## <a name="adding-package-sources"></a>Aggiunta di origini dei pacchetti

I pacchetti disponibili per l'installazione vengono inizialmente recuperati da nuget.org. Tuttavia, è possibile aggiungere altri percorsi dei pacchetti Visual Studio per Mac. Ciò può essere utile per testare i pacchetti NuGet in fase di sviluppo oppure per usare un server NuGet privato all'interno dell'azienda o dell'organizzazione.

In Visual Studio per Mac passare a **Visual Studio > Preferenze > NuGet > Origini** per visualizzare e modificare l'elenco di origini dei pacchetti. Si noti che le origini possono essere un server remoto (specificato da un URL) o una directory locale.

![Origini dei pacchetti](media/nuget-walkthrough-PackageSource.png)

Fare clic su **Aggiungi** per configurare una nuova origine. Immettere un nome descrittivo e l'URL (o il percorso file) dell'origine del pacchetto. Se l'origine è un server Web sicuro, immettere nome utente e password, in caso contrario lasciare vuote queste voci:

![Finestra di dialogo Aggiungi origine pacchetto con un prompt per Nome, URL percorso, nome utente e password.](media/nuget-walkthrough-PackageSource2.png)

Quando si cercano i pacchetti è quindi possibile selezionare origini diverse:

![Finestra di dialogo Aggiungi origine pacchetto che mostra un elenco a discesa con un elenco di origini dei pacchetti.](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Controllo della versione

La documentazione di NuGet illustra come [usare NuGet senza eseguire il commit di pacchetti nel controllo del codice sorgente](/nuget/consume-packages/packages-and-source-control). Se si preferisce non archiviare i file binari e le informazioni non usate nel controllo del codice sorgente, è possibile configurare Visual Studio per Mac per il ripristino automatico dei pacchetti dal server. Ciò significa che quando uno sviluppatore recupera il progetto dal controllo del codice sorgente per la prima volta, Visual Studio per Mac scarica e installa automaticamente i pacchetti richiesti.

![Ripristino automatico dei pacchetti](media/nuget-walkthrough-AutoRestore.png)

Vedere la documentazione relativa al controllo del codice sorgente specifico per informazioni dettagliate su come escludere la directory `packages` dal controllo.

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Vedi anche

* [Installare e usare un pacchetto in Visual Studio (in Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
