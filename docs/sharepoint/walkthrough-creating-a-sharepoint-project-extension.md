---
title: 'Procedura dettagliata: Creazione di un SharePoint Project di | Microsoft Docs'
description: Creare un SharePoint di progetto, che è possibile usare per rispondere agli eventi a livello di progetto, ad esempio quando un progetto viene aggiunto, eliminato o rinominato.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 6db7829524b43718d8c41afa7792b86bc589c75c7874bc2e447f9093d4016370
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121244225"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>Procedura dettagliata: Creare un'estensione SharePoint progetto
  Questa procedura dettagliata illustra come creare un'estensione per SharePoint progetti. È possibile usare un'estensione di progetto per rispondere agli eventi a livello di progetto, ad esempio quando un progetto viene aggiunto, eliminato o rinominato. È anche possibile aggiungere proprietà personalizzate o rispondere quando cambia il valore di una proprietà. A differenza delle estensioni degli elementi di progetto, le estensioni di progetto non possono essere associate a un tipo di SharePoint specifico. Quando si crea un'estensione di progetto, l'estensione viene caricata quando un SharePoint progetto viene aperto in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 In questa procedura dettagliata verrà creata una proprietà booleana personalizzata che viene aggiunta a qualsiasi SharePoint creato in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Se impostata **su True,** la nuova proprietà aggiunge o esegue il mapping di una cartella di risorse Images al progetto. Se impostato su **False,** la cartella Images viene rimossa, se esistente. Per altre informazioni, vedere [Procedura: aggiungere e rimuovere cartelle mappate.](../sharepoint/how-to-add-and-remove-mapped-folders.md)

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] un'estensione per SharePoint che esegue le operazioni seguenti:

  - Aggiunge una proprietà di progetto personalizzata all'Finestra Proprietà. La proprietà si applica a qualsiasi SharePoint progetto.

  - Usa il SharePoint a oggetti del progetto per aggiungere una cartella mappata a un progetto.

  - Usa il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modello a oggetti di automazione (DTE) per eliminare una cartella mappata dal progetto.

- Compilazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] un pacchetto di estensione (VSIX) per distribuire l'assembly di estensione della proprietà del progetto.

