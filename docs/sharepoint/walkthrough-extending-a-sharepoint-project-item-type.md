---
title: 'Procedura dettagliata: Estensione di un SharePoint Project tipo di elemento | Microsoft Docs'
description: In questa procedura dettagliata viene creata un'estensione per un SharePoint di elemento di progetto, ad esempio l'elemento di progetto del modello di integrazione applicativa dei dati (BDC).
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 589a9b09f6a59aef62f447f5ce2970eef56e85b6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625068"
---
# <a name="walkthrough-extend-a-sharepoint-project-item-type"></a>Procedura dettagliata: Estendere un tipo SharePoint di elemento di progetto
  È possibile usare **l'elemento di** progetto Modello di connettività dei dati di business per creare un modello per il servizio Business Data Connectivity (BDC) in SharePoint. Per impostazione predefinita, quando si crea un modello usando questo elemento di progetto, i dati nel modello non vengono visualizzati agli utenti. È inoltre necessario creare un elenco esterno in SharePoint consentire agli utenti di visualizzare i dati.

 In questa procedura dettagliata verrà creata un'estensione per l'elemento di progetto **Modello di connettività dei dati** di business. Gli sviluppatori possono utilizzare l'estensione per creare un elenco esterno nel progetto che visualizza i dati nel modello BDC. In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un Visual Studio che esegue due attività principali:

  - Genera un elenco esterno che visualizza i dati in un modello BDC. L'estensione usa il modello a oggetti per SharePoint sistema del progetto per generare un file *Elements.xml* che definisce l'elenco. Aggiunge inoltre il file al progetto in modo che sia distribuito insieme al modello BDC.

  - Aggiunge una voce di menu di scelta rapida agli elementi di progetto del modello di connettività **dei** dati di business in **Esplora soluzioni**. Gli sviluppatori possono fare clic su questa voce di menu per generare un elenco esterno per il modello BDC.

- Compilazione di un pacchetto vsix (Visual Studio Extension) per distribuire l'assembly dell'estensione.

- Test dell'estensione.

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, sono necessari i componenti seguenti nel computer di sviluppo:

- Edizioni supportate di Microsoft Windows, SharePoint e Visual Studio.

