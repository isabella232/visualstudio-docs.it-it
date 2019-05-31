---
title: Creare colonne del sito, tipo di contenuto ed elenco per SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 141ce92fa083a0afacdae3a279d2697e0931e3be
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401276"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Procedura dettagliata: Creare una colonna del sito, tipo di contenuto ed elenco per SharePoint
  Le procedure seguenti illustrano come creare colonne personalizzate del sito di SharePoint, oppure *campi*, oltre a un tipo di contenuto che utilizza le colonne del sito. Viene inoltre illustrato come creare un elenco che usa il nuovo tipo di contenuto.

 In questa procedura dettagliata sono incluse le attività seguenti:

- [Creare colonne del sito personalizzate](#create-custom-site-columns).

- [Creare un tipo di contenuto personalizzato](#create-a-custom-content-type).

- [Creare un elenco](#create-a-list).

- [Testare l'applicazione](#test-the-application).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Windows e SharePoint.

- [!INCLUDE[vsprvs-current](../sharepoint/includes/vsprvs-current-md.md)]

## <a name="create-custom-site-columns"></a>Creare colonne del sito personalizzate
 Questo esempio crea un elenco per la gestione dei pazienti in un ospedale. In primo luogo, è necessario creare un progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e aggiungervi le colonne del sito, come indicato di seguito.

#### <a name="to-create-the-project"></a>Per creare il progetto

1. Nel [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **File** menu, scegliere **New** > **progetto**.

2. Nel **nuovo progetto** in presenza di una finestra di dialogo **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere **2010**.

3. Nel **modelli** riquadro, scegliere **progetto SharePoint 2010**, modificare il nome del progetto in cui **Clinic**e quindi scegliere il **OK** pulsante.

     Il modello di progetto SharePoint 2010 è un progetto vuoto che viene usato in questo esempio per contenere le colonne del sito e altri elementi del progetto che vengono aggiunti in un secondo momento.

4. Nel **specificare il livello di sito e la sicurezza per il debug** pagina, immettere l'URL per il sito di SharePoint locale a cui si desidera aggiungere il nuovo elemento campo personalizzato o usare il percorso predefinito (`http://<`*NomeSistema* `>/)`.

5. Nel **qual è il livello di attendibilità per la soluzione SharePoint?** sezione, usare il valore predefinito **Distribuisci come soluzione creata mediante sandbox**.

     Per altre informazioni sulle modalità sandbox e soluzioni farm, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).

6. Scegliere il **fine** pulsante. Il progetto viene ora elencato nel **Esplora soluzioni**.

#### <a name="to-add-site-columns"></a>Per aggiungere le colonne del sito

1. Aggiungere una nuova colonna di sito. A tale scopo, in **Esplora soluzioni**, aprire il menu di scelta rapida **Clinic**, quindi scegliere **Add** > **nuovo elemento**.

2. Nel **Aggiungi nuovo elemento** finestra di dialogo, scegliere **colonna del sito**, modificare il nome in **nome Patient**e quindi scegliere il **Aggiungi** pulsante.

3. Nella colonna del sito *Elements. XML* del file, lasciare il **tipo** impostando come **testo**e modificare il **gruppo** impostando su  **Le colonne del sito clinic**. Al termine, la colonna di sito *Elements* file dovrebbe essere simile all'esempio seguente.

    ```xml
    <Field
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"
         Name="Clinic - Patient Name"
         DisplayName="Patient Name"
         Type="Text"
         Required="FALSE"
         Group="Clinic Site Columns">
    </Field>
    ```

4. Con la stessa procedura, aggiungere altre due colonne del sito per il progetto: **ID dei pazienti** (tipo = "Integer") e **Dottor nome** (tipo = "Text"). Impostare i valore di gruppo **colonne del sito Clinic**.

## <a name="create-a-custom-content-type"></a>Creare un tipo di contenuto personalizzato
 Successivamente, creare un tipo di contenuto, ovvero in base al tipo di contenuto di contatti, che include le colonne del sito che è stato creato nella procedura precedente. È possibile basare un tipo di contenuto su un tipo di contenuto esistente, per risparmiare tempo perché il tipo di contenuto base fornisce diverse colonne del sito da utilizzare nel nuovo tipo di contenuto.

#### <a name="to-create-a-custom-content-type"></a>Per creare un tipo di contenuto personalizzato

1. Aggiungere un tipo di contenuto al progetto. A questo scopo, nella **Esplora soluzioni**, scegliere il nodo del progetto

2. Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

3. In presenza di una **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.

4. Nel **modelli** riquadro, scegliere il **tipo di contenuto** modello, modificare il nome in **informazioni di paziente**e quindi scegliere il **Aggiungi** pulsante.

     Il **Personalizzazione guidata SharePoint** apre.

5. Nel **quale tipo di contenuto base deve ereditare questo tipo di contenuto da** elenco, scegliere **Contact** come tipo di contenuto su cui basare il nuovo tipo di contenuto e quindi scegliere il **fine**pulsante.

     Questa operazione consente di accedere alle altre colonne del sito potenzialmente utile nel tipo di contenuto contatto, oltre alle colonne del sito definita in precedenza.

6. Dopo il tipo di contenuto Progettazione progetti, nelle **colonne** scheda, aggiungere le tre colonne definiti in precedenza del sito: **Nome dei pazienti**, **ID paziente**, e **Dottor nome**. Per aggiungere tali colonne, scegliere la prima casella di riepilogo nell'elenco le colonne del sito sotto **nome visualizzato**e quindi ogni colonna del sito in elenco una alla volta.

    > [!TIP]
    > Per scegliere le colonne del sito più rapidamente, filtrare l'elenco immettendo le prime lettere del nome della colonna.

7. Oltre alle tre colonne del sito personalizzato, aggiungere il **commenti** colonna del sito dall'elenco delle colonne del sito.

8. Selezionare il **obbligatorio** casella di controllo per il **nome Patient** e **ID paziente** colonne del sito in modo che siano i campi obbligatori.

9. Nel **Content Type** scheda, verificare che il nome del tipo di contenuto sia **paziente Info**e quindi modificare la descrizione **scheda informazioni dei pazienti**.

10. Change **nome del gruppo** a **tipi di contenuto Clinic**e lasciare le altre impostazioni sui valori predefiniti.

11. Nella barra dei menu, scegliere **File** > **Salva tutto**e quindi chiudere la finestra di progettazione di tipo di contenuto.

## <a name="create-a-list"></a>Creare un elenco
 A questo punto, creare un elenco che usa le nuove colonne di tipo e il sito del contenuto.

#### <a name="to-create-a-list"></a>Per creare un elenco

1. Aggiungere un elenco al progetto. A questo scopo, nella **Esplora soluzioni**, scegliere il nodo del progetto.

2. Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

3. In presenza di una **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.

4. Nel **modelli** riquadro, scegliere il **elenco** modello, modificare il nome in **pazienti**e quindi scegliere il **Aggiungi** pulsante.

5. Lasciare il **personalizzare l'elenco in base** impostando come **predefinito (vuoto)** , quindi scegliere il **fine** pulsante.

6. Nella finestra di progettazione elenco, scegliere il **tipi di contenuto** pulsante per visualizzare i **impostazioni del tipo di contenuto** nella finestra di dialogo.

7. Scegliere la nuova riga, scegliere il **le informazioni di paziente** tipo nell'elenco dei tipi di contenuto di contenuto e quindi scegliere il **OK** pulsante.

     Questa operazione aggiunge tutte le colonne del sito dal **le informazioni di paziente** tipo nell'elenco di contenuto.

8. Eliminare tutte le colonne del sito in elenco ad eccezione dei seguenti:

    - ID dei pazienti

    - Nome dei pazienti

    - Telefono abitazione

    - Messaggio di posta elettronica

    - Nome del Dottor

    - Commenti

9. Sotto **nome visualizzato colonna**, scegliere una riga vuota, aggiungere una colonna di elenco personalizzato e denominarlo **ospedale**. Lasciare il tipo di dati **una riga di testo**.

     La colonna di elenco personalizzato si applica solo a questo elenco. Quando si aggiunge una colonna di elenco personalizzato per un elenco, un nuovo tipo di contenuto, incluse tutte le colonne aggiunte all'elenco, viene creato e impostato come elenco predefinito.

    > [!TIP]
    > Se si sceglie una colonna dall'elenco di colonne del sito, viene utilizzata una colonna di sito esistente. Tuttavia, se si immette un valore di nome di colonna senza scegliere tutte le colonne nell'elenco, viene creata una colonna di elenco personalizzato, anche se una colonna con lo stesso nome esiste già nell'elenco.

     Facoltativamente, anziché impostare il tipo di dati della colonna di elenco personalizzato per **una riga di testo**, invece, è possibile impostare il tipo di dati per questa colonna di ricerca e i relativi valori verrà recuperati da una tabella o un altro elenco. Per informazioni sulle colonne di ricerca, vedere [relazioni di elenco in SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=224994) e [elenco relazioni e ricerche](http://go.microsoft.com/fwlink/?LinkID=224995).

10. Accanto al **ID paziente** e **nome Patient** caselle, selezionare il **necessari** casella di controllo.

11. Nel **viste** scheda, scegliere una riga vuota per creare una vista. Immettere **i dettagli sui pazienti**.

     Nel **viste** scheda, è possibile specificare le colonne che si desidera visualizzare nell'elenco di SharePoint.

12. Scegliere il nuovo **dettagli paziente** riga e quindi scegliere il **imposta come predefinito** pulsante.

     La nuova vista è ora la visualizzazione predefinita per un elenco.

13. Aggiungere le colonne seguenti per il **colonne selezionate** elenco nell'ordine seguente:

    - ID dei pazienti

    - Nome dei pazienti

    - Telefono abitazione

    - Messaggio di posta elettronica

    - Nome del Dottor

    - Ospedale

    - Commenti

14. Nel **delle proprietà** scegliere il **ordinamento e raggruppamento** proprietà e quindi scegliere il pulsante con puntini di sospensione ![puntini di sospensione](../sharepoint/media/ellipsisicon.gif "puntini di sospensione")per visualizzare la **ordinamento e raggruppamento** nella finestra di dialogo.

15. Nel **nome della colonna** scegliere **nome Patient**, verificare che il **ordinamento** colonna è impostata su **crescente**e quindi scegliere il  **OK** pulsante.

## <a name="test-the-application"></a>Testare l'applicazione
 Ora che le colonne del sito personalizzato, tipo di contenuto ed elenco sono pronti, distribuirle in SharePoint ed eseguire l'applicazione per eseguire il test.

#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione

1. Sulla barra dei menu scegliere **File** > **Salva tutto**.

2. Scegliere il **F5** per eseguire l'applicazione.

     L'applicazione viene compilata e quindi le relative funzionalità vengono distribuite in SharePoint e attivate.

3. Nella barra di navigazione rapida, scegliere il **pazienti** link per visualizzare i **i pazienti** elenco.

     I nomi delle colonne nell'elenco devono corrispondere a quelli che è stato immesso il **viste** scheda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

4. Scegliere il **Aggiungi nuovo elemento** collegamento per creare una scheda informazioni dei pazienti.

5. Immettere le informazioni nei campi e quindi scegliere il **salvare** pulsante.

     Il nuovo record venga visualizzato nell'elenco.

## <a name="see-also"></a>Vedere anche
- [Creare colonne del sito, i tipi di contenuto ed elenchi per SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Procedura: Creare un tipo di campo personalizzato](http://go.microsoft.com/fwlink/?LinkId=192079)
- [Tipi di contenuto](http://go.microsoft.com/fwlink/?LinkId=192080)
- [Colonne](http://go.microsoft.com/fwlink/?LinkId=192081)
