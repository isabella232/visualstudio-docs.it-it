---
title: 'Procedura dettagliata: Creare il primo VSTO componente aggiuntivo per Excel'
description: Creare un componente aggiuntivo a livello di applicazione per Microsoft Excel. Le funzionalità create sono disponibili per l'applicazione stessa, indipendentemente dalle cartelle di lavoro aperte.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Excel [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 4a3dedc8a954f278e1446667c0623ea7da5d6fa5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147609"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-excel"></a>Procedura dettagliata: Creare il primo VSTO componente aggiuntivo per Excel
  Questa procedura dettagliata introduttiva descrive come creare un componente aggiuntivo a livello di applicazione per Microsoft Office Excel. Le funzionalità create dall'utente in questo tipo di soluzione sono disponibili per l'applicazione stessa, indipendentemente da quali cartelle di lavoro siano aperte.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Vengono illustrate le attività seguenti:

- Creazione di un progetto di componente aggiuntivo VSTO per Excel.

- Scrittura di codice che usa il modello a oggetti di Excel per aggiungere testo a una cartella di lavoro, quando viene salvata.

- Creazione ed esecuzione del progetto a scopo di test.

- Pulizia del progetto completato, per fare in modo che il componente aggiuntivo VSTO non venga più eseguito automaticamente nel computer di sviluppo.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Creare il progetto

#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>Per creare un nuovo progetto di componente aggiuntivo VSTO per Excel in Visual Studio

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Scegliere **Nuovo** dal menu **File** e quindi fare clic su **Progetto**.

3. Nel riquadro dei modelli, espandere **Visual C#** o **Visual Basic**, quindi espandere **Office/SharePoint**.

4. Nel nodo **Office/SharePoint** espanso, selezionare il nodo **Componenti aggiuntivi di Office** .

5. Nell'elenco relativo ai modelli di progetto, selezionare **Componente aggiuntivo per Excel 2010** o **Componente aggiuntivo per Excel 2013**.

6. Nella casella **Nome** , digitare **FirstExcelAddIn**.

7. Fare clic su **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea il **progetto FirstExcelAddIn** e apre il file di codice ThisAddIn nell'editor.

## <a name="write-code-to-add-text-to-the-saved-workbook"></a>Scrivere codice per aggiungere testo alla cartella di lavoro salvata
 Aggiungere quindi codice al file di codice ThisAddIn. Il nuovo codice usa il modello a oggetti di Excel al fine di inserire testo boilerplate nella prima riga del foglio di lavoro attivo. Il foglio di lavoro attivo è quello aperto quando l'utente salva la cartella di lavoro. Per impostazione predefinita, il file di codice ThisAddIn contiene il seguente codice generato:

- Una definizione parziale della classe `ThisAddIn` . Questa classe fornisce un punto di ingresso per il codice e fornisce l'accesso al modello a oggetti di Excel. Per altre informazioni, vedere [Programmi VSTO componenti aggiuntivi](../vsto/programming-vsto-add-ins.md). Il resto della `ThisAddIn` classe è definito in un file di codice nascosto che non è necessario modificare.

- I gestori eventi `ThisAddIn_Startup` e `ThisAddIn_Shutdown` . Questi gestori eventi vengono chiamati quando Excel carica e scarica il componente aggiuntivo VSTO. Usare questi gestori eventi per inizializzare il componente aggiuntivo VSTO quando viene caricato e per eseguire la pulizia delle risorse usate dal componente aggiuntivo quando viene scaricato. Per altre informazioni, vedere [Eventi nei Office .](../vsto/events-in-office-projects.md)

### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>Aggiungere una riga di testo alla cartella di lavoro salvata

1. Nel file di codice ThisAddIn, aggiungere il codice seguente alla classe `ThisAddIn` . Il nuovo codice definisce un gestore eventi per l'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> , che viene generato quando si salva una cartella di lavoro.

    Quando l'utente salva una cartella di lavoro, il gestore eventi aggiunge il nuovo testo all'inizio del foglio di lavoro attivo.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs" id="Snippet1":::

2. Se si usa C#, aggiungere il seguente codice obbligatorio al gestore eventi `ThisAddIn_Startup` . Tale codice viene usato per connettere il gestore eventi `Application_WorkbookBeforeSave` all'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs" id="Snippet2":::

   Per modificare la cartella di lavoro salvata, gli esempi di codice precedenti usano i seguenti oggetti:

- Il campo `Application` della classe `ThisAddIn` . Il campo `Application` restituisce un oggetto <xref:Microsoft.Office.Interop.Excel.Application> che rappresenta l'istanza corrente di Excel.

- Il parametro `Wb` del gestore eventi dell'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> . Il `Wb` parametro consiste in un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> che rappresenta la cartella di lavoro. Per altre informazioni, vedere panoramica Excel [modello a oggetti](../vsto/excel-object-model-overview.md).

## <a name="test-the-project"></a>Testare il progetto

### <a name="to-test-the-project"></a>Per testare il progetto

1. Premere **F5** per compilare ed eseguire il progetto.

     Quando si crea il progetto, il codice viene compilato in un assembly incluso nella cartella di output di compilazione relativa al progetto. Visual Studio crea anche un set di voci del Registro di sistema che permettono a Excel di individuare e caricare il componente aggiuntivo VSTO e configura le impostazioni di sicurezza nel computer di sviluppo per permettere l'esecuzione del componente aggiuntivo VSTO. Per altre informazioni, vedere [Compilare Office soluzioni](../vsto/building-office-solutions.md).

2. In Excel, salvare la cartella di lavoro.

3. Verificare che il seguente testo venga aggiunto alla cartella di lavoro.

     **This text was added by using code.**

4. Chiudere Excel.

## <a name="clean-up-the-project"></a>Pulire il progetto
 Al termine dello sviluppo di un progetto, rimuovere l'assembly del componente aggiuntivo VSTO, le voci del Registro di sistema e le impostazioni di sicurezza dal computer di sviluppo. In caso contrario, il componente aggiuntivo VSTO continuerà a essere eseguito ogni volta che si apre Excel nel computer di sviluppo.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Per pulire il progetto completato nel computer di sviluppo

1. In Visual Studio, nel menu **Compila** , fare clic su **Pulisci soluzione**.

## <a name="next-steps"></a>Passaggi successivi
 Dopo aver creato un componente aggiuntivo VSTO di base per Excel, è possibile visualizzare altre informazioni su come sviluppare componenti aggiuntivi VSTO in questi argomenti:

- Attività di programmazione generali che è possibile eseguire in VSTO componenti aggiuntivi: programma VSTO [componenti aggiuntivi](../vsto/programming-vsto-add-ins.md).

- Attività di programmazione specifiche per Excel VSTO componenti aggiuntivi: Excel [soluzioni](../vsto/excel-solutions.md).

- Uso del modello a oggetti di Excel: [panoramica Excel modello a oggetti](../vsto/excel-object-model-overview.md).

- Personalizzazione dell'interfaccia utente di Excel, ad esempio, aggiungendo una scheda personalizzata alla barra multifunzione o creando un riquadro attività personalizzato: Office personalizzazione [dell'interfaccia utente](../vsto/office-ui-customization.md).

- Compilazione e debug VSTO componenti aggiuntivi per Excel: Compilare [Office soluzioni](../vsto/building-office-solutions.md).

- Distribuzione VSTO componenti aggiuntivi per Excel: Distribuire [una Office soluzione .](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Vedi anche
- [Office panoramica dello sviluppo di soluzioni &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Excel soluzioni](../vsto/excel-solutions.md)
- [Componenti aggiuntivi VSTO programma](../vsto/programming-vsto-add-ins.md)
- [Excel panoramica del modello a oggetti](../vsto/excel-object-model-overview.md)
- [Office Personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md)
- [Compilare Office soluzioni](../vsto/building-office-solutions.md)
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)
- [Office dei modelli di progetto](../vsto/office-project-templates-overview.md)
