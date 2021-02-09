---
title: "Procedura dettagliata: creazione di un'estensione di progetto SharePoint | Microsoft Docs"
description: Creare un'estensione di progetto SharePoint, che è possibile utilizzare per rispondere agli eventi a livello di progetto, ad esempio quando un progetto viene aggiunto, eliminato o rinominato.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 378e839ea5f4223873fbbeec8d7b401ae0b16fc0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918755"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>Procedura dettagliata: creare un'estensione di progetto SharePoint
  In questa procedura dettagliata viene illustrato come creare un'estensione per i progetti SharePoint. È possibile usare un'estensione di progetto per rispondere a eventi a livello di progetto, ad esempio quando un progetto viene aggiunto, eliminato o rinominato. È anche possibile aggiungere proprietà personalizzate o rispondere quando viene modificato il valore di una proprietà. Diversamente dalle estensioni di elementi di progetto, le estensioni di progetto non possono essere associate a un particolare tipo di progetto SharePoint. Quando si crea un'estensione di progetto, l'estensione viene caricata quando un qualsiasi tipo di progetto SharePoint viene aperto in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 In questa procedura dettagliata verrà creata una proprietà booleana personalizzata che viene aggiunta a qualsiasi progetto SharePoint creato in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Quando è impostato su **true**, la nuova proprietà aggiunge, o esegue il mapping, una cartella delle risorse images al progetto. Se è impostato su **false**, la cartella images viene rimossa, se esistente. Per altre informazioni, vedere [procedura: aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un' [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] estensione per i progetti SharePoint che esegue le operazioni seguenti:

  - Aggiunge una proprietà di progetto personalizzata al Finestra Proprietà. La proprietà si applica a qualsiasi progetto SharePoint.

  - Usa il modello a oggetti del progetto SharePoint per aggiungere una cartella mappata a un progetto.

  - Usa il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modello a oggetti di automazione (DTE) per eliminare una cartella mappata dal progetto.

- Compilazione di un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per distribuire l'assembly dell'estensione della proprietà del progetto.

- Debug e test della proprietà del progetto.

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario che nel computer di sviluppo siano presenti i componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] , SharePoint e [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Oggetto [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Questa procedura dettagliata usa il modello di **progetto VSIX** in [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] per creare un pacchetto VSIX per distribuire l'estensione della proprietà del progetto. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare due progetti:

- Progetto VSIX per creare il pacchetto VSIX per distribuire l'estensione del progetto.

- Progetto di libreria di classi che implementa l'estensione del progetto.

  Avviare la procedura dettagliata creando i progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto**.

3. Nella finestra di dialogo **nuovo progetto** espandere i nodi **Visual C#** o **Visual Basic** , quindi scegliere il nodo **estensibilità** .

    > [!NOTE]
    > Questo nodo è disponibile solo se si installa Visual Studio SDK. Per ulteriori informazioni, vedere la sezione Prerequisiti più indietro in questo argomento.

4. Nella parte superiore della finestra di dialogo scegliere **.NET Framework 4,5** nell'elenco di versioni del .NET Framework, quindi scegliere il modello di **progetto VSIX** .

5. Nella casella **nome** immettere **ProjectExtensionPackage**, quindi scegliere il pulsante **OK** .

     Il progetto **ProjectExtensionPackage** viene visualizzato in **Esplora soluzioni**.

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo soluzione, scegliere **Aggiungi**, quindi scegliere **nuovo progetto**.

2. Nella finestra di dialogo **nuovo progetto** espandere i nodi **Visual C#** o **Visual Basic** , quindi scegliere **Windows**.

3. Nella parte superiore della finestra di dialogo scegliere **.NET Framework 4,5** nell'elenco di versioni del .NET Framework, quindi scegliere il modello di progetto **libreria di classi** .

4. Nella casella **nome** immettere **ProjectExtension**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **ProjectExtension** alla soluzione e apre il file di codice Class1 predefinito.

5. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-project"></a>Configurare il progetto
 Prima di scrivere il codice per creare l'estensione del progetto, aggiungere i file di codice e i riferimenti ad assembly al progetto di estensione.

#### <a name="to-configure-the-project"></a>Per configurare il progetto

1. Aggiungere un file di codice denominato **CustomProperty** al progetto ProjectExtension.

2. Aprire il menu di scelta rapida per il progetto **ProjectExtension** , quindi scegliere **Aggiungi riferimento**.

3. Nella finestra di dialogo **Gestione riferimenti-CustomProperty** , scegliere il nodo **Framework** , quindi selezionare la casella di controllo accanto agli assembly System. ComponentModel. Composition e System. Windows. Forms.

4. Scegliere il nodo **estensioni** , selezionare la casella di controllo accanto agli assembly Microsoft. VisualStudio. SharePoint e EnvDTE, quindi scegliere il pulsante **OK** .

5. In **Esplora soluzioni**, nella cartella **riferimenti** per il progetto **ProjectExtension** , scegliere **EnvDTE**.

6. Nella finestra **Proprietà** modificare la proprietà **Incorpora tipi di interoperabilità** su **false**.

## <a name="define-the-new-sharepoint-project-property"></a>Definire la nuova proprietà del progetto SharePoint
 Creare una classe che definisce l'estensione del progetto e il comportamento della nuova proprietà del progetto. Per definire la nuova estensione di progetto, la classe implementa l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaccia. Implementare questa interfaccia quando si desidera definire un'estensione per un progetto SharePoint. Aggiungere inoltre alla <xref:System.ComponentModel.Composition.ExportAttribute> classe. Questo attributo consente [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a di individuare e caricare l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> tipo al costruttore dell'attributo.

#### <a name="to-define-the-new-sharepoint-project-property"></a>Per definire la proprietà del nuovo progetto SharePoint

1. Incollare il codice seguente nel file di codice CustomProperty.

     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]

## <a name="build-the-solution"></a>Compilare la soluzione
 Successivamente, compilare la soluzione per assicurarsi che venga compilata senza errori.

#### <a name="to-build-the-solution"></a>Per compilare la soluzione

1. Sulla barra dei menu scegliere **Compila**  >  **Compila soluzione**.

## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>Creare un pacchetto VSIX per distribuire l'estensione della proprietà del progetto
 Per distribuire l'estensione di progetto, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Per prima cosa, configurare il pacchetto VSIX modificando il file source. Extension. vsixmanifest incluso nel progetto VSIX. Quindi, creare il pacchetto VSIX compilando la soluzione.

#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il file source. Extension. vsixmanifest, quindi scegliere il pulsante **Apri** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre il file nella finestra di progettazione del manifesto. Le informazioni visualizzate nella scheda **metadati** vengono visualizzate anche in **estensioni e aggiornamenti**. Tutti i pacchetti VSIX richiedono il file Extension. vsixmanifest. Per altre informazioni su questo file, vedere [riferimento allo schema di estensione VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. Nella casella **nome prodotto** immettere **Proprietà progetto personalizzato**.

3. Nella casella **autore** immettere **Contoso**.

4. Nella casella **Descrizione** immettere **una proprietà del progetto SharePoint personalizzata che consente di attivare o disabilitare il mapping della cartella delle risorse immagini al progetto**.

5. Scegliere la scheda **Asset** , quindi scegliere il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

6. Nell'elenco **tipo** scegliere **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Questo valore corrisponde all' `MEFComponent` elemento nel file Extension. vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per altre informazioni, vedere [Elemento MEFComponent (schema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Nell'elenco **origine** scegliere il pulsante di opzione **progetto in una soluzione corrente** .

8. Nell'elenco **progetto** scegliere **ProjectExtension**.

     Questo valore identifica il nome dell'assembly che si sta compilando nel progetto.

9. Scegliere **OK** per chiudere la finestra di dialogo **Aggiungi nuovo asset** .

10. Nella barra dei menu scegliere **file**  >  **Salva tutto** al termine e quindi chiudere la finestra di progettazione del manifesto.

11. Sulla barra dei **menu scegliere Compila compila**  >  **soluzione**, quindi assicurarsi che il progetto venga compilato senza errori.

12. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto **ProjectExtensionPackage** e scegliere il pulsante **Apri cartella in Esplora file** .

13. In **Esplora file** aprire la cartella di output di compilazione per il progetto ProjectExtensionPackage e quindi verificare che la cartella contenga un file denominato ProjectExtensionPackage. vsix.

     Per impostazione predefinita, la cartella di output di compilazione è.. cartella \bin\Debug nella cartella che contiene il file di progetto.

## <a name="test-the-project-property"></a>Testare la proprietà del progetto
 A questo punto si è pronti per testare la proprietà del progetto personalizzato. È più semplice eseguire il debug e testare la nuova estensione della proprietà del progetto in un'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Questa istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] viene creata quando si esegue un progetto VSIX o un altro progetto di estendibilità. Dopo aver eseguito il debug del progetto, è possibile installare l'estensione nel sistema e continuare a eseguire il debug e testarla in un'istanza di normale [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Per eseguire il debug e il test dell'estensione in un'istanza sperimentale di Visual Studio

1. Riavviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenziali amministrative, quindi aprire la soluzione ProjectExtensionPackage.

2. Avviare una build di debug del progetto scegliendo il tasto **F5** oppure, sulla barra dei menu, scegliendo **debug**  >  **Avvia debug**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] installa l'estensione nel progetto%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Property\1.0 e avvia un'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

3. Nell'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] creare un progetto SharePoint per una soluzione farm e utilizzare i valori predefiniti per gli altri valori nella procedura guidata.

    1. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto**.

    2. Nella parte superiore della finestra di dialogo **nuovo progetto** scegliere **.NET Framework 3,5** nell'elenco delle versioni del .NET Framework.

         Le estensioni degli strumenti di SharePoint richiedono funzionalità in questa versione di [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

    3. Nel nodo **modelli** espandere il nodo **Visual C#** o **Visual Basic** , scegliere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

    4. Scegliere il modello di **progetto SharePoint 2010** , quindi immettere **ModuleTest** come nome del progetto.

4. In **Esplora soluzioni** scegliere il nodo del progetto **ModuleTest** .

     Viene visualizzata una nuova **cartella immagini della mappa** delle proprietà personalizzata nella finestra **Proprietà** con il valore predefinito **false**.

5. Modificare il valore di tale proprietà su **true**.

     Una cartella delle risorse images viene aggiunta al progetto SharePoint.

6. Modificare nuovamente il valore della proprietà in **false**.

     Se si sceglie il pulsante **Sì** nella finestra di dialogo **Elimina cartella immagini?** , la cartella delle risorse immagini verrà eliminata dal progetto SharePoint.

7. Chiudere l'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

## <a name="see-also"></a>Vedi anche
- [Estensione di progetti SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Conversione tra tipi di sistemi di progetto SharePoint e altri tipi di progetto di Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Salvare i dati nelle estensioni del sistema di progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Associare dati personalizzati alle estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)