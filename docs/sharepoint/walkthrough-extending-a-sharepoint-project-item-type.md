---
title: 'Procedura dettagliata: estensione di un tipo di elemento di progetto SharePoint | Microsoft Docs'
description: In questa procedura dettagliata creare un'estensione per un tipo di elemento di progetto SharePoint, ad esempio l'elemento del progetto del modello di integrazione applicativa dei dati.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3a360b6a336f64920c0144f742e98a64282eeeec
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970406"
---
# <a name="walkthrough-extend-a-sharepoint-project-item-type"></a>Procedura dettagliata: estensione di un tipo di elemento di progetto SharePoint
  È possibile utilizzare l'elemento di progetto **modello di integrazione applicativa dei dati** per creare un modello per il servizio di integrazione applicativa dei dati in SharePoint. Per impostazione predefinita, quando si crea un modello utilizzando questo elemento del progetto, i dati nel modello non vengono visualizzati agli utenti. È inoltre necessario creare un elenco esterno in SharePoint per consentire agli utenti di visualizzare i dati.

 In questa procedura dettagliata verrà creata un'estensione per l'elemento del progetto **modello di integrazione applicativa dei dati** . Gli sviluppatori possono usare l'estensione per creare un elenco esterno nel progetto che Visualizza i dati nel modello di integrazione applicativa dei dati. In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un'estensione di Visual Studio che esegue due attività principali:

  - Genera un elenco esterno che Visualizza i dati in un modello di integrazione applicativa dei dati. L'estensione usa il modello a oggetti per il sistema del progetto SharePoint per generare un file di *Elements.xml* che definisce l'elenco. Aggiunge inoltre il file al progetto in modo che venga distribuito insieme al modello di integrazione applicativa dei dati.

  - Viene aggiunta una voce di menu di scelta rapida agli elementi del progetto **modello di integrazione applicativa dei dati** in **Esplora soluzioni**. Gli sviluppatori possono fare clic sulla voce di menu per generare un elenco esterno per il modello di integrazione applicativa dei dati.

- Creazione di un pacchetto di estensione di Visual Studio (VSIX) per distribuire l'assembly dell'estensione.

- Test dell'estensione.

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario che nel computer di sviluppo siano presenti i componenti seguenti:

- Edizioni supportate di Microsoft Windows, SharePoint e Visual Studio.

