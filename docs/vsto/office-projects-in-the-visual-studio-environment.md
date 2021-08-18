---
title: Office progetti nell'ambiente Visual Studio
description: Informazioni su come Microsoft Office progetti hanno un'esperienza di sviluppo simile ad altri tipi di progetti in Visual Studio, ad esempio progetti Windows Form.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.WordDocument
- VST.ProjectItem.ExcelWorkbook
- VST.ProjectItem.ExcelTemplate
- VST.ProjectItem.ExcelSheet
- VST.ProjectItem.BlueprintCode
- VST.ProjectItem.Word
- VST.ProjectItem.Excel
- VST.ProjectItem.AddinProject
- Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner
- VST.ProjectItem.ExtendedBluePrint
- VST.ProjectItem.WordTemplate
- Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner
- VST.Designer.ExcelVST.Designer.Word
- VST.ProjectItem.ExtendedBlueprintCode
- VST.ProjectItem.BluePrint
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- hidden files [Office development in Visual Studio]
- project files [Office development in Visual Studio], hidden
- Office development in Visual Studio, documents in Visual Studio
- design view, Excel
- designers, Office development in Visual Studio
- Office documents [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], about documents in Visual Studio
- designers [Office development in Visual Studio]
- Word designer
- Word [Office development in Visual Studio], Word designer
- Visual Studio, Office documents in
- worksheets [Office development in Visual Studio]
- VST.Designer.ExcelVST.Designer.Word
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 1fb601543c6650fc87be15adcd7ffc2e689d575f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082855"
---
# <a name="office-projects-in-the-visual-studio-environment"></a>Office progetti nell'ambiente Visual Studio
  L'esperienza di sviluppo relativa ai progetti di Microsoft Office è simile a quella per altri tipi di progetti in Visual Studio, ad esempio progetti Windows Form. Quando si crea o si apre un progetto di Office, gli elementi del progetto vengono visualizzati in **Esplora soluzioni**. Per i progetti a livello di documento, il documento (ossia il documento di Word o la cartella di lavoro di Excel) viene aperto in Visual Studio e funziona come una finestra di progettazione visiva.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="project-items-in-solution-explorer"></a>Project elementi in Esplora soluzioni
 In un progetto a livello di documento, in **Esplora soluzioni** sono illustrati gli elementi predefiniti seguenti:

- I nodi per il documento, la cartella di lavoro e i fogli personalizzati per il progetto. Questi nodi fungono da contenitori per i file di codice associati al documento, alla cartella di lavoro e ai fogli.

- I file di codice associati al documento, alla cartella di lavoro e ai fogli personalizzato dal progetto. Nei progetti di Word i file di codice vengono associati al documento o al modello di Word. Nei progetti di Excel i file di codice vengono associati alla cartella di lavoro o al modello di Excel e a ogni foglio di lavoro e foglio grafico nella cartella di lavoro o nel modello.

- I file di progetto nascosti per i quali non è prevista la modifica diretta. Per altre informazioni, vedere [File di progetto nascosti](#hiddenfiles).

  In un progetto di componente aggiuntivo VSTO, in **Esplora soluzioni** sono illustrati gli elementi predefiniti seguenti:

- Il nodo dell'applicazione. Questo nodo ha lo stesso nome dell'applicazione host, ad esempio **Word**, **Excel** oppure **Outlook**. Il nodo dell'applicazione contiene il file di codice ThisAddIn. Fornisce anche la proprietà **Spazio dei nomi per elemento host** . Per altre informazioni su questa proprietà, vedere [Proprietà nei Office progetti](../vsto/properties-in-office-projects.md).

- Il file di codice ThisAddIn. Questo file contiene la classe `ThisAddIn` generata per il componente aggiuntivo VSTO. Per altre informazioni su questa classe, vedere [Componenti VSTO componenti aggiuntivi .](../vsto/programming-vsto-add-ins.md)

- I file di progetto nascosti per i quali non è prevista la modifica diretta. Per altre informazioni, vedere [File di progetto nascosti](#hiddenfiles).

### <a name="temporary-certificates"></a>Certificati temporanei
 I progetti di Office includono anche un certificato temporaneo denominato *Nome progetto_TemporaryKey.pfx*. Questo certificato viene usato per firmare i manifesti dell'applicazione e della distribuzione per il progetto durante lo sviluppo. Per altre informazioni, vedere [Concedere l'attendibilità Office soluzioni e](../vsto/granting-trust-to-office-solutions.md) Proteggere Office [soluzioni](../vsto/securing-office-solutions.md).

### <a name="hidden-project-files"></a><a name="hiddenfiles"></a> File di progetto nascosti
 Alcuni file di progetto sono nascosti per impostazione predefinita. Questi file vengono generati da Visual Studio e si differenziano in base al tipo di progetto. Per visualizzare i file nascosti, fare clic su **Mostra tutti i file** in **Esplora soluzioni**.

 Non modificare i file di progetto nascosti. La modifica diretta di questi file non è supportata e potrebbe danneggiare il progetto. I file di progetto nascosti vengono rigenerati ogni volta che vengono apportate determinate modifiche al documento. Se si apportano modifiche manuali a un file di progetto nascosto, tali modifiche vengono perse quando il file viene rigenerato.

## <a name="document-designer-in-document-level-projects"></a>Progettazione documenti nei progetti a livello di documento
 I progetti a livello di documento per Excel e Word forniscono una finestra di progettazione che ospita il documento associato al progetto in Visual Studio. La finestra di progettazione consente di modificare il documento senza uscire dall'ambiente di Visual Studio.

 Per aprire un documento nella finestra di progettazione, fare doppio clic sul file di codice associato al documento in **Esplora soluzioni** . Ad esempio, per aprire il foglio di lavoro **Foglio1** nella finestra di progettazione in un progetto di Excel, fare doppio clic sul file di codice **Foglio1** .

 Quando si modifica il documento nella finestra di progettazione, è possibile usare la funzionalità nativa dell'applicazione di Office. Ad esempio, è possibile digitare il testo nel documento o in un foglio di lavoro oppure usare la barra multifunzione per eseguire attività quali l'aggiunta di una tabella o di un grafico. Per impostazione predefinita, per i tasti di scelta rapida viene usato automaticamente il mapping di Visual Studio. Per usare invece i mapping dei tasti di scelta rapida di Office, modificare le impostazioni in corrispondenza del nodo **Impostazioni tastiera Microsoft Office** nella finestra di dialogo **Opzioni** del menu **Strumenti** .

### <a name="controls-on-documents"></a>Controlli nei documenti
 È possibile trascinare i *controlli host* e i controlli Windows Form dalla **Casella degli strumenti** di Visual Studio all'area di progettazione del documento. I controlli host sono versioni specifiche di oggetti di Office, quali controlli del contenuto di Word e intervalli di Excel, che possono essere usati in progetti di Office creati tramite Visual Studio. I controlli host dispongono di funzionalità aggiuntive che non sono disponibili negli oggetti di Office corrispondenti, ad esempio associazione dati e ulteriori eventi.

 Per altre informazioni, vedere Panoramica degli [elementi host](../vsto/host-items-and-host-controls-overview.md) e dei controlli host e Windows dei moduli Office [documenti.](../vsto/windows-forms-controls-on-office-documents-overview.md)

### <a name="excel-worksheets-and-workbooks-in-the-designer"></a>Excel fogli di lavoro e cartelle di lavoro nella finestra di progettazione
 Quando si apre un foglio di lavoro nella finestra di progettazione, è possibile modificarlo come se fosse aperto direttamente in Excel. Se si fa doppio clic su una cella del foglio di lavoro, la cella passa alla modalità di modifica. Se si fa doppio clic su una cella che contiene un controllo host, viene aperto l'editor di codice Visual Studio genera il gestore eventi predefinito per il controllo. Per passare agli altri fogli di lavoro, è possibile fare clic sulle schede dei fogli di lavoro nella parte inferiore della finestra di progettazione.

 Quando si apre la cartella di lavoro nella finestra di progettazione, non è visualizzata alcuna area di progettazione. La visualizzazione Progettazione per la cartella di lavoro è una barra dei componenti di grandi dimensioni che occupa la finestra di progettazione.

 Alla cartella di lavoro e a ciascun foglio di lavoro è associato un file di codice. Ogni file di codice contiene una classe *elemento host* generata che rappresenta la cartella di lavoro o il foglio. Per altre informazioni, vedere [Automatizzare Excel tramite oggetti estesi.](../vsto/automating-excel-by-using-extended-objects.md)

### <a name="word-documents-in-the-designer"></a>Documenti di Word nella finestra di progettazione
 Quando si apre il documento nella finestra di progettazione, è possibile modificarlo come se fosse aperto direttamente in Word. Se si fa doppio clic su una parola nel documento, tale parola viene selezionata. Se tuttavia la parola è all'interno di un controllo host, viene aperto l'editor di codice e in Visual Studio viene generato il gestore eventi predefinito per il controllo.

 Al documento è associato un file di codice. Il file di codice contiene una classe *elemento host* generata che rappresenta il documento. Per altre informazioni, vedere [Elemento host document](../vsto/document-host-item.md).

### <a name="design-mode-vs-runtime-mode"></a>Modalità progettazione e modalità runtime
 Se aperto nell'ambiente Visual Studio, il documento è sempre in *modalità di progettazione*. È possibile eseguire alcune attività, ad esempio il trascinamento di un controllo host nell'area del documento, solo in modalità di progettazione.

 Per visualizzare il documento in *modalità runtime,* è necessario aprire l'applicazione e il documento all'esterno Visual Studio. È anche possibile compilare ed eseguire il progetto, che aprirà automaticamente il documento e l'applicazione all'esterno di Visual Studio.

## <a name="code-editor"></a>Editor di codice
 L'editor di codice consente di visualizzare e modificare i file di codice visibili nella soluzione. Questi file contengono il codice che definisce il comportamento della soluzione.

 Per altre informazioni sull'editor di codice, vedere [Scrivere codice nell'editor di codice e di testo](../ide/writing-code-in-the-code-and-text-editor.md). Per altre informazioni su come scrivere codice in progetti Office, vedere [Scrivere codice in Office soluzioni](../vsto/writing-code-in-office-solutions.md).

## <a name="properties-window"></a>Finestra Proprietà
 La finestra **Proprietà** mostra le proprietà per gli elementi del progetto selezionati in **Esplora soluzioni** e per gli elementi dell'interfaccia utente selezionati nella finestra di progettazione, ad esempio i controlli o il documento in un progetto a livello di documento. Alcune proprietà sono specifiche dell'applicazione e del documento, mentre altre sono identiche per tutti i progetti.

## <a name="data-sources-window"></a>Finestra Origini dati
 È possibile usare la finestra **Origini dati** all'interno dei progetti di Office a livello di documento per trascinare un'origine dati nel documento e creare un controllo associato all'origine dati. Per altre informazioni, vedere [Associare i controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche

- [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md)
- [Office dei modelli di progetto](../vsto/office-project-templates-overview.md)
- [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Proprietà nei Office progetto](../vsto/properties-in-office-projects.md)