- Oggetto [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Questa procedura dettagliata usa il **modello Project VSIX** nell'SDK per creare un pacchetto VSIX per distribuire l'elemento di progetto. Per altre informazioni, vedere [Estendere gli strumenti SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  La conoscenza dei concetti seguenti è utile, ma non necessaria, per completare la procedura dettagliata:

- Servizio BDC in [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] . Per altre informazioni, vedere [BDC Architecture](/previous-versions/office/developer/sharepoint-2010/ee558876(v=office.14)).

- XML Schema per i modelli BDC. Per altre informazioni, vedere [BDC Model Infrastructure](/previous-versions/office/developer/sharepoint-2010/ee556378(v=office.14)).

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare due progetti:

- Un progetto VSIX per creare il pacchetto VSIX per distribuire l'estensione dell'elemento di progetto.

- Progetto di libreria di classi che implementa l'estensione dell'elemento di progetto.

  Iniziare la procedura dettagliata creando i progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Sulla barra dei menu scegliere **File**  >  **Nuovo**  >  **Project**.

3. Nella finestra **di dialogo Project** espandere i nodi Visual **C#** o **Visual Basic** e quindi scegliere il **nodo Extensibility.**

    > [!NOTE]
    > Il **nodo Extensibility** è disponibile solo se si installa Visual Studio SDK. Per altre informazioni, vedere la sezione prerequisiti più indietro in questo argomento.

4. Nell'elenco nella parte superiore della finestra **di dialogo Project** nuova versione scegliere .NET Framework **4.5**.

     SharePoint estensioni degli strumenti richiedono funzionalità in questa versione del .NET Framework.

5. Scegliere il **modello di Project VSIX.**

6. Nella casella **Nome** immettere **GenerateExternalDataLists** e quindi scegliere **il pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto GenerateExternalDataLists** **Esplora soluzioni**.

7. Se il file source.extension.vsixmanifest non si apre automaticamente, aprire il relativo menu di scelta rapida nel progetto GenerateExternalDataLists e quindi scegliere **Apri**

8. Verificare che il file source.extension.vsixmanifest abbia una voce non vuota (immettere Contoso) per il campo Autore, salvare il file e quindi chiuderlo.

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo della soluzione **GenerateExternalDataLists,** scegliere Aggiungi **e** quindi scegliere **Nuovo Project**.

2. Nella finestra **di dialogo Project** nuovo nodo espandere i nodi Visual **C#** o **Visual Basic** e quindi scegliere il **Windows** nodo.

3. Nell'elenco nella parte superiore della finestra di dialogo **scegliere .NET Framework 4.5**.

4. Nell'elenco dei modelli di progetto scegliere **Libreria di classi.**

5. Nella casella **Nome** immettere **BdcProjectItemExtension** e quindi scegliere **il pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto BdcProjectItemExtension** alla soluzione e apre il file di codice Class1 predefinito.

6. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-extension-project"></a>Configurare il progetto di estensione
 Prima di scrivere codice per creare l'estensione dell'elemento di progetto, aggiungere i file di codice e i riferimenti all'assembly al progetto di estensione.

#### <a name="to-configure-the-project"></a>Per configurare il progetto

1. Nel progetto BdcProjectItemExtension aggiungere due file di codice con i nomi seguenti:

    - ProjectItemExtension

    - GenerateExternalDataLists

2. Scegliere il progetto BdcProjectItemExtension e quindi nella barra dei menu **scegliere Project**  >  **Aggiungi riferimento**.

3. Nel **nodo Assembly** scegliere il **nodo Framework** e selezionare la casella di controllo per ognuno degli assembly seguenti:

    - System.ComponentModel.Composition

    - WindowsBase

4. Nel **nodo Assembly** scegliere il nodo **Estensioni** e quindi selezionare la casella di controllo per l'assembly seguente:

    - Microsoft.VisualStudio. SharePoint

5. Fare clic su **OK** .

## <a name="define-the-project-item-extension"></a>Definire l'estensione dell'elemento di progetto
 Creare una classe che definisce l'estensione per l'elemento di progetto Del modello **di connettività dei** dati di business. Per definire l'estensione, la classe implementa <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> l'interfaccia . Implementare questa interfaccia ogni volta che si desidera estendere un tipo esistente di elemento di progetto.

#### <a name="to-define-the-project-item-extension"></a>Per definire l'estensione dell'elemento di progetto

1. Incollare il codice seguente nel file di codice ProjectItemExtension.

    > [!NOTE]
    > Dopo aver aggiunto questo codice, il progetto presenterà alcuni errori di compilazione. Questi errori verranno visualizzati quando si aggiungerà codice nei passaggi successivi.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb" id="Snippet1":::

## <a name="create-the-external-data-lists"></a>Creare gli elenchi di dati esterni
 Aggiungere una definizione parziale della classe `GenerateExternalDataListsExtension` che crea un elenco di dati esterni per ogni entità nel modello BDC. Per creare l'elenco di dati esterni, questo codice legge innanzitutto i dati dell'entità nel modello BDC analizzando i dati XML nel file di modello BDC. Crea quindi un'istanza di elenco basata sul modello BDC e aggiunge l'istanza di elenco al progetto.

#### <a name="to-create-the-external-data-lists"></a>Per creare gli elenchi di dati esterni

1. Incollare il codice seguente nel file di codice GenerateExternalDataLists.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs" id="Snippet2":::

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per l'estensione dell'elemento di progetto si trova ora nel progetto. Compilare la soluzione per assicurarsi che il progetto venga compilato senza errori.

#### <a name="to-build-the-solution"></a>Per compilare la soluzione

1. Nella barra dei menu scegliere **Compila**  >  **compila soluzione.**

## <a name="create-a-vsix-package-to-deploy-the-project-item-extension"></a>Creare un pacchetto VSIX per distribuire l'estensione dell'elemento di progetto
 Per distribuire l'estensione, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Configurare prima di tutto il pacchetto VSIX modificando il file source.extension.vsixmanifest incluso nel progetto VSIX. Creare quindi il pacchetto VSIX compilando la soluzione.

#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il file source.extension.vsixmanifest nel progetto GenerateExternalDataLists e quindi scegliere **Apri.**

     Visual Studio apre il file nell'editor manifesto. Il file source.extension.vsixmanifest è la base per il file extension.vsixmanifest richiesto da tutti i pacchetti VSIX. Per altre informazioni su questo file, vedere Informazioni di riferimento sullo schema dell'estensione [VSIX 1.0.](/previous-versions/dd393700(v=vs.110))

2. Nella casella **Product Name (Nome** prodotto) immettere **External Data List Generator**.

3. Nella casella **Autore** immettere **Contoso**.

4. Nella casella **Descrizione** immettere **Un'estensione per gli elementi di** progetto del modello di connettività dei dati business che può essere usata per generare elenchi di dati esterni.

5. Nella **scheda Asset dell'editor** scegliere il **pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

6. **Nell'elenco Tipo** scegliere **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    > Questo valore corrisponde `MefComponent` all'elemento nel file extension.vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per altre informazioni, vedere [Elemento MEFComponent (schema VSX).](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))

7. **Nell'elenco Origine** scegliere **Un progetto nella soluzione corrente**.

8. **Nell'Project** scegliere **BdcProjectItemExtension** e quindi fare clic **sul pulsante OK.**

9. Sulla barra dei menu scegliere **Compila**  >  **soluzione**.

10. Assicurarsi che il progetto venga compilato e compilato senza errori.

11. Assicurarsi che la cartella di output di compilazione per il progetto GenerateExternalDataLists contenga ora il file GenerateExternalDataLists.vsix.

     Per impostazione predefinita, la cartella dell'output di compilazione è . Cartella \bin\Debug nella cartella che contiene il file di progetto.

## <a name="test-the-project-item-extension"></a>Testare l'estensione dell'elemento di progetto
 A questo punto è possibile testare l'estensione dell'elemento di progetto. Avviare prima di tutto il debug del progetto di estensione nell'istanza sperimentale di Visual Studio. Usare quindi l'estensione nell'istanza sperimentale di Visual Studio per generare un elenco esterno per un modello BDC. Aprire infine l'elenco esterno nel SharePoint per verificare che funzioni come previsto.

#### <a name="to-start-debugging-the-extension"></a>Per avviare il debug dell'estensione

1. Se necessario, riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione GenerateExternalDataLists.

2. Nel progetto BdcProjectItemExtension aprire il file di codice ProjectItemExtension e quindi aggiungere un punto di interruzione alla riga di codice nel `Initialize` metodo .

3. Aprire il file di codice GenerateExternalDataLists e quindi aggiungere un punto di interruzione alla prima riga di codice nel `GenerateExternalDataLists_Execute` metodo .

4. Avviare il debug scegliendo **il tasto F5** o, sulla barra dei menu, scegliendo **Debug**  >  **Avvia debug**.

     Visual Studio installa l'estensione in %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External Data List Generator\1.0 e avvia un'istanza sperimentale di Visual Studio. L'elemento di progetto verrà testato in questa istanza di Visual Studio.

#### <a name="to-test-the-extension"></a>Per testare l'estensione

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **File**  >    >  **nuovo Project**.

2. Nella finestra di **dialogo Nuovo Project**  espandere il nodo Modelli, espandere il  nodo **Visual C#,** espandere il nodo SharePoint e quindi scegliere **2010**.

3. Nell'elenco nella parte superiore della finestra di dialogo assicurarsi che sia **.NET Framework 3.5.** I progetti [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] per richiedono questa versione del .NET Framework.

4. Nell'elenco dei modelli di progetto scegliere **SharePoint 2010 Project**.

5. Nella casella **Nome** immettere **SharePointProjectTestBDC** e quindi scegliere **OK.**

6. Nella Personalizzazione guidata SharePoint, immettere l'URL del sito che si vuole usare per il debug, scegliere Distribuisci come soluzione **farm** e quindi scegliere il **pulsante** Fine.

7. Aprire il menu di scelta rapida per il progetto SharePointProjectTestBDC, scegliere **Aggiungi** e quindi **Nuovo elemento.**

8. Nella finestra **di dialogo Aggiungi NewItem - SharePointProjectTestBDC** espandere il nodo del linguaggio installato, quindi espandere il **SharePoint.**

9. Scegliere il **nodo 2010** e quindi il modello Modello di connettività dati **business (solo soluzione farm).**

10. Nella casella **Nome** immettere **TestBDCModel** e quindi scegliere il **pulsante** Aggiungi.

11. Verificare che il codice nell'altra istanza di Visual Studio si arresti sul punto di interruzione impostato nel metodo del file di codice `Initialize` ProjectItemExtension.

12. Nell'istanza arrestata di Visual Studio premere **F5** oppure sulla barra dei menu scegliere **Debug** Continua per continuare a eseguire  >   il debug del progetto.

13. Nell'istanza sperimentale di Visual Studio premere **F5** oppure, sulla barra dei menu, scegliere **Debug** Avvia debug per compilare, distribuire ed eseguire il  >   progetto **TestBDCModel.**

     Il Web browser si apre alla pagina predefinita del sito SharePoint specificato per il debug.

14. Verificare che **la sezione** Elenchi nell'area Avvio veloce non contenga ancora un elenco basato sul modello BDC predefinito nel progetto. È prima di tutto necessario creare un elenco di dati esterni, usando l'SharePoint utente o l'estensione dell'elemento di progetto.

15. Chiudere il Web browser.

16. Nell'istanza di Visual Studio in cui è aperto il progetto TestBDCModel aprire il menu di scelta rapida per il nodo **TestBDCModel** **in Esplora soluzioni** e quindi scegliere Genera elenco di dati **esterni**.

17. Verificare che il codice nell'altra istanza di Visual Studio si arresti sul punto di interruzione impostato nel `GenerateExternalDataLists_Execute` metodo . Premere **F5** oppure, sulla barra dei menu, scegliere **Debug**  >  **continua** per continuare a eseguire il debug del progetto.

18. L'istanza sperimentale di Visual Studio aggiunge un'istanza di elenco denominata **Entity1DataList** al progetto TestBDCModel e l'istanza genera anche una funzionalità denominata **Feature2** per l'istanza di elenco.

19. Premere **F5** oppure, sulla barra dei menu, scegliere **Debug** Avvia debug per compilare, distribuire ed eseguire  >   il progetto TestBDCModel.

     Il Web browser si apre alla pagina predefinita del sito SharePoint usato per il debug.

20. Nella sezione **Elenchi** dell'area Avvio veloce selezionare **l'elenco Entity1DataList.**

21. Verificare che l'elenco contenga colonne denominate Identifier1 e Message, oltre a un elemento con valore Identifier1 pari a 0 e un valore Message pari a Hello World.

     Il **modello di progetto Modello** di connettività dati business genera il modello BDC predefinito che fornisce tutti questi dati.

22. Chiudere il Web browser.

## <a name="clean-up-the-development-computer"></a>Pulire il computer di sviluppo
 Dopo aver completato il test dell'estensione dell'elemento di progetto, rimuovere l'elenco esterno e il modello BDC dal sito di SharePoint e rimuovere l'estensione dell'elemento di progetto Visual Studio.

#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>Per rimuovere l'elenco di dati esterni dal SharePoint sito

1. Nell'area Avvio veloce del sito SharePoint scegliere **l'elenco Entity1DataList.**

2. Nella barra multifunzione del sito SharePoint scegliere la **scheda** Elenco.

3. Nel **gruppo Impostazioni** della  scheda Elenco scegliere **Impostazioni**.

4. In **Autorizzazioni e gestione** scegliere Elimina **questo** elenco e quindi scegliere **OK** per confermare che si vuole inviare l'elenco al Cestino.

5. Chiudere il Web browser.

#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>Per rimuovere il modello di integrazione applicativa dei dati dal SharePoint sito

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **Build**  >  **Retract**.

     Visual Studio il modello BDC dal SharePoint sito.

#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Per rimuovere l'estensione dell'elemento di progetto Visual Studio

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **Estensioni**  >  **e aggiornamenti degli strumenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco di estensioni scegliere **External Data List Generator** e quindi fare clic sul pulsante **Disinstalla.**

3. Nella finestra di dialogo visualizzata scegliere **Sì** per confermare la disinstallazione dell'estensione.

4. Scegliere **Riavvia ora** per completare la disinstallazione.

5. Chiudere entrambe le istanze Visual Studio (l'istanza sperimentale e l'istanza in cui è aperta la soluzione GenerateExternalDataLists).

## <a name="see-also"></a>Vedi anche
- [Estendere il SharePoint di progetto](../sharepoint/extending-the-sharepoint-project-system.md)
- [Creare un modello di connettività dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Progettare un modello di connettività dei dati aziendali](../sharepoint/designing-a-business-data-connectivity-model.md)