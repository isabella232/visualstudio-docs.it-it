---
title: Creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint
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
ms.openlocfilehash: e78594a98066dec6cedff6da6f3f1de823bec796
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985008"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint
  Nelle procedure riportate di seguito viene illustrato come creare colonne o *campi*personalizzati di un sito di SharePoint, nonché un tipo di contenuto che utilizza le colonne del sito. Viene inoltre illustrato come creare un elenco che utilizza il nuovo tipo di contenuto.

 In questa procedura dettagliata sono incluse le attività seguenti:

- [Creazione di colonne del sito personalizzate](#create-custom-site-columns).

- [Creare un tipo di contenuto personalizzato](#create-a-custom-content-type).

- [Creare un elenco](#create-a-list).

- [Testare l'applicazione](#test-the-application).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Windows e SharePoint.

- [!INCLUDE[vsprvs-current](../sharepoint/includes/vsprvs-current-md.md)]

## <a name="create-custom-site-columns"></a>Creazione di colonne del sito personalizzate
 Questo esempio crea un elenco per la gestione dei pazienti in un ospedale. In primo luogo, è necessario creare un progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e aggiungervi le colonne del sito, come indicato di seguito.

#### <a name="to-create-the-project"></a>Per creare il progetto

1. Scegliere **nuovo** > **progetto**dal menu **file** di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Nella finestra di dialogo **nuovo progetto** , in **Visual C#**  o **Visual Basic**, espandere il nodo **SharePoint** , quindi selezionare **2010**.

3. Nel riquadro **modelli** scegliere **progetto SharePoint 2010**, modificare il nome del progetto in **Clinic**, quindi scegliere il pulsante **OK** .

     Il modello di progetto SharePoint 2010 è un progetto vuoto usato in questo esempio per contenere le colonne del sito e altri elementi del progetto che vengono aggiunti in un secondo momento.

4. Nella pagina **specificare il sito e il livello di sicurezza per il debug** immettere l'URL per il sito di SharePoint locale a cui si desidera aggiungere il nuovo elemento campo personalizzato oppure utilizzare il percorso predefinito (`http://<`*SystemName*`>/)`.

5. Nella sezione **Qual è il livello di attendibilità per la soluzione SharePoint** usare il valore predefinito **Distribuisci come soluzione creata mediante sandbox**.

     Per ulteriori informazioni sulle soluzioni in modalità sandbox e farm, vedere Considerazioni sulle soluzioni [create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).

6. Scegliere il pulsante **fine** . Il progetto è ora elencato in **Esplora soluzioni**.

#### <a name="to-add-site-columns"></a>Per aggiungere colonne del sito

1. Aggiungere una nuova colonna del sito. A tale scopo, in **Esplora soluzioni**aprire il menu di scelta rapida per **Clinic**, quindi scegliere **Aggiungi** > **nuovo elemento**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere **colonna sito**, modificare il nome in **nome paziente**, quindi scegliere il pulsante **Aggiungi** .

3. Nel file *Elements. XML* della colonna del sito lasciare l'impostazione del **tipo** come **testo**e modificare l'impostazione di **gruppo** in **colonne del sito Clinic**. Al termine, il file *Elements. XML* della colonna del sito dovrebbe essere simile all'esempio seguente.

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

4. Utilizzando la stessa procedura, aggiungere altre due colonne del sito al progetto: **ID del paziente** (Type = "Integer") e **nome del medico** (Type = "Text"). Impostare il valore di gruppo sulle **colonne del sito Clinic**.

## <a name="create-a-custom-content-type"></a>Creare un tipo di contenuto personalizzato
 Successivamente, creare un tipo di contenuto, in base al tipo di contenuto contacts, che include le colonne del sito create nella procedura precedente. Basando un tipo di contenuto su un tipo di contenuto esistente, è possibile risparmiare tempo perché il tipo di contenuto di base fornisce diverse colonne del sito da utilizzare nel nuovo tipo di contenuto.

#### <a name="to-create-a-custom-content-type"></a>Per creare un tipo di contenuto personalizzato

1. Aggiungere un tipo di contenuto al progetto. A tale scopo, nella **Esplora soluzioni**scegliere il nodo del progetto

2. Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

3. In **Visual C#**  o **Visual Basic**espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

4. Nel riquadro **modelli** scegliere il modello **tipo di contenuto** , modificare il nome in **informazioni sul paziente**, quindi scegliere il pulsante **Aggiungi** .

     Verrà visualizzata la **procedura guidata di personalizzazione di SharePoint** .

5. Nell'elenco specificare il tipo di contenuto di **base da cui ereditare questo tipo di contenuto** scegliere **Contact** come tipo di contenuto su cui basare il nuovo tipo di contenuto, quindi scegliere il pulsante **fine** .

     Questa operazione consente di accedere ad altre colonne del sito potenzialmente utili nel tipo di contenuto Contact, oltre alle colonne del sito definite in precedenza.

6. Quando viene visualizzata la finestra di progettazione dei tipi di contenuto, nella scheda **colonne** aggiungere le tre colonne del sito definite in precedenza, ovvero il **nome del paziente**, l' **ID del paziente**e il nome del **medico**. Per aggiungere queste colonne, scegliere la prima casella di riepilogo nell'elenco colonne sito in **nome visualizzato**, quindi scegliere ogni colonna del sito nell'elenco uno alla volta.

    > [!TIP]
    > Per scegliere più rapidamente le colonne del sito, filtrare l'elenco immettendo le prime lettere del nome della colonna.

7. Oltre alle tre colonne del sito personalizzate, aggiungere la colonna del sito **Commenti** dall'elenco colonne sito.

8. Selezionare la casella di controllo **obbligatorio** per le colonne del sito **nome del paziente** e **ID paziente** per impostare i campi necessari.

9. Nella scheda **tipo di contenuto** verificare che il nome del tipo di contenuto sia **informazioni sul paziente**, quindi modificare la descrizione in **scheda informazioni del paziente**.

10. Modificare il **nome del gruppo** in tipi di **contenuto Clinic**e lasciare invariati i valori predefiniti per le altre impostazioni.

11. Nella barra dei menu scegliere **File** > **Salva tutto**, quindi chiudere la finestra di progettazione del tipo di contenuto.

## <a name="create-a-list"></a>Creazione di un elenco
 A questo punto, creare un elenco che usa il nuovo tipo di contenuto e le colonne del sito.

#### <a name="to-create-a-list"></a>Per creare un elenco

1. Aggiungere un elenco al progetto. A tale scopo, nella **Esplora soluzioni**scegliere il nodo del progetto.

2. Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

3. In **Visual C#**  o **Visual Basic**espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

4. Nel riquadro **modelli** scegliere il modello **elenco** , modificare il nome in **pazienti**, quindi scegliere il pulsante **Aggiungi** .

5. Lasciare l'opzione **Personalizza l'elenco in base** all'impostazione **predefinita (vuota)** , quindi scegliere il pulsante **fine** .

6. Nella finestra di progettazione elenco scegliere il pulsante **tipi di contenuto** per visualizzare la finestra di dialogo **Impostazioni tipo di contenuto** .

7. Scegliere la nuova riga, scegliere il tipo di contenuto **informazioni sul paziente** nell'elenco dei tipi di contenuto, quindi scegliere il pulsante **OK** .

     Questa operazione consente di aggiungere all'elenco tutte le colonne del sito dal tipo di contenuto **info del paziente** .

8. Eliminare tutte le colonne del sito nell'elenco eccetto le seguenti:

    - ID paziente

    - Nome del paziente

    - Telefono abitazione

    - Posta elettronica

    - Nome del medico

    - Comments

9. In **nome visualizzato colonna**scegliere una riga vuota, aggiungere una colonna elenco personalizzata e denominarla **Hospital**. Lasciare il tipo di dati come **singola riga di testo**.

     La colonna elenco personalizzato si applica solo a questo elenco. Quando si aggiunge una colonna elenco personalizzata a un elenco, viene creato un nuovo tipo di contenuto elenco, incluse tutte le colonne aggiunte nell'elenco, che viene impostato come elenco predefinito.

    > [!TIP]
    > Se si sceglie una colonna dall'elenco di colonne del sito, viene utilizzata una colonna del sito esistente. Tuttavia, se si immette un valore nome colonna senza scegliere alcuna colonna nell'elenco, viene creata una colonna elenco personalizzata, anche se nell'elenco esiste già una colonna con lo stesso nome.

     Facoltativamente, anziché impostare il tipo di dati per la colonna elenco personalizzata su una **sola riga di testo**, è possibile impostare il tipo di dati per questa colonna su Lookup e i relativi valori verranno recuperati da una tabella o da un altro elenco. Per informazioni sulle colonne di ricerca, vedere [elencare le relazioni in SharePoint 2010](/previous-versions/msp-n-p/ff798514(v=pandp.10)) e [ricerche ed elencare le relazioni](/previous-versions/office/developer/sharepoint-2010/ff623048(v=office.14)).

10. Accanto alle caselle **ID del paziente** e **nome del paziente** Selezionare la casella di controllo **obbligatorio** .

11. Nella scheda **viste** scegliere una riga vuota per creare una visualizzazione. Immettere **i dettagli del paziente**.

     Nella scheda **viste** è possibile specificare le colonne che si desidera visualizzare nell'elenco SharePoint.

12. Scegliere la nuova riga **Dettagli paziente** , quindi scegliere il pulsante **Imposta come predefinito** .

     La nuova vista è ora la visualizzazione predefinita per l'elenco.

13. Aggiungere le colonne seguenti all'elenco **colonne selezionate** nell'ordine seguente:

    - ID paziente

    - Nome del paziente

    - Telefono abitazione

    - Posta elettronica

    - Nome del medico

    - Ospedale

    - Comments

14. Nell'elenco **Proprietà** scegliere la proprietà **ordinamento e raggruppamento** , quindi scegliere il pulsante con i puntini di sospensione ![icona con i puntini](../sharepoint/media/ellipsisicon.gif "Icona con i puntini di sospensione") di sospensione per visualizzare la finestra di dialogo **ordinamento e raggruppamento** .

15. Nell'elenco **nome colonna** scegliere **nome paziente**, verificare che la colonna **ordinamento** sia impostata su **crescente**, quindi scegliere il pulsante **OK** .

## <a name="test-the-application"></a>Testare l'applicazione
 Ora che le colonne del sito personalizzate, il tipo di contenuto e l'elenco sono pronti, distribuirli in SharePoint ed eseguire l'applicazione per testarla.

#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione

1. Sulla barra dei menu scegliere **File** > **Salva tutto**.

2. Premere il tasto **F5** per eseguire l'applicazione.

     L'applicazione viene compilata e le relative funzionalità vengono quindi distribuite in SharePoint e attivate.

3. Sulla barra di spostamento veloce scegliere il collegamento **patients (pazienti** ) per visualizzare l'elenco dei **pazienti** .

     I nomi delle colonne nell'elenco devono corrispondere a quelli immessi nella scheda **viste** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

4. Scegliere il collegamento **Aggiungi nuovo elemento** per creare una scheda informazioni sul paziente.

5. Immettere le informazioni nei campi, quindi scegliere il pulsante **Salva** .

     Il nuovo record verrà visualizzato nell'elenco.

## <a name="see-also"></a>Vedere anche
- [Creazione di colonne del sito, tipi di contenuto ed elenchi per SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Procedura: creare un tipo di campo personalizzato](/previous-versions/office/developer/sharepoint-2010/bb862248(v=office.14))
- [Tipi di contenuto](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14))
- [Colonne](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))