- Oggetto [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Questa procedura dettagliata usa il modello di **progetto VSIX** nell'SDK per creare un pacchetto VSIX per distribuire l'elemento di progetto. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Per completare la procedura dettagliata, è necessario conoscere i concetti seguenti:

- Il servizio di integrazione applicativa dei dati in [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] . Per ulteriori informazioni, vedere [architettura BDC](/previous-versions/office/developer/sharepoint-2010/ee558876(v=office.14)).

- XML Schema per i modelli di integrazione applicativa dei dati. Per altre informazioni, vedere [infrastruttura del modello di integrazione applicativa](/previous-versions/office/developer/sharepoint-2010/ee556378(v=office.14))dei dati.

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare due progetti:

- Progetto VSIX per creare il pacchetto VSIX per distribuire l'estensione dell'elemento di progetto.

- Progetto di libreria di classi che implementa l'estensione dell'elemento di progetto.

  Avviare la procedura dettagliata creando i progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto**.

3. Nella finestra di dialogo **nuovo progetto** espandere i nodi **Visual C#** o **Visual Basic** , quindi scegliere il nodo **estensibilità** .

    > [!NOTE]
    > Il nodo **estensibilità** è disponibile solo se si installa Visual Studio SDK. Per ulteriori informazioni, vedere la sezione Prerequisiti più indietro in questo argomento.

4. Nell'elenco nella parte superiore della finestra di dialogo **nuovo progetto** scegliere **.NET Framework 4,5**.

     Le estensioni degli strumenti di SharePoint richiedono funzionalità in questa versione del .NET Framework.

5. Scegliere il modello di **progetto VSIX** .

6. Nella casella **nome** immettere **GenerateExternalDataLists**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **GenerateExternalDataLists** a **Esplora soluzioni**.

7. Se il file source. Extension. vsixmanifest non viene aperto automaticamente, aprire il relativo menu di scelta rapida nel progetto GenerateExternalDataLists, quindi scegliere **Apri** .

8. Verificare che il file source. Extension. vsixmanifest includa una voce non vuota (immettere contoso) per il campo autore, salvare il file e quindi chiuderlo.

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo della soluzione **GenerateExternalDataLists** , scegliere **Aggiungi**, quindi **nuovo progetto**.

2. Nella finestra di dialogo **Aggiungi nuovo progetto** espandere i nodi **Visual C#** o **Visual Basic** , quindi scegliere il nodo **Windows** .

3. Nell'elenco nella parte superiore della finestra di dialogo scegliere **.NET Framework 4,5**.

4. Nell'elenco dei modelli di progetto scegliere **libreria di classi**.

5. Nella casella **nome** immettere **BdcProjectItemExtension**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **BdcProjectItemExtension** alla soluzione e apre il file di codice Class1 predefinito.

6. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-extension-project"></a>Configurare il progetto di estensione
 Prima di scrivere il codice per creare l'estensione dell'elemento di progetto, aggiungere i file di codice e i riferimenti ad assembly al progetto di estensione.

#### <a name="to-configure-the-project"></a>Per configurare il progetto

1. Nel progetto BdcProjectItemExtension aggiungere due file di codice con i nomi seguenti:

    - ProjectItemExtension

    - GenerateExternalDataLists

2. Scegliere il progetto BdcProjectItemExtension, quindi nella barra dei menu scegliere **progetto**  >  **Aggiungi riferimento**.

3. Nel nodo **assembly** , scegliere il nodo **Framework** , quindi selezionare la casella di controllo per ognuno degli assembly seguenti:

    - System.ComponentModel.Composition

    - WindowsBase

4. Nel nodo **assembly** , scegliere il nodo **estensioni** , quindi selezionare la casella di controllo per l'assembly seguente:

    - Microsoft. VisualStudio. SharePoint

5. Fare clic su **OK** .

## <a name="define-the-project-item-extension"></a>Definire l'estensione dell'elemento di progetto
 Creare una classe che definisce l'estensione per l'elemento del progetto **modello di integrazione applicativa dei dati** . Per definire l'estensione, la classe implementa l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfaccia. Implementare questa interfaccia quando si desidera estendere un tipo di elemento di progetto esistente.

#### <a name="to-define-the-project-item-extension"></a>Per definire l'estensione dell'elemento di progetto

1. Incollare il codice seguente nel file di codice ProjectItemExtension.

    > [!NOTE]
    > Una volta aggiunto questo codice, il progetto avrà alcuni errori di compilazione. Questi errori si verificano quando si aggiunge codice nei passaggi successivi.

     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]

## <a name="create-the-external-data-lists"></a>Creare gli elenchi di dati esterni
 Aggiungere una definizione parziale della `GenerateExternalDataListsExtension` classe che crea un elenco di dati esterno per ogni entità nel modello di integrazione applicativa dei dati. Per creare l'elenco di dati esterni, questo codice legge prima di tutto i dati di entità nel modello di integrazione applicativa dei dati analizzando i dati XML nel file del modello di integrazione applicativa dei dati. Crea quindi un'istanza di elenco basata sul modello di integrazione applicativa dei dati e aggiunge questa istanza di elenco al progetto.

#### <a name="to-create-the-external-data-lists"></a>Per creare gli elenchi di dati esterni

1. Incollare il codice seguente nel file di codice GenerateExternalDataLists.

     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per l'estensione dell'elemento di progetto è ora presente nel progetto. Compilare la soluzione per verificare che il progetto venga compilato senza errori.

#### <a name="to-build-the-solution"></a>Per compilare la soluzione

1. Sulla barra dei menu scegliere **Compila**  >  **Compila soluzione**.

## <a name="create-a-vsix-package-to-deploy-the-project-item-extension"></a>Creare un pacchetto VSIX per distribuire l'estensione dell'elemento di progetto
 Per distribuire l'estensione, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Per prima cosa, configurare il pacchetto VSIX modificando il file source. Extension. vsixmanifest incluso nel progetto VSIX. Quindi, creare il pacchetto VSIX compilando la soluzione.

#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il file source. Extension. vsixmanifest nel progetto GenerateExternalDataLists, quindi scegliere **Apri**.

     Visual Studio apre il file nell'editor manifesto. Il file source. Extension. vsixmanifest è la base del file Extension. vsixmanifest è richiesto da tutti i pacchetti VSIX. Per altre informazioni su questo file, vedere [riferimento allo schema di estensione VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. Nella casella **Product Name** immettere **External Data List Generator**.

3. Nella casella **autore** immettere **Contoso**.

4. Nella casella **Descrizione** immettere **un'estensione per gli elementi del progetto del modello di integrazione applicativa dei dati che possono essere utilizzati per generare elenchi di dati esterni**.

5. Nella scheda **Asset** dell'Editor scegliere il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

6. Nell'elenco **tipo** scegliere **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Questo valore corrisponde all' `MefComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per altre informazioni, vedere [Elemento MEFComponent (schema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Nell'elenco **origine** scegliere **un progetto nella soluzione corrente**.

8. Nell'elenco **progetto** scegliere **BdcProjectItemExtension**, quindi scegliere il pulsante **OK** .

9. Sulla barra dei menu scegliere **Compila**  >  **Compila soluzione**.

10. Verificare che il progetto venga compilato e compilato senza errori.

11. Assicurarsi che la cartella di output di compilazione per il progetto GenerateExternalDataLists contenga ora il file GenerateExternalDataLists. vsix.

     Per impostazione predefinita, la cartella di output di compilazione è.. cartella \bin\Debug nella cartella che contiene il file di progetto.

## <a name="test-the-project-item-extension"></a>Testare l'estensione dell'elemento di progetto
 A questo punto è possibile eseguire il test dell'estensione dell'elemento di progetto. Innanzitutto, avviare il debug del progetto di estensione nell'istanza sperimentale di Visual Studio. Usare quindi l'estensione nell'istanza sperimentale di Visual Studio per generare un elenco esterno per un modello di integrazione applicativa dei dati. Infine, aprire l'elenco esterno nel sito di SharePoint per verificare che funzioni come previsto.

#### <a name="to-start-debugging-the-extension"></a>Per avviare il debug dell'estensione

1. Se necessario, riavviare Visual Studio con credenziali amministrative, quindi aprire la soluzione GenerateExternalDataLists.

2. Nel progetto BdcProjectItemExtension aprire il file di codice ProjectItemExtension e quindi aggiungere un punto di interruzione alla riga di codice nel `Initialize` metodo.

3. Aprire il file di codice GenerateExternalDataLists, quindi aggiungere un punto di interruzione alla prima riga di codice nel `GenerateExternalDataLists_Execute` metodo.

4. Per avviare il debug, premere il tasto **F5** oppure scegliere **debug**  >  **Avvia debug** sulla barra dei menu.

     Visual Studio installa l'estensione in%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External Data List Generator\1.0 e avvia un'istanza sperimentale di Visual Studio. Si eseguirà il test dell'elemento del progetto in questa istanza di Visual Studio.

#### <a name="to-test-the-extension"></a>Per testare l'estensione

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **file**  >  **nuovo**  >  **progetto**.

2. Nella finestra di dialogo **nuovo progetto** espandere il nodo **modelli** , espandere il nodo **Visual C#** , espandere il nodo **SharePoint** , quindi selezionare **2010**.

3. Nell'elenco nella parte superiore della finestra di dialogo verificare che sia selezionata l'opzione **.NET Framework 3,5** . Per i progetti per è [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] necessaria questa versione del .NET Framework.

4. Nell'elenco dei modelli di progetto scegliere **progetto SharePoint 2010**.

5. Nella casella **nome** immettere **SharePointProjectTestBDC**, quindi scegliere il pulsante **OK** .

6. Nella procedura guidata di personalizzazione di SharePoint, immettere l'URL del sito che si desidera utilizzare per il debug, scegliere **Distribuisci come soluzione farm**, quindi scegliere il pulsante **fine** .

7. Aprire il menu di scelta rapida per il progetto SharePointProjectTestBDC, scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.

8. Nella finestra di dialogo **Aggiungi newItem-SharePointProjectTestBDC** espandere il nodo lingua installata, espandere il nodo **SharePoint** .

9. Scegliere il nodo **2010** , quindi scegliere il modello **Business Data Connectivity Model (solo soluzione farm)** .

10. Nella casella **nome** immettere **TestBDCModel**, quindi scegliere il pulsante **Aggiungi** .

11. Verificare che il codice nell'altra istanza di Visual Studio si arresti in base al punto di interruzione impostato nel `Initialize` metodo del file di codice ProjectItemExtension.

12. Nell'istanza arrestata di Visual Studio, premere il tasto **F5** oppure sulla barra dei menu scegliere **debug**  >  **continua** per continuare a eseguire il debug del progetto.

13. Nell'istanza sperimentale di Visual Studio premere il tasto **F5** oppure, sulla barra dei menu, scegliere **debug**  >  **Avvia debug** per compilare, distribuire ed eseguire il progetto **TestBDCModel** .

     Il Web browser si apre alla pagina predefinita del sito di SharePoint specificato per il debug.

14. Verificare che la sezione degli **elenchi** nell'area avvio veloce non contenga ancora un elenco basato sul modello di integrazione applicativa dei dati predefinito nel progetto. Per prima cosa, è necessario creare un elenco di dati esterni usando l'interfaccia utente di SharePoint o l'estensione dell'elemento di progetto.

15. Chiudere il Web browser.

16. Nell'istanza di Visual Studio in cui è aperto il progetto TestBDCModel, aprire il menu di scelta rapida per il nodo **TestBDCModel** in **Esplora soluzioni**, quindi scegliere **generate external data list**.

17. Verificare che il codice nell'altra istanza di Visual Studio si arresti in base al punto di interruzione impostato nel `GenerateExternalDataLists_Execute` metodo. Premere il tasto **F5** oppure, sulla barra dei menu, scegliere **debug**  >  **continua** per continuare a eseguire il debug del progetto.

18. L'istanza sperimentale di Visual Studio aggiunge un'istanza di elenco denominata **Entity1DataList** al progetto TestBDCModel e l'istanza genera anche una funzionalità denominata **Funzionalità2** per l'istanza dell'elenco.

19. Premere il tasto **F5** oppure, sulla barra dei menu, scegliere **debug**  >  **Avvia debug** per compilare, distribuire ed eseguire il progetto TestBDCModel.

     Il Web browser si apre alla pagina predefinita del sito di SharePoint usato per il debug.

20. Nella sezione **elenchi** dell'area avvio veloce scegliere l'elenco **Entity1DataList** .

21. Verificare che l'elenco contenga colonne denominate Identificatore1 e Message, oltre a un elemento con un valore Identificatore1 pari a 0 e un valore del messaggio Hello World.

     Il modello di progetto **Business Data Connectivity Model** genera il modello di integrazione applicativa dei dati predefinito che fornisce tutti questi dati.

22. Chiudere il Web browser.

## <a name="clean-up-the-development-computer"></a>Pulire il computer di sviluppo
 Al termine del test dell'estensione dell'elemento di progetto, rimuovere l'elenco esterno e il modello di integrazione applicativa dei dati dal sito di SharePoint e rimuovere l'estensione dell'elemento di progetto da Visual Studio.

#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>Per rimuovere l'elenco di dati esterni dal sito di SharePoint

1. Nell'area avvio veloce del sito di SharePoint, scegliere l'elenco **Entity1DataList** .

2. Sulla barra multifunzione sul sito di SharePoint scegliere la scheda **elenco** .

3. Nel gruppo **Impostazioni** della scheda **elenco** scegliere **Impostazioni elenco**.

4. In **autorizzazioni e gestione** scegliere **Elimina questo elenco**, quindi scegliere **OK** per confermare che si desidera inviare l'elenco al Cestino.

5. Chiudere il Web browser.

#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>Per rimuovere il modello di integrazione applicativa dei dati dal sito di SharePoint

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **Build**  >  **ritrazione** compilazione.

     Visual Studio rimuove il modello di integrazione applicativa dei dati dal sito di SharePoint.

#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Per rimuovere l'estensione dell'elemento di progetto da Visual Studio

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **strumenti**  >  **estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni scegliere **External Data List Generator**, quindi scegliere il pulsante **Disinstalla** .

3. Nella finestra di dialogo visualizzata scegliere **Sì** per confermare che si desidera disinstallare l'estensione.

4. Scegliere **Riavvia ora** per completare la disinstallazione.

5. Chiudere entrambe le istanze di Visual Studio (l'istanza sperimentale e l'istanza in cui è aperta la soluzione GenerateExternalDataLists).

## <a name="see-also"></a>Vedi anche
- [Estendere il sistema del progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Creare un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Progettare un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)