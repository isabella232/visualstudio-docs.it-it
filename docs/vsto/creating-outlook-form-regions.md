---
title: Creare aree Outlook modulo
description: Informazioni su come usare le aree del modulo per personalizzare i moduli Outlook Microsoft per semplificarne la progettazione, lo sviluppo e il debug.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio]
- form regions [Office development in Visual Studio], creating
- Outlook [Office development in Visual Studio], form regions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 99049652ba378bf3a73a73412369145a0f695b9d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047127"
---
# <a name="create-outlook-form-regions"></a>Creare aree Outlook modulo
  È possibile usare aree del modulo per personalizzare i moduli di Microsoft Office Outlook. Visual Studio fornisce strumenti avanzati che semplificano la progettazione, lo sviluppo e il debug delle aree del modulo.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Questo argomento contiene informazioni sui seguenti aspetti:

- [Vantaggi dell'uso delle aree del modulo](#Enhance)

- [Aggiungere un Outlook'area del modulo al progetto](#Adding)

- [Usare la finestra di progettazione dell'area del modulo](#UsingFormRegionDesigner)

- [Usare un'area del modulo progettata in Outlook](#UsingFormRegionDesignedOutlook)

- [Aggiungere codice personalizzato a un'area del modulo](#AddingCustomCode)

- [Compilare il progetto](#Building)

- [Eseguire il debug di un'area del modulo](#Debugging)

- [Distribuire un'area del modulo](#Deploying)

## <a name="advantages-of-using-form-regions"></a><a name="Enhance"></a> Vantaggi dell'uso delle aree del modulo
 Le aree del modulo offrono numerosi miglioramenti rispetto allo sviluppo di moduli Outlook tradizionali:

- Personalizzare la pagina predefinita di qualsiasi modulo standard.

- Aggiungere fino a 12 pagine aggiuntive a qualsiasi modulo standard.

- Sostituire o migliorare un modulo standard.

- Visualizzare l'interfaccia utente personalizzata nel riquadro di lettura e nei controlli.

  Per altre informazioni, vedere [Personalizzare le pagine del modulo e le aree del modulo.](/office/vba/outlook/Concepts/Forms/customizing-form-pages-and-form-regions)

## <a name="add-an-outlook-form-region-to-your-project"></a><a name="Adding"></a>Aggiungere un Outlook'area del modulo al progetto
 È possibile usare la procedura **guidata Nuova** area Outlook modulo per progettare una nuova area del modulo o importare un'area del modulo progettata in Outlook. È anche possibile riutilizzare un'area del modulo esistente, precedentemente usata in un altro progetto di componente aggiuntivo VSTO di Outlook.

### <a name="create-a-new-form-region-by-using-the-wizard"></a><a name="CreatingFormRegion"></a> Creare una nuova area del modulo usando la procedura guidata
 Per creare un'area del modulo, aggiungere **Outlook'area del** modulo a un progetto Outlook VSTO componente aggiuntivo. Verrà avviata la **procedura guidata Nuova area Outlook modulo.**

 Usare la procedura guidata per indicare se si vuole progettare una nuova area del modulo o importare un'area del modulo progettata in Outlook. Per altre informazioni sulla progettazione di una nuova area del modulo, vedere [Usare la finestra di progettazione dell'area del modulo](#UsingFormRegionDesigner). Per altre informazioni sull'uso di un'area del modulo progettata in Outlook, vedere [Importare un'area del](#UsingFormRegionDesignedOutlook)modulo progettata in Outlook .

 Usare la procedura guidata per specificare il tipo di area del modulo da creare. La tabella seguente descrive ciascun tipo di area del modulo.

|Tipo di area|Descrizione|
|-----------------|-----------------|
|Separa|Aggiunge l'area del modulo come una nuova pagina a un modulo di Outlook.|
|Adiacente|Aggiunge l'area del modulo alla parte inferiore della pagina predefinita di un modulo di Outlook.|
|Sostituzione|Aggiunge l'area del modulo come una nuova pagina che sostituisce la pagina predefinita di un modulo di Outlook.|
|Sostituzione completa|Sostituisce l'intero modulo di Outlook con l'area del modulo.|

 È anche possibile usare la procedura guidata per specificare le condizioni di visualizzazione e selezionare il tipo di modulo da estendere. Per altre informazioni, [vedere Procedura: Aggiungere un'area del modulo a](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)un progetto Outlook componente aggiuntivo .

 Le selezioni effettuate nella procedura guidata influiscono sulle opzioni disponibili in altre pagine della procedura guidata. Ad esempio, se si seleziona  Adiacente o Separato nella pagina Crea una nuova area  del modulo **Outlook,** i campi **Titolo** e Descrizione non sono disponibili nella pagina Specifica testo descrittivo e selezionare le preferenze di **visualizzazione.**  Questo avviene perché Outlook non usa questi campi quando viene visualizzata un'area del modulo adiacente o separata.

#### <a name="form-region-files"></a>File dell'area del modulo
 Al termine della procedura **guidata Nuova area Outlook modulo,** Visual Studio automaticamente i file seguenti al progetto:

- Un file di codice dell'area del modulo. Questo file ha il nome specificato per l'Outlook **dell'area del** modulo nella finestra **di** dialogo Aggiungi nuovo elemento . Aggiungere a questo file il codice per gestire gli eventi dell'area del modulo.

- Un file di codice di Progettazione aree di form. Questo file contiene il codice generato da Progettazione aree di form e non può essere modificato direttamente.

- Un Outlook Form Archiviazione (*ofs*).

    > [!NOTE]
    > Questo file viene aggiunto al progetto solo se si importa un'area del modulo progettata in Outlook.

#### <a name="form-region-factory-class"></a>Classe factory dell'area del modulo
 Il file di codice dell'area del modulo contiene una classe parziale che implementa l'interfaccia <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory>. Si tratta della classe factory dell'area del modulo che è responsabile della creazione di nuove istanze dell'area del modulo.

 È possibile trovare questa classe espandendo **l'area Factory dell'area del** modulo.

 La **procedura guidata Nuova Outlook'area** del modulo aggiunge attributi a questa classe che specificano il nome interno dell'area del modulo e le classi di messaggio che visualizzano l'area del modulo. È possibile modificare manualmente questi attributi dopo che il file è stato aggiunto al progetto.

 La maggior parte della classe factory dell'area del modulo è implementata nel file di Progettazione aree di form. Tuttavia, il gestore eventi `FormRegionInitializing` è esposto nel file di codice dell'area del modulo e può essere usato per specificare se l'area del modulo deve essere visualizzata in Outlook. Per altre informazioni, vedere [Gestire gli eventi dell'area del modulo.](#HandlingFormRegionEvents)

### <a name="add-an-existing-form-region-to-your-project"></a><a name="AddingExistingFormRegion"></a> Aggiungere un'area del modulo esistente al progetto
 Un'area del modulo di Outlook di un altro progetto di Outlook può essere riutilizzata nel progetto corrente di componente aggiuntivo VSTO per Outlook con la finestra di dialogo **Aggiungi elemento esistente** .

 L'area del modulo esistente deve avere un file di codice (*vb* o *cs*). Non è possibile aggiungere Outlook file Archiviazione form (*ofs*) usando la finestra di dialogo **Aggiungi** elemento esistente . Tuttavia, è possibile creare un'area del modulo nuova importando un file ofs (Outlook From Storage). Per altre informazioni, [vedere Procedura: Aggiungere un'area del modulo a](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)un progetto Outlook componente aggiuntivo .

## <a name="use-the-form-region-designer"></a><a name="UsingFormRegionDesigner"></a> Usare la finestra di progettazione dell'area del modulo
 Progettazione aree di form consente di configurare il layout e l'aspetto di un'area del modulo. È possibile trascinare i controlli gestiti nell'area della finestra di progettazione, fare doppio clic sui controlli per aprire i gestori eventi e impostare le proprietà nella **finestra** Proprietà.

> [!NOTE]
> È possibile trovare le proprietà che influiscono sul modo in cui l'area del modulo viene visualizzata Outlook sotto il **nodo** Manifesto nella **finestra** Proprietà.

 La finestra di progettazione dell'area del modulo è  disponibile solo se si seleziona Progetta una nuova area del modulo nella pagina Selezionare la modalità di creazione dell'area del modulo della procedura guidata Nuova area modulo Outlook **modulo.** 

 È possibile aprire Progettazione aree di form in tre modi diversi:

- In **Esplora soluzioni** fare doppio clic sul file di codice dell'area del modulo.

- In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file di codice dell'area del modulo e **quindi scegliere Progettazione visualizzazioni**.

- In **Esplora soluzioni** selezionare il file di codice dell'area del modulo e quindi scegliere Progettazione dal **menu** **Visualizza**.

  Progettazione aree di form supporta solo i controlli gestiti. Non è possibile aggiungere controlli nativi di Outlook.

## <a name="import-a-form-region-designed-in-outlook"></a><a name="UsingFormRegionDesignedOutlook"></a>Importare un'area del modulo progettata in Outlook
 Quando si progetta in Outlook, è possibile aggiungere all'area del modulo i controlli nativi di Outlook che consentono di effettuare associazioni ai dati di Outlook in fase di progettazione. Tuttavia, non si potrà usare in seguito Progettazione aree di form per aggiungere i controlli gestiti o modificare la progettazione dell'area del modulo.

 È possibile importare aree del modulo in Outlook VSTO progetto di componente aggiuntivo usando la procedura **guidata Nuova Outlook'area del modulo.** Nella pagina **Selezionare la modalità di creazione dell'area** del modulo selezionare Importa un file Outlook Form Archiviazione **(ofs).** È quindi possibile passare al percorso di un file Outlook Form Archiviazione file *(ofs).* (Outlook salva le aree del modulo *come file con estensione ofs.*

 La **procedura guidata Nuova Outlook'area** del modulo copia il file con estensione *ofs* nella directory del progetto e aggiunge i riferimenti al controllo al file di progettazione dell'area del modulo. È possibile quindi gestire gli eventi di controllo nel file di codice dell'area del modulo.

 Per gestire gli eventi in un progetto Visual Basic, selezionare un evento dall'elenco dei nomi di metodo nella parte superiore dell'editor di codice.

 Per gestire gli eventi in un progetto C#, sottoscrivere gli eventi di controllo nel metodo <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>. Per altre informazioni, vedere [Procedura: ](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events)Sottoscrivere e annullare la sottoscrizione di eventi &#40;C&#35; di programmazione&#41;.

 È possibile modificare le proprietà dell'area del modulo nel metodo `InitializeManifest` della classe factory dell'area del modulo.

> [!NOTE]
> Per importare un'area del modulo, è necessario lavorare a un progetto destinato alla stessa versione di Outlook installata nel computer di sviluppo. Se, ad esempio, Outlook 2010 è installato, l'importazione di un'area del modulo funzionerà solo in un progetto creato usando il modello di progetto componente aggiuntivo **Outlook 2010.**

### <a name="update-an-imported-form-regions-design"></a>Aggiornare la progettazione di un'area del modulo importata
 È possibile aggiungere, rimuovere o modificare i controlli dell'area del modulo. Prima di eseguire queste operazioni, effettuare il backup del codice aggiunto al file di codice dell'area del modulo. Aprire quindi il file con estensione *ofs* in Outlook, modificare l'area del modulo e quindi salvare le modifiche. Usare la **procedura guidata Nuova Outlook'area del** modulo per importare il file con estensione *ofs* modificato. È quindi possibile incollare il codice nel file di codice della nuova area del modulo.

## <a name="add-custom-code-to-a-form-region"></a><a name="AddingCustomCode"></a> Aggiungere codice personalizzato a un'area del modulo
 Lo spazio dei nomi <xref:Microsoft.Office.Tools.Outlook> fornisce l'accesso alle classi che rappresentano l'area del modulo, all'elemento di Outlook che visualizza l'area del modulo e ad altri elementi utili. **L Outlook'area** del modulo aggiunge automaticamente un riferimento a questo assembly nel progetto e inserisce l'istruzione **using** o **Imports** appropriata nella parte superiore del file di codice dell'area del modulo.

 È possibile usare classi, metodi e proprietà nello spazio dei nomi `Microsoft.Office.Interop.Outlook` per eseguire la maggior parte delle attività di programmazione di Outlook. Per altre informazioni sul modello Outlook a oggetti, vedere panoramica Outlook [modello a oggetti](../vsto/outlook-object-model-overview.md). Per esempi di attività tipiche che usano il modello Outlook a oggetti, vedere Outlook [soluzioni](../vsto/outlook-solutions.md).

### <a name="handle-form-region-events"></a><a name="HandlingFormRegionEvents"></a> Gestire gli eventi dell'area del modulo
 **L Outlook'area del** modulo aggiunge automaticamente i tre gestori eventi seguenti al file di codice dell'area del modulo.

|Event|Descrizione|
|-----------|-----------------|
|FormRegionInitializing|Si verifica prima dell'inizializzazione dell'area del form. È possibile selezionare le condizioni di questo gestore eventi per determinare se l'area del modulo deve essere visualizzata in Outlook. Per altre informazioni, vedere [Procedura: Impedire Outlook di visualizzare un'area del modulo.](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|
|FormRegionShowing|Si verifica dopo la creazione di un'istanza dell'area del modulo, ma prima della visualizzazione dell'area del modulo.|
|FormRegionClosed|Si verifica prima della chiusura dell'area del modulo.|

## <a name="build-the-project"></a><a name="Building"></a> Compilare il progetto
 Quando si compila un progetto di componente aggiuntivo VSTO per Outlook contenente un'area del modulo, Visual Studio aggiunge le informazioni seguenti al Registro di sistema:

- Una chiave per ogni classe di messaggi associata a una o più aree del modulo.

- Una voce per ogni area del modulo e un valore associato che rappresenta il nome del componente aggiuntivo VSTO di Outlook.

  Outlook usa queste informazioni per caricare le aree del modulo.

## <a name="debug-a-form-region"></a><a name="Debugging"></a> Eseguire il debug di un'area del modulo
 È possibile eseguire il debug di un componente aggiuntivo VSTO di Outlook contenente un'area del modulo proprio come se si trattasse del debug di altri progetti [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. All'avvio del debugger di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Visual Studio avvia automaticamente Outlook.

 Per visualizzare l'area del modulo è necessario aprire l'elemento di Outlook appropriato. Ad esempio, se un'area del modulo adiacente viene aggiunta alla fine di un elemento di posta, aprire un elemento di posta.

## <a name="deploy-a-form-region"></a><a name="Deploying"></a> Distribuire un'area del modulo
 Le aree del modulo sono distribuite automaticamente con il componente aggiuntivo VSTO di Outlook associato. Non è quindi necessario eseguire un'attività particolare per distribuire un'area del modulo. Per altre informazioni sulla distribuzione VSTO componenti aggiuntivi, vedere [Distribuire una Office soluzione](../vsto/deploying-an-office-solution.md).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Linee guida per la creazione di aree Outlook modulo](../vsto/guidelines-for-creating-outlook-form-regions.md)|Fornisce informazioni che consentono di ottimizzare le aree del modulo ed evitare eventuali problemi.|
|[Procedura: Aggiungere un'area del modulo a un progetto Outlook componente aggiuntivo](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Viene illustrato come creare un'area del modulo per estendere un modulo di Microsoft Office Outlook standard o personalizzato usando la procedura guidata Nuova area del modulo Outlook **modulo.**|
|[Associare un'area del modulo a una Outlook di messaggio](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Illustra come specificare quali elementi di Microsoft Office Outlook consentono di visualizzare un'area del modulo associando l'area del modulo alla classe di messaggio di ogni elemento.|
|[Procedura dettagliata: Progettare un'area Outlook modulo](../vsto/walkthrough-designing-an-outlook-form-region.md)|Mostra come progettare un'area del modulo personalizzata che viene visualizzata come una nuova pagina nella finestra di controllo di un contatto.|
|[Procedura dettagliata: Importare un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Viene illustrato come progettare un'area del modulo in Microsoft Office Outlook e quindi importare l'area del modulo in un progetto di componente aggiuntivo Outlook VSTO usando la procedura **guidata** Nuova area del modulo Outlook modulo.|
|[Accedere a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)|Descrive come scrivere codice per mostrare, nascondere o modificare i controlli presenti in un'area del modulo e consentire agli utenti di eseguire il codice da altre aree del progetto usando la classe `Globals`.|
|[Procedura: Impedire Outlook di visualizzare un'area del modulo](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Illustra come impedire a Microsoft Office Outlook di visualizzare un'area del modulo per un particolare elemento.|
|Illustra come accedere all'elemento di Outlook in cui viene visualizzata un'area del modulo.|
|[Azioni personalizzate nelle aree Outlook modulo](../vsto/custom-actions-in-outlook-form-regions.md)|Descrive come consentire agli utenti di rispondere a un elemento di Outlook.|