- Debug e test della proprietà del progetto.

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, sono necessari i componenti seguenti nel computer di sviluppo:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] , SharePoint e [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Oggetto [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Questa procedura dettagliata usa il **modello di Project VSIX** in per [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] creare un pacchetto VSIX per distribuire l'estensione della proprietà del progetto. Per altre informazioni, vedere [Estendere gli strumenti SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario creare due progetti:

- Progetto VSIX per creare il pacchetto VSIX per distribuire l'estensione di progetto.

- Progetto di libreria di classi che implementa l'estensione di progetto.

  Avviare la procedura dettagliata creando i progetti.

#### <a name="to-create-the-vsix-project"></a>Per creare il progetto VSIX

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Sulla barra dei menu scegliere **File**  >  **nuovo**  >  **Project**.

3. Nella finestra **di dialogo Nuovo Project** espandere i nodi Visual **C#** o **Visual Basic** e quindi scegliere il nodo **Estendibilità.**

    > [!NOTE]
    > Questo nodo è disponibile solo se si installa Visual Studio SDK. Per altre informazioni, vedere la sezione dei prerequisiti più indietro in questo argomento.

4. Nella parte superiore della finestra di dialogo scegliere **.NET Framework 4.5** nell'elenco delle versioni del .NET Framework e quindi scegliere il modello di Project **VSIX.**

5. Nella casella **Nome** immettere **ProjectExtensionPackage** e quindi fare clic sul **pulsante OK.**

     Il **progetto ProjectExtensionPackage** viene visualizzato in **Esplora soluzioni**.

#### <a name="to-create-the-extension-project"></a>Per creare il progetto di estensione

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo della soluzione, scegliere Aggiungi **e** quindi nuovo **Project**.

2. Nella finestra **di dialogo Nuovo Project** espandere i nodi Visual **C#** o **Visual Basic** e quindi scegliere **Windows**.

3. Nella parte superiore della finestra di dialogo scegliere **.NET Framework 4.5** nell'elenco delle versioni del .NET Framework e quindi scegliere il modello **di** progetto Libreria di classi.

4. Nella casella **Nome** immettere **ProjectExtension** e quindi fare clic sul **pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto ProjectExtension** alla soluzione e apre il file di codice Class1 predefinito.

5. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-project"></a>Configurare il progetto
 Prima di scrivere codice per creare l'estensione di progetto, aggiungere i file di codice e i riferimenti all'assembly al progetto di estensione.

#### <a name="to-configure-the-project"></a>Per configurare il progetto

1. Aggiungere un file di codice denominato **CustomProperty** al progetto ProjectExtension.

2. Aprire il menu di scelta rapida per **il progetto ProjectExtension** e quindi scegliere **Aggiungi riferimento**.

3. Nella finestra di dialogo Gestione riferimenti **- CustomProperty** scegliere il **nodo Framework** e quindi selezionare la casella di controllo accanto a System.ComponentModel.Composition e System. Windows. Assembly del form.

4. Scegliere il **nodo Estensioni** e selezionare la casella di controllo accanto a Microsoft.VisualStudio. SharePoint assembly EnvDTE e quindi scegliere **OK.**

5. In **Esplora soluzioni**, nella **cartella Riferimenti** per il progetto **ProjectExtension** scegliere **EnvDTE**.

6. Nella finestra **Proprietà** modificare la proprietà **Incorpora tipi di interoperabilità** in **False**.

## <a name="define-the-new-sharepoint-project-property"></a>Definire la nuova proprietà SharePoint progetto
 Creare una classe che definisce l'estensione di progetto e il comportamento della nuova proprietà del progetto. Per definire la nuova estensione di progetto, la classe implementa <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> l'interfaccia . Implementare questa interfaccia ogni volta che si vuole definire un'estensione per un SharePoint progetto. Aggiungere anche alla <xref:System.ComponentModel.Composition.ExportAttribute> classe . Questo attributo consente [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] di individuare e caricare l'implementazione. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Passare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> tipo al costruttore dell'attributo.

#### <a name="to-define-the-new-sharepoint-project-property"></a>Per definire la nuova proprietà SharePoint progetto

1. Incollare il codice seguente nel file di codice CustomProperty.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs" id="Snippet1":::

## <a name="build-the-solution"></a>Compilare la soluzione
 Compilare quindi la soluzione per assicurarsi che venga compilata senza errori.

#### <a name="to-build-the-solution"></a>Per compilare la soluzione

1. Sulla barra dei menu scegliere **Compila**  >  **soluzione**.

## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>Creare un pacchetto VSIX per distribuire l'estensione di proprietà del progetto
 Per distribuire l'estensione di progetto, usare il progetto VSIX nella soluzione per creare un pacchetto VSIX. Configurare innanzitutto il pacchetto VSIX modificando il file source.extension.vsixmanifest incluso nel progetto VSIX. Creare quindi il pacchetto VSIX compilando la soluzione.

#### <a name="to-configure-and-create-the-vsix-package"></a>Per configurare e creare il pacchetto VSIX

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il file source.extension.vsixmanifest e quindi scegliere il **pulsante** Apri.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre il file nella finestra di progettazione del manifesto. Le informazioni visualizzate nella **scheda Metadati** vengono visualizzate anche in Estensioni **e aggiornamenti**. Tutti i pacchetti VSIX richiedono il file extension.vsixmanifest. Per altre informazioni su questo file, vedere Informazioni di riferimento sullo [schema dell'estensione VSIX 1.0.](/previous-versions/dd393700(v=vs.110))

2. Nella casella **Product Name (Nome** prodotto) immettere **Custom Project Property (Proprietà Project personalizzata).**

3. Nella casella **Autore** immettere **Contoso**.

4. Nella casella **Descrizione** immettere una proprietà SharePoint progetto personalizzato che attiva o disattiva il mapping della cartella **della risorsa Images al progetto**.

5. Scegliere la **scheda Asset** e quindi fare clic **sul pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

6. **Nell'elenco Tipo** scegliere **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    > Questo valore corrisponde `MEFComponent` all'elemento nel file extension.vsixmanifest. Questo elemento specifica il nome di un assembly di estensione nel pacchetto VSIX. Per altre informazioni, vedere [Elemento MEFComponent (schema VSX).](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))

7. **Nell'elenco Origine** scegliere il **pulsante di opzione Un progetto nella soluzione** corrente.

8. **Nell'Project** scegliere **ProjectExtension**.

     Questo valore identifica il nome dell'assembly che si sta compilando nel progetto.

9. Scegliere **OK** per chiudere la **finestra di dialogo Aggiungi** nuovo asset.

10. Al termine, scegliere Salva tutto **dalla** barra dei menu e quindi chiudere la finestra di progettazione  >   del manifesto.

11. Sulla barra dei menu scegliere **Compila** soluzione e quindi assicurarsi che  >  il progetto venga compilato senza errori.

12. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto **ProjectExtensionPackage** e scegliere il pulsante **Apri cartella in** Esplora file.

13. In **Esplora file** aprire la cartella di output di compilazione per il progetto ProjectExtensionPackage e quindi verificare che la cartella contenga un file denominato ProjectExtensionPackage.vsix.

     Per impostazione predefinita, la cartella dell'output di compilazione è . Cartella \bin\Debug nella cartella che contiene il file di progetto.

## <a name="test-the-project-property"></a>Testare la proprietà del progetto
 A questo punto è possibile testare la proprietà del progetto personalizzato. È più semplice eseguire il debug e testare la nuova estensione di proprietà del progetto in un'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Questa istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] viene creata quando si esegue un vsix o un altro progetto di estendibilità. Dopo aver eseguono il debug del progetto, è possibile installare l'estensione nel sistema e quindi continuare a eseguirne il debug e il test in un'istanza regolare di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Per eseguire il debug e il test dell'estensione in un'istanza sperimentale di Visual Studio

1. Riavviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenziali amministrative e quindi aprire la soluzione ProjectExtensionPackage.

2. Avviare una build di debug del progetto scegliendo il tasto **F5** o, sulla barra dei menu, scegliendo **Debug**  >  **Avvia debug**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]installa l'estensione in %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Project Property\1.0 e avvia un'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

3. Nell'istanza sperimentale di creare un SharePoint per una soluzione farm e usare i valori predefiniti per gli altri [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] valori della procedura guidata.

    1. Sulla barra dei menu scegliere **File**  >  **nuovo**  >  **Project**.

    2. Nella parte superiore della **finestra di dialogo Nuovo Project** scegliere .NET Framework **3.5** nell'elenco delle versioni del .NET Framework.

         SharePoint estensioni degli strumenti richiedono funzionalità in questa versione di [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

    3.  Nel nodo **Modelli** espandere il nodo Visual **C#** o **Visual Basic,** scegliere il nodo SharePoint e quindi scegliere il nodo **2010.**

    4. Scegliere il SharePoint modello Project **2010** e quindi immettere **ModuleTest** come nome del progetto.

4. In **Esplora soluzioni** scegliere il **nodo del progetto ModuleTest.**

     Nella finestra Proprietà viene visualizzata  una nuova proprietà personalizzata **Map Images Folder** con il valore predefinito **False**.

5. Modificare il valore di tale proprietà in **True.**

     Una cartella di risorse Images viene aggiunta al SharePoint progetto.

6. Modificare il valore di tale proprietà su **False.**

     Se si sceglie il **pulsante** Sì nella finestra di dialogo Elimina la cartella **Immagini?** , la cartella della risorsa Immagini viene eliminata dal SharePoint progetto.

7. Chiudere l'istanza sperimentale di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

## <a name="see-also"></a>Vedi anche
- [Estendere SharePoint progetti](../sharepoint/extending-sharepoint-projects.md)
- [Procedura: Aggiungere una proprietà ai SharePoint progetto](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Eseguire la conversione SharePoint tipi di sistema del progetto e altri Visual Studio di progetto](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Salvare i dati nelle estensioni del sistema SharePoint progetto](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Associare dati personalizzati alle estensioni SharePoint strumenti di configurazione](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)