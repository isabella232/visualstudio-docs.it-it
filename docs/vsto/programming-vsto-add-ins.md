---
title: Componenti VSTO programma
description: Informazioni su come usare la classe ThisAddIn per eseguire attività quali l'accesso al modello a oggetti dell Microsoft Office app host.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7afd9532affc9a4d22c602a65faf7adc225dd41f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025914"
---
# <a name="program-vsto-add-ins"></a>Componenti VSTO programma
  Quando si estende un'applicazione di Microsoft Office creando un componente aggiuntivo VSTO, si scrive il codice direttamente per la classe `ThisAddIn` nel progetto. È possibile usare questa classe per eseguire attività quali l'accesso al modello a oggetti dell'applicazione host di Microsoft Office, la personalizzazione dell'interfaccia utente dell'applicazione e l'esposizione di oggetti nel componente aggiuntivo VSTO ad altre soluzioni Office.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Alcuni aspetti della scrittura del codice nei progetti di componente aggiuntivo VSTO presentano delle differenze rispetto ad altri tipi di progetti in Visual Studio. Molte di queste differenze sono causate dalla modalità di esposizione dei modelli a oggetti di Office al codice gestito. Per altre informazioni, vedere [Scrivere codice in Office soluzioni](../vsto/writing-code-in-office-solutions.md).

 Per informazioni generali su VSTO componenti aggiuntivi e altri tipi di soluzioni che è possibile creare usando gli strumenti di sviluppo di Office in Visual Studio, vedere Office [solutions development overview &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-thisaddin-class"></a>Usare la classe ThisAddIn
 È possibile iniziare a scrivere il codice del componente aggiuntivo VSTO nella classe `ThisAddIn` . Visual Studio genera automaticamente questa classe nel file di codice *ThisAddIn.vb* (in ) o [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] *ThisAddIn.cs* (in C#) nel progetto VSTO componente aggiuntivo. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea automaticamente l'istanza di questa classe quando l'applicazione di Microsoft Office carica il componente aggiuntivo VSTO.

 Sono disponibili due gestori eventi predefiniti nella classe `ThisAddIn` . Per eseguire il codice quando viene caricato il componente aggiuntivo VSTO, aggiungere il codice al gestore eventi `ThisAddIn_Startup` . Per eseguire il codice poco prima che il componente aggiuntivo VSTO venga scaricato, aggiungere il codice al gestore eventi `ThisAddIn_Shutdown` . Per altre informazioni su questi gestori eventi, vedere [Eventi nei Office progetti](../vsto/events-in-office-projects.md).

> [!NOTE]
> In Outlook, per impostazione predefinita, il gestore eventi `ThisAddIn_Shutdown` non viene chiamato sempre quando il componente aggiuntivo VSTO viene scaricato. Per altre informazioni, vedere [Eventi nei Office .](../vsto/events-in-office-projects.md)

### <a name="access-the-object-model-of-the-host-application"></a>Accedere al modello a oggetti dell'applicazione host
 Per accedere il modello a oggetti dell'applicazione host, usare il campo `Application` della classe `ThisAddIn` . Questo campo restituisce un oggetto che rappresenta l'istanza corrente dell'applicazione host. La tabella seguente elenca il tipo di valore restituito per il campo `Application` in ogni progetto di componente aggiuntivo VSTO.

|Applicazione host|Tipo di valore restituito|
|----------------------|-----------------------|
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|
|Microsoft Office PowerPoint|[Applicazione](/previous-versions/office/developer/office-2010/ff764034(v=office.14))|
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|

 Nell'esempio di codice seguente viene illustrato come usare il campo per creare una nuova cartella di lavoro in un VSTO `Application` componente aggiuntivo per Microsoft Office Excel. Questo esempio è destinato a essere eseguito dalla classe `ThisAddIn` .

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 Per eseguire la stessa operazione dall'esterno della classe `ThisAddIn` , usare l'oggetto `Globals` per accedere alla classe `ThisAddIn` . Per altre informazioni sull'oggetto, vedere Accesso globale agli `Globals` oggetti nei Office [progetti](../vsto/global-access-to-objects-in-office-projects.md).

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 Per altre informazioni sui modelli a oggetti di applicazioni specifiche di Microsoft Office, vedere gli argomenti seguenti:

- [Excel panoramica del modello a oggetti](../vsto/excel-object-model-overview.md)

- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)

- [Outlook panoramica del modello a oggetti](../vsto/outlook-object-model-overview.md)

- [Soluzioni InfoPath](../vsto/infopath-solutions.md)

- [PowerPoint soluzioni](../vsto/powerpoint-solutions.md)

- [Project soluzioni](../vsto/project-solutions.md)

- [Visio panoramica del modello a oggetti](../vsto/visio-object-model-overview.md)

### <a name="access-a-document-when-the-office-application-starts"></a><a name="AccessingDocuments"></a>Accedere a un documento all'avvio Office'applicazione
 Non tutte le applicazioni di [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aprono automaticamente un documento all'avvio e nessuna applicazione di [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] apre un documento all'avvio. Pertanto, non aggiungere codice nel gestore `ThisAdd-In_Startup` eventi se il codice richiede l'apertura di un documento. Al contrario, aggiungere tale codice a un evento generato dall'applicazione di Office quando un utente crea o apre un documento. In questo modo, è possibile garantire che un documento venga aperto prima che il codice esegua le relative operazioni.

 Nell'esempio di codice seguente si usa un documento di Word solo quando l'utente crea un documento o si apre un documento esistente.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs" id="Snippet3":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb" id="Snippet3":::

### <a name="thisaddin-members-to-use-for-other-tasks"></a>Membri ThisAddIn da usare per altre attività
 Nella tabella seguente vengono descritte altre attività comuni e i membri della classe `ThisAddIn` che si possono usare per eseguire le attività.

|Attività|Membro da usare|
|----------|-------------------|
|Eseguire il codice per inizializzare il componente aggiuntivo VSTO quando viene caricato.|Aggiungere il codice al metodo `ThisAddIn_Startup` . Questo metodo è il gestore eventi predefinito per l'evento <xref:Microsoft.Office.Tools.AddInBase.Startup> . Per altre informazioni, vedere [Eventi nei Office .](../vsto/events-in-office-projects.md)|
|Eseguire il codice per pulire le risorse usate dal componente aggiuntivo VSTO prima che venga scaricato.|Aggiungere il codice al metodo `ThisAddIn_Shutdown` . Questo metodo è il gestore eventi predefinito per l'evento <xref:Microsoft.Office.Tools.AddInBase.Shutdown> . Per altre informazioni, vedere [Eventi nei Office .](../vsto/events-in-office-projects.md) **Nota:**  In Outlook, per impostazione predefinita il gestore eventi non viene sempre chiamato `ThisAddIn_Shutdown` quando VSTO componente aggiuntivo viene scaricato. Per altre informazioni, vedere [Eventi nei Office .](../vsto/events-in-office-projects.md)|
|Visualizzare un riquadro attività personalizzato.|Usare il campo `CustomTaskPanes` . Per altre informazioni, vedere [Riquadri attività personalizzati](../vsto/custom-task-panes.md).|
|Esporre gli oggetti nel componente aggiuntivo VSTO ad altre soluzioni Microsoft Office.|Eseguire l'override del metodo <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>. Per altre informazioni, vedere [Chiamare il codice in VSTO componenti aggiuntivi](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)da altre Office soluzioni .|
|Personalizzare una funzionalità nel sistema Microsoft Office implementando un'interfaccia di estensibilità.|Eseguire l'override del metodo <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> in modo da ottenere un'istanza della classe che implementi l'interfaccia. Per altre informazioni, vedere [Personalizzare le funzionalità dell'interfaccia utente usando le interfacce di estendibilità.](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md) **Nota:**  Per personalizzare l'interfaccia utente della barra multifunzione, è anche possibile eseguire l'override del <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> metodo .|

### <a name="understand-the-design-of-the-thisaddin-class"></a>Comprendere la progettazione della classe ThisAddIn
 Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], <xref:Microsoft.Office.Tools.AddIn> è un'interfaccia. La classe `ThisAddIn` deriva dalla classe <xref:Microsoft.Office.Tools.AddInBase> . Questa classe di base reindirizza tutte le chiamate ai relativi membri a un'implementazione interna dell'interfaccia <xref:Microsoft.Office.Tools.AddIn> nel [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

 Nei progetti di componente aggiuntivo VSTO per Outlook la classe `ThisAddIn` deriva dalla classe `Microsoft.Office.Tools.Outlook.OutlookAddIn` nei progetti destinati a .NET Framework 3.5 e da <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Queste classi di base forniscono funzionalità aggiuntive per supportare le aree del modulo. Per altre informazioni sulle aree del modulo, vedere [Creare Outlook modulo.](../vsto/creating-outlook-form-regions.md)

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Personalizzare l'interfaccia utente delle Microsoft Office applicazioni
 È possibile personalizzare l'interfaccia utente delle applicazioni di Microsoft Office a livello di codice usando un componente aggiuntivo VSTO. Ad esempio, è possibile personalizzare la barra multifunzione, visualizzare un riquadro attività personalizzato o creare un'area del modulo personalizzata in Outlook. Per altre informazioni, vedere personalizzazione [Office'interfaccia utente.](../vsto/office-ui-customization.md)

 Visual Studio fornisce le finestre di progettazione e le classi che si usano per creare riquadri attività personalizzati, personalizzazioni della barra multifunzione e aree del modulo di Outlook. Le finestre di progettazione e le classi consentono di semplificare il processo di personalizzazione di queste funzionalità. Per altre informazioni, vedere [Riquadri attività personalizzati,](../vsto/custom-task-panes.md) [Progettazione](../vsto/ribbon-designer.md)barra multifunzione e Creare Outlook [modulo.](../vsto/creating-outlook-form-regions.md)

 Per personalizzare una di queste funzionalità in un modo non supportato da classi e finestre di progettazione, è possibile implementare un' *interfaccia di estendibilità* nel componente aggiuntivo VSTO. Per altre informazioni, vedere [Personalizzare le funzionalità dell'interfaccia utente usando le interfacce di estendibilità.](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)

 Inoltre, è possibile modificare l'interfaccia utente di documenti di Word e di cartelle di lavoro di Excel generando elementi host che estendono il comportamento dei documenti e delle cartelle di lavoro. In tal modo è possibile aggiungere controlli gestiti a documenti e fogli di lavoro. Per altre informazioni, vedere Estendere documenti di Word Excel cartelle di lavoro in VSTO [componenti aggiuntivi in fase di esecuzione.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Chiamare il codice VSTO componenti aggiuntivi da altre soluzioni
 Gli oggetti nel componente aggiuntivo VSTO possono essere esposti ad altre soluzioni, ad esempio ad altre soluzioni Microsoft Office. Questa funzionalità è utile se il componente aggiuntivo VSTO fornisce un servizio che si vuole usare anche in altre soluzioni. Ad esempio, se si dispone di un componente aggiuntivo VSTO per Microsoft Office Excel che esegue calcoli sui dati finanziari da un servizio Web, altre soluzioni possono eseguire questi calcoli chiamando il componente aggiuntivo Excel VSTO in fase di esecuzione.

 Per altre informazioni, vedere [Chiamare il codice in VSTO componenti aggiuntivi](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)da altre Office soluzioni .

## <a name="see-also"></a>Vedi anche
- [Sviluppare Office soluzioni](../vsto/developing-office-solutions.md)
- [Estendere documenti di Word Excel cartelle di lavoro in VSTO componenti aggiuntivi in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Chiamare il codice VSTO componenti aggiuntivi da altre Office soluzioni](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Procedura dettagliata: Chiamare il codice in VSTO componente aggiuntivo da VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Personalizzare le funzionalità dell'interfaccia utente usando le interfacce di estendibilità](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Scrivere codice in Office soluzioni](../vsto/writing-code-in-office-solutions.md)
