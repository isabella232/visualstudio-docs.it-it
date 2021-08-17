---
title: Creare la colonna del sito, il tipo di contenuto e l'elenco per SharePoint
titleSuffix: ''
description: In questa procedura dettagliata viene creata una colonna (campo) del sito personalizzata, un tipo di contenuto personalizzato che usa la colonna del sito e un elenco che usa il tipo di contenuto in SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: aafbee5bd508930b2b7f5f260977791d0c111c2a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092749"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Procedura dettagliata: Creare una colonna del sito, un tipo di contenuto ed un elenco per SharePoint
  Le procedure seguenti illustrano come creare colonne SharePoint sito personalizzate, o campi, nonché un tipo di contenuto che usa le colonne del sito. Viene inoltre illustrato come creare un elenco che usa il nuovo tipo di contenuto.

 In questa procedura dettagliata sono incluse le attività seguenti:

- [Creare colonne del sito personalizzate.](#create-custom-site-columns)

- [Creare un tipo di contenuto personalizzato](#create-a-custom-content-type).

- [Creare un elenco](#create-a-list).

- [Testare l'applicazione](#test-the-application).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Windows e SharePoint.

- [!INCLUDE[vsprvs-current](../sharepoint/includes/vsprvs-current-md.md)]

## <a name="create-custom-site-columns"></a>Creare colonne del sito personalizzate
 Questo esempio crea un elenco per la gestione dei pazienti in un ospedale. In primo luogo, è necessario creare SharePoint progetto di distribuzione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e aggiungervi colonne del sito, come indicato di seguito.

#### <a name="to-create-the-project"></a>Per creare il progetto

1. Scegliere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **Nuovo** dal menu File  >  **Project**.
::: moniker range="=vs-2017"
2. Nella finestra **di dialogo Nuovo Project,** in **Visual C#** o **Visual Basic**, espandere il nodo **Office/SharePoint** e quindi **selezionare SharePoint Soluzioni**.

3. Nel riquadro **Modelli** scegliere il SharePoint **vuoto Project** per la versione specifica SharePoint installata. Ad esempio, se è stata installata SharePoint 2016, selezionare il **SharePoint 2016 - Vuoto Project 2016.**  

4. Modificare il nome del progetto in **Clinic** e quindi scegliere **il pulsante OK.**

5. Nella  finestra di dialogo Specificare il sito e il livello di sicurezza per il debug immettere l'URL del sito SharePoint locale a cui si vuole aggiungere il nuovo elemento campo personalizzato oppure usare il percorso predefinito ( `http://<` *SystemName* `>/)` .

6. Nella sezione **Qual è il livello di attendibilità** per questa SharePoint soluzione? usare il valore predefinito **Distribuisci come soluzione in modalità sandbox.**

     Per altre informazioni sulle soluzioni sandbox e farm, vedere [Considerazioni sulle soluzioni in modalità sandbox.](../sharepoint/sandboxed-solution-considerations.md)

7. Fare clic sul pulsante **Fine**. Il progetto è ora elencato in **Esplora soluzioni**.
::: moniker-end
::: moniker range=">=vs-2019"
2.  Nella finestra **di dialogo Create a New Project** (Crea un nuovo Project) selezionare il SharePoint Vuoto **Project** per la versione specifica SharePoint installata. Ad esempio, se è stata installata SharePoint 2016, selezionare il **SharePoint 2016 - Vuoto Project 2016.**
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Modificare il nome del progetto in **Clinic** e quindi scegliere il **pulsante** Crea.

4. Nella  finestra di dialogo Specificare il sito e il livello di sicurezza per il debug immettere l'URL del sito SharePoint locale a cui si vuole aggiungere il nuovo elemento campo personalizzato oppure usare il percorso predefinito ( `http://<` *SystemName* `>/)` .

5. Nella sezione **Qual è il livello di attendibilità** per questa SharePoint soluzione? usare il valore predefinito **Distribuisci come soluzione in modalità sandbox.**

     Per altre informazioni sulle soluzioni sandbox e farm, vedere [Considerazioni sulle soluzioni in modalità sandbox.](../sharepoint/sandboxed-solution-considerations.md)

6. Fare clic sul pulsante **Fine**. Il progetto è ora elencato in **Esplora soluzioni**.
::: moniker-end

#### <a name="to-add-site-columns"></a>Per aggiungere colonne del sito

1. Aggiungere una nuova colonna del sito. A tale scopo, in **Esplora soluzioni** fare clic con il pulsante destro del mouse sul **progetto Clinic** e quindi **scegliere Aggiungi**  >  **nuovo elemento.**

2. Nella finestra **di dialogo Aggiungi** nuovo elemento scegliere **Colonna** del sito , modificare il nome in **PatientName** e quindi scegliere il **pulsante** Aggiungi.

3. Nel file di configurazione della colonna *Elements.xml* sito lasciare l'impostazione Tipo impostata su **Testo** e modificare l'impostazione Gruppo in **Clinic Site Columns**.   Al termine, il fileElements.xml *della* colonna del sito dovrebbe essere simile all'esempio seguente.

    ```xml
    <Field
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"
         Name="PatientName"
         DisplayName="Patient Name"
         Type="Text"
         Required="FALSE"
         Group="Clinic Site Columns">
    </Field>
    ```

    > [!TIP]
    > Visual Studio aggiungerà automaticamente uno spazio in DisplayName se si usa la distinzione tra maiuscole e minuscole camel nel nome della colonna del sito.
    > È consigliabile non usare spazi nel nome della colonna del sito perché può causare problemi quando si tenta di distribuire la soluzione in SharePoint.

4. Usando la stessa procedura, aggiungere altre due colonne del sito al progetto: **PatientID** (Type = "Integer") e **DoctorName** (Type = "Text"). Impostare il valore group su **Clinic Site Columns**.

## <a name="create-a-custom-content-type"></a>Creare un tipo di contenuto personalizzato
 Creare quindi un tipo di contenuto, basato sul tipo di contenuto Contatti, che includa le colonne del sito create nella procedura precedente. Basando un tipo di contenuto su un tipo di contenuto esistente, è possibile risparmiare tempo perché il tipo di contenuto di base fornisce diverse colonne del sito da usare nel nuovo tipo di contenuto.

#### <a name="to-create-a-custom-content-type"></a>Per creare un tipo di contenuto personalizzato

1. Aggiungere un tipo di contenuto al progetto. A tale scopo, in **Esplora soluzioni** scegliere il nodo del progetto

2. Nella barra dei menu scegliere **Project**  >  **Aggiungi nuovo elemento**.

3. In **Visual C#** o **Visual Basic** espandere  il SharePoint e quindi scegliere il **nodo 2010.**

4. Nel riquadro **Modelli** scegliere il modello **Tipo di** contenuto, modificare il nome in **Patient Info** e quindi scegliere il **pulsante Aggiungi.**

     Verrà **visualizzata SharePoint personalizzazione guidata** impostazioni.

5. **Nell'elenco** Da quale tipo di contenuto di base deve ereditare questo tipo di contenuto scegliere **Contatto** come tipo di contenuto su cui basare il nuovo tipo di contenuto e quindi scegliere **il pulsante** Fine.

     In questo modo è possibile accedere ad altre colonne del sito potenzialmente utili nel tipo di contenuto Contatto, oltre alle colonne del sito definite in precedenza.

6. Quando viene visualizzata la finestra  di progettazione Tipo di contenuto, nella scheda Colonne aggiungere le tre colonne del sito definite in precedenza: **Nome** paziente , **ID** paziente e **Nome medico**. Per aggiungere queste colonne, scegliere la prima casella di riepilogo nell'elenco delle colonne del sito in **Nome** visualizzato e quindi scegliere una alla volta ogni colonna del sito nell'elenco.

    > [!TIP]
    > Per scegliere più rapidamente le colonne del sito, filtrare l'elenco immettendo le prime lettere del nome della colonna.

7. Oltre alle tre colonne del sito personalizzate, aggiungere la **colonna del sito** Commenti dall'elenco delle colonne del sito.

8. Selezionare la **casella di** controllo Obbligatorio per le colonne del sito Patient **Name (Nome** paziente) e **Patient ID (ID** paziente) per renderle obbligatorie.

9. Nella scheda **Tipo di contenuto** verificare che il nome del tipo di contenuto sia Patient **Info** e quindi modificare la descrizione in Patient **information card**.

10. Modificare **Group Name (Nome** **gruppo) in Clinic Content Types**(Tipi di contenuto clinici) e lasciare i valori predefiniti per le altre impostazioni.

11. Sulla barra dei menu scegliere **File** Salva tutto e quindi chiudere la finestra  >  di progettazione Tipo di contenuto.

## <a name="create-a-list"></a>Crea un elenco
 Creare ora un elenco che usa il nuovo tipo di contenuto e le colonne del sito.

#### <a name="to-create-a-list"></a>Per creare un elenco

1. Aggiungere un elenco al progetto. A tale scopo, in **Esplora soluzioni** scegliere il nodo del progetto.

2. Nella barra dei menu scegliere **Project**  >  **Aggiungi nuovo elemento**.

3. In **Visual C#** o **Visual Basic** espandere il **nodo SharePoint.**

4. Nel riquadro **Modelli** scegliere il modello **Elenco,** modificare il nome in **Patients** e quindi scegliere il **pulsante** Aggiungi.

5. Lasciare **l'impostazione Personalizza l'elenco** in base all'impostazione Predefinita **(elenco personalizzato)** e quindi scegliere **il pulsante** Fine.

6. In Progettazione elenchi scegliere il pulsante **Tipi di** contenuto per visualizzare la finestra di dialogo Tipo **Impostazioni** contenuto .

7. Scegliere la nuova riga, scegliere il tipo **di contenuto Patient Info** nell'elenco dei tipi di contenuto e quindi scegliere il pulsante **OK.**

     In questo modo vengono aggiunte tutte le colonne del sito dal tipo **di contenuto Patient Info** nell'elenco.

8. Eliminare tutte le colonne del sito nell'elenco, ad eccezione delle seguenti:

    - ID paziente

    - Nome del paziente

    - Telefono (ab.)

    - Posta elettronica

    - Nome medico

    - Commenti

9. In **Nome visualizzato colonna** scegliere una riga vuota, aggiungere una colonna elenco personalizzata e assegnare alla colonna il nome **Hospital**. Lasciare il tipo di dati **su Riga singola di testo**.

     La colonna dell'elenco personalizzato si applica solo a questo elenco. Quando si aggiunge una colonna di elenco personalizzata a un elenco, viene creato e impostato come elenco predefinito un nuovo tipo di contenuto elenco, incluse tutte le colonne aggiunte all'elenco.

    > [!TIP]
    > Se si sceglie una colonna dall'elenco delle colonne del sito, viene usata una colonna del sito esistente. Tuttavia, se si immette un valore di nome di colonna senza scegliere alcuna colonna nell'elenco, viene creata una colonna di elenco personalizzata, anche se nell'elenco esiste già una colonna con lo stesso nome.

     Facoltativamente, anziché impostare il tipo di dati per la colonna dell'elenco personalizzato su Riga singola di testo **,** è possibile impostare il tipo di dati per questa colonna su Ricerca e i relativi valori verranno recuperati da una tabella o da un altro elenco. Per informazioni sulle colonne di ricerca, vedere Relazioni tra [elenchi in SharePoint 2010](/previous-versions/msp-n-p/ff798514(v=pandp.10)) e [Ricerche ed Elencare relazioni.](/previous-versions/office/developer/sharepoint-2010/ff623048(v=office.14))

10. Accanto alle **caselle PATIENT ID (ID** paziente) **e Patient Name (Nome paziente)** selezionare la casella di controllo Required **(Richiesto).**

11. Nella scheda **Viste** scegliere una riga vuota per creare una vista. Immettere **Patient Details** (Dettagli pazienti) in una riga vuota sotto la colonna View Name **(Visualizza** nome).

     Nella **scheda Viste** è possibile specificare le colonne da visualizzare nell'elenco SharePoint dati.

12. Scegliere la nuova **riga Patient Details** (Dettagli pazienti) e quindi scegliere il pulsante Set as Default **(Imposta come** predefinito).

     La nuova visualizzazione è ora la visualizzazione predefinita per l'elenco.

13. Aggiungere le colonne seguenti **all'elenco Colonne** selezionate nell'ordine seguente:

    - ID paziente

    - Nome del paziente

    - Telefono (ab.)

    - Posta elettronica

    - Nome medico

    - Ospedale

    - Commenti

14. **Nell'elenco** Proprietà scegliere la proprietà **Ordinamento** e raggruppamento e ![](../sharepoint/media/ellipsisicon.gif "Icona con i puntini di sospensione") quindi fare clic sul pulsante con i puntini di sospensione Icona puntini di sospensione per visualizzare la finestra di dialogo Ordinamento **e** raggruppamento .

15. **Nell'elenco Nome** colonna scegliere **Nome** paziente, assicurarsi che la colonna **Ordinamento** sia impostata su Crescente **e** quindi scegliere il pulsante **OK.**

## <a name="test-the-application"></a>Testare l'applicazione
 Ora che le colonne del sito personalizzato, il tipo di contenuto e l'elenco sono pronti, distribuirle in SharePoint ed eseguire l'applicazione per testarla.

#### <a name="to-test-the-application"></a>Per testare l'applicazione

1. Sulla barra dei menu scegliere **File**  >  **Salva tutto.**

2. Premere **F5 per** eseguire l'applicazione.

     L'applicazione viene compilata e quindi le relative funzionalità vengono distribuite in SharePoint e attivate.

3. Nella barra di spostamento rapido scegliere il collegamento **Patients (Pazienti)** per visualizzare l'elenco **Patients (Pazienti).**

     I nomi delle colonne nell'elenco devono corrispondere a quelli immessi nella **scheda** Viste in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

4. Scegliere il **collegamento Aggiungi nuovo elemento** per creare una scheda informazioni sul paziente.

5. Immettere le informazioni nei campi e quindi scegliere il **pulsante** Salva.

     Il nuovo record viene visualizzato nell'elenco.

## <a name="see-also"></a>Vedi anche
- [Creare colonne del sito, tipi di contenuto ed elenchi per SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Procedura: Creare un tipo di campo personalizzato](/previous-versions/office/developer/sharepoint-2010/bb862248(v=office.14))
- [Tipi di contenuto](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14))
- [Colonne](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))
