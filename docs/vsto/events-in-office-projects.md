---
title: Eventi nei Office progetto
description: Informazioni su come ogni Office di progetto genera diversi gestori eventi e su come tali gestori eventi sono leggermente diversi dai gestori eventi per VSTO componenti aggiuntivi.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Sheet1_Startup
- ThisDocument_Shutdown
- ThisDocument_Startup
- application-level add-ins [Office development in Visual Studio], events
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- Sheet2_Startup
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio], events
- Sheet2_Shutdown
- Startup event
- Sheet3_Shutdown
- add-ins [Office development in Visual Studio], events
- Shutdown event
- ThisAddIn_Startup
- Sheet3_Startup
- Startup method [Office development in Visual Studio]
- Shutdown method [Office development in Visual Studio]
- Sheet1_Shutdown
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 4eee6a66e8cd9d0a9868af75bc68ad249be76827
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038045"
---
# <a name="events-in-office-projects"></a>Eventi nei Office progetto
  Ogni modello di progetto di Office genera automaticamente diversi gestori eventi. I gestori eventi per le personalizzazioni a livello di documento sono leggermente diversi dai gestori eventi per componenti aggiuntivi VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="document-level-projects"></a>Progetti a livello di documento
 Visual Studio fornisce codice generato sottostante documenti nuovi o esistenti o fogli di lavoro nelle personalizzazioni a livello di documento. Questo codice genera due eventi distinti: **Startup** e **Shutdown**.

### <a name="startup-event"></a>Startup (evento)
 L'evento **Startup** viene generato per ogni elemento host (documento, cartella di lavoro o foglio di lavoro) dopo l'esecuzione del documento e di tutto il codice di inizializzazione nell'assembly. È l'ultima operazione da eseguire nel costruttore della classe in cui viene eseguito il codice. Per altre informazioni sugli elementi host, vedere [Panoramica degli elementi host e dei controlli host.](../vsto/host-items-and-host-controls-overview.md)

 Quando si crea un progetto a livello di documento, Visual Studio crea gestori eventi per l'evento **Startup** nei file del codice generato:

- Per i progetti di Microsoft Office Word, il gestore eventi è denominato `ThisDocument_Startup`.

- Per i progetti di Microsoft Office Excel, i gestori di eventi presentano i nomi seguenti:

  - `Sheet1_Startup`

  - `Sheet2_Startup`

  - `Sheet3_Startup`

  - `ThisWorkbook_Startup`

### <a name="shutdown-event"></a>Shutdown (evento)
 L'evento **Shutdown** viene generato per ogni elemento host (documento o foglio di lavoro) quando il dominio dell'applicazione in cui è caricato il codice sta per essere scaricato. È l'ultima operazione da chiamare nella classe durante lo scaricamento.

 Quando si crea un progetto a livello di documento, Visual Studio crea gestori eventi per l'evento **Shutdown** nei file del codice generato:

- Per i progetti di Microsoft Office Word, il gestore eventi è denominato `ThisDocument_Shutdown`.

- Per i progetti di Microsoft Office Excel, i gestori di eventi presentano i nomi seguenti:

  - `Sheet1_Shutdown`

  - `Sheet2_Shutdown`

  - `Sheet3_Shutdown`

  - `ThisWorkbook_Shutdown`

> [!NOTE]
> Non rimuovere a livello di codice i controlli durante l'esecuzione del gestore dell'evento **Shutdown** del documento. Gli elementi dell'interfaccia utente del documento non sono più disponibili quando si verifica l'evento **Shutdown** . Se si desidera rimuovere i controlli prima della chiusura dell'applicazione, aggiungere il codice a un altro gestore eventi, ad esempio **BeforeClose** o **BeforeSave**.

### <a name="event-handler-method-declarations"></a>Dichiarazioni di metodi del gestore eventi
 A ogni dichiarazione di metodo del gestore eventi vengono passati gli stessi argomenti: *sender* e *e*. In Excel, l'argomento *sender* fa riferimento al foglio, ad esempio `Sheet1` o `Sheet2`. In Word, l'argomento *sender* fa riferimento al documento. L'argomento *e* fa riferimento agli argomenti standard per un evento, che non vengono usati in questo caso.

 Nell'esempio di codice seguente vengono illustrati i gestori eventi predefiniti in progetti a livello di documento di Word.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet121":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet121":::

 Nell'esempio di codice seguente vengono illustrati i gestori eventi predefiniti in progetti a livello di documento di Excel.

> [!NOTE]
> Nell'esempio di codice riportato di seguito vengono illustrati i gestori eventi nella classe `Sheet1` . I nomi dei gestori eventi in altre classi dell'elemento host corrispondono al nome della classe. Ad esempio, nella classe `Sheet2` , il gestore eventi **Startup** è denominato `Sheet2_Startup`. Nella classe `ThisWorkbook` , il gestore eventi **Startup** è denominato `ThisWorkbook_Startup`.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet83":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet83":::

### <a name="order-of-events-in-document-level-excel-projects"></a>Ordine degli eventi nei progetti Excel documento
 I gestori eventi **Startup** nei progetti di Excel vengono chiamati nell'ordine seguente:

1. `ThisWorkbook_Startup`.

2. `Sheet1_Startup`.

3. `Sheet2_Startup`.

4. `Sheet3_Startup`.

5. Altri fogli in ordine.

   I gestori eventi **Shutdown** in una soluzione di cartella di lavoro vengono chiamati nell'ordine seguente:

6. `ThisWorkbook_Shutdown`.

7. `Sheet1_Shutdown`.

8. `Sheet2_Shutdown`.

9. `Sheet3_Shutdown`.

10. Altri fogli in ordine.

    L'ordine viene determinato quando viene compilato il progetto. Se l'utente riorganizza i fogli in fase di esecuzione, non viene modificato l'ordine poiché gli eventi vengono generati alla successiva apertura o chiusura della cartella di lavoro.

## <a name="vsto-add-in-projects"></a>Progetti di componente aggiuntivo VSTO
 Visual Studio fornisce codice generato VSTO componenti aggiuntivi. Questo codice genera due eventi diversi: <xref:Microsoft.Office.Tools.AddInBase.Startup> e <xref:Microsoft.Office.Tools.AddInBase.Shutdown> .

### <a name="startup-event"></a>Startup (evento)
 L'evento <xref:Microsoft.Office.Tools.AddIn.Startup> viene generato dopo che il componente aggiuntivo VSTO viene caricato e tutto il codice di inizializzazione nell'assembly è stato eseguito. Questo evento viene gestito dal metodo `ThisAddIn_Startup` nel file di codice generato.

 Il codice nel gestore eventi `ThisAddIn_Startup` è il primo codice utente da eseguire, a meno che il componente aggiuntivo VSTO non esegua l'override del metodo <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . In questo caso, il gestore eventi `ThisAddIn_Startup` viene chiamato dopo <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>.

 Non aggiungere codice nel gestore eventi `ThisAdd-In_Startup` se il codice richiede l'apertura di un documento. Al contrario, aggiungere tale codice a un evento generato dall'applicazione di Office quando un utente crea o apre un documento. Per altre informazioni, vedere [Accedere a un documento all'avvio Office'applicazione](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 Per altre informazioni sulla sequenza di avvio VSTO componenti aggiuntivi, vedere [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

### <a name="shutdown-event"></a>Shutdown (evento)
 L'evento <xref:Microsoft.Office.Tools.AddInBase.Shutdown> viene generato quando il dominio dell'applicazione in cui è caricato il codice sta per essere scaricato. Questo evento viene gestito dal metodo `ThisAddIn_Shutdown` nel file di codice generato. Questo gestore eventi è l'ultimo codice utente da eseguire quando viene scaricato il componente aggiuntivo VSTO.

#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Evento di arresto Outlook VSTO componenti aggiuntivi
 L'evento <xref:Microsoft.Office.Tools.AddInBase.Shutdown> viene generato solo quando l'utente disabilita il componente aggiuntivo VSTO usando la finestra di dialogo dei componenti aggiuntivi COM in Outlook. Non viene generato quando si esce da Outlook. Se si dispone di codice che deve essere eseguito quando si esce da Outlook, gestire uno degli eventi seguenti:

- Evento <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> .

- Evento <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> .

> [!NOTE]
> È possibile imporre a Outlook di generare l'evento <xref:Microsoft.Office.Tools.AddInBase.Shutdown> alla chiusura modificando il Registro di sistema. Tuttavia, se un amministratore ripristina questa impostazione, qualsiasi codice viene aggiunto al metodo `ThisAddIn_Shutdown` , non viene più eseguito quando si esce da Outlook. Per altre informazioni, vedere [Shutdown changes for Outlook 2010](/previous-versions/office/developer/office-2010/ee720183(v=office.14)).

## <a name="see-also"></a>Vedi anche
- [Sviluppare Office soluzioni](../vsto/developing-office-solutions.md)
- [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)
- [Componenti VSTO programma](../vsto/programming-vsto-add-ins.md)
- [Office dei modelli di progetto](../vsto/office-project-templates-overview.md)
