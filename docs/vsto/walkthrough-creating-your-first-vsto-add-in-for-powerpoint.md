---
title: 'Procedura dettagliata: Creare il primo VSTO componente aggiuntivo per PowerPoint'
description: Creare un componente aggiuntivo a livello di applicazione per Microsoft PowerPoint. Questa funzionalità è disponibile per l'applicazione stessa, indipendentemente dalle presentazioni aperte.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- PowerPoint [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 39998bb7d60b55405be13493900ef936c05c3032
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633763"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-powerpoint"></a>Procedura dettagliata: Creare il primo VSTO componente aggiuntivo per PowerPoint
  Questa procedura dettagliata illustra come creare un componente aggiuntivo VSTO per Microsoft Office PowerPoint. Le funzionalità create dall'utente in questo tipo di soluzione sono disponibili per l'applicazione stessa, indipendentemente da quali presentazioni siano aperte. Per altre informazioni, vedere panoramica [Office sviluppo di soluzioni &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

 Vengono illustrate le attività seguenti:

- Creazione di un progetto del componente aggiuntivo VSTO PowerPoint per PowerPoint.

- Scrittura di codice che usa il modello a oggetti di PowerPoint per aggiungere una casella di testo a ogni nuova diapositiva.

- Creazione ed esecuzione del progetto a scopo di test.

- Pulizia del progetto, in modo che il componente aggiuntivo VSTO non venga più eseguito automaticamente nel computer di sviluppo.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- PowerPoint

## <a name="create-the-project"></a>Creare il progetto

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Scegliere **Nuovo** dal menu **File** e quindi fare clic su **Progetto**.

3. Nel riquadro dei modelli, espandere **Visual C#** o **Visual Basic**, quindi espandere **Office/SharePoint**.

4. Nel nodo **Office/SharePoint** espanso, selezionare il nodo **Componenti aggiuntivi di Office** .

5. Nell'elenco dei modelli di progetto scegliere un progetto del componente aggiuntivo VSTO di PowerPoint.

6. Nella casella **Nome** digitare **FirstPowerPointAddIn**.

7. Fare clic su **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea il **progetto FirstPowerPointAddIn** e apre il file di codice **ThisAddIn** nell'editor.

## <a name="write-code-that-adds-text-to-each-new-slide"></a>Scrivere codice che aggiunge testo a ogni nuova diapositiva
 Aggiungere quindi codice al file di codice ThisAddIn. Il nuovo codice usa il modello a oggetti di PowerPoint per aggiungere una casella di testo a ogni nuova diapositiva. Per impostazione predefinita, il file di codice ThisAddIn contiene il seguente codice generato:

- Una definizione parziale della classe `ThisAddIn` . Questa classe fornisce un punto di ingresso per il codice e fornisce l'accesso al modello a oggetti di PowerPoint. Per altre informazioni, vedere [Programmi VSTO componenti aggiuntivi](../vsto/programming-vsto-add-ins.md). Il resto della `ThisAddIn` classe è definito in un file di codice nascosto che non è necessario modificare.

- I gestori eventi `ThisAddIn_Startup` e `ThisAddIn_Shutdown` . Questi gestori eventi vengono chiamati quando PowerPoint carica e scarica il componente aggiuntivo VSTO. Usare questi gestori eventi per inizializzare il componente aggiuntivo VSTO al momento del caricamento e per eseguire la pulizia delle risorse usate dal componente aggiuntivo VSTO quando viene scaricato. Per altre informazioni, vedere [Eventi nei Office .](../vsto/events-in-office-projects.md)

### <a name="to-add-a-text-box-to-each-new-slide"></a>Per aggiungere una casella di testo a ogni nuova diapositiva

1. Nel file di codice ThisAddIn, aggiungere il codice seguente alla classe `ThisAddIn` . Questo codice definisce un gestore eventi per [microsoft.Office. Interoperabilità. PowerPoint. EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) [dell'oggetto](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) Application.

    Quando l'utente aggiunge una nuova diapositiva alla presentazione attiva, il gestore eventi aggiunge una casella di testo nella parte superiore della nuova diapositiva, quindi aggiunge il testo nella casella di testo.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs" id="Snippet1":::

2. Se si usa C#, aggiungere il seguente codice al gestore eventi `ThisAddIn_Startup` . Questo codice è necessario per connettere il `Application_PresentationNewSlide` gestore eventi con [Microsoft.Office. Interoperabilità. PowerPoint. EApplication_Event.PresentationNewSlide.](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14))

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs" id="Snippet2":::

   Per modificare tutte le nuove diapositive, negli esempi di codice precedenti vengono usati i seguenti oggetti:

- Il campo `Application` della classe `ThisAddIn` . Il `Application` campo restituisce un oggetto [Application,](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) che rappresenta l'istanza corrente di PowerPoint.

- Parametro `Sld` del gestore eventi per [microsoft.Office. Interoperabilità. PowerPoint. EApplication_Event.PresentationNewSlide.](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) Il `Sld` parametro è un oggetto [Slide](/previous-versions/office/developer/office-2010/ff763417(v=office.14)) che rappresenta la nuova diapositiva. Per altre informazioni, vedere PowerPoint [soluzioni](../vsto/powerpoint-solutions.md).

## <a name="test-the-project"></a>Testare il progetto
 Quando si compila e si esegue il progetto, verificare che la casella di testo venga visualizzata nelle nuove diapositive aggiunte a una presentazione.

### <a name="to-test-the-project"></a>Per testare il progetto

1. Premere **F5** per compilare ed eseguire il progetto.

     Quando si compila il progetto, il codice viene compilato in un assembly incluso nella cartella di output di compilazione relativa al progetto. Inoltre, Visual Studio crea un set di voci del Registro di sistema che consentono a PowerPoint di individuare e caricare il componente aggiuntivo VSTO e di configurare le impostazioni di sicurezza nel computer di sviluppo per attivare l'esecuzione del componente aggiuntivo VSTO. Per altre informazioni, vedere [Compilare Office soluzioni](../vsto/building-office-solutions.md).

2. In PowerPoint, aggiungere una nuova diapositiva alla presentazione attiva.

3. Verificare che il seguente testo venga aggiunto a una nuova casella di testo nella parte superiore della diapositiva.

     **This text was added by using code.**

4. Chiudere PowerPoint.

## <a name="clean-up-the-project"></a>Pulire il progetto
 Al termine dello sviluppo di un progetto, rimuovere l'assembly del componente aggiuntivo VSTO, le voci del Registro di sistema e le impostazioni di sicurezza dal computer di sviluppo. In caso contrario, il componente aggiuntivo VSTO verrà eseguito ogni volta che si apre PowerPoint nel computer di sviluppo.

### <a name="to-clean-up-your-project"></a>Per pulire il progetto

1. In Visual Studio, nel menu **Compila** , fare clic su **Pulisci soluzione**.

## <a name="next-steps"></a>Passaggi successivi
 Ora che è stato creato un componente aggiuntivo VSTO di base per PowerPoint, è possibile ottenere altre informazioni sullo sviluppo di componenti aggiuntivi VSTO in questi argomenti:

- Attività di programmazione generali che è possibile eseguire usando i componenti aggiuntivi VSTO per PowerPoint. Per altre informazioni, vedere [Programmi VSTO componenti aggiuntivi](../vsto/programming-vsto-add-ins.md).

- Uso del modello a oggetti di PowerPoint. Per altre informazioni, vedere PowerPoint [soluzioni](../vsto/powerpoint-solutions.md).

- Personalizzazione dell'interfaccia utente di PowerPoint, ad esempio tramite l'aggiunta di una scheda personalizzata alla barra multifunzione o la creazione di un riquadro attività personalizzato. Per altre informazioni, vedere personalizzazione [Office'interfaccia utente.](../vsto/office-ui-customization.md)

- Compilazione e debug di componenti aggiuntivi VSTO per PowerPoint. Per altre informazioni, vedere [Compilare Office soluzioni](../vsto/building-office-solutions.md).

- Distribuzione di componenti aggiuntivi VSTO per PowerPoint. Per altre informazioni, vedere [Deploy an Office solution](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Vedi anche
- [Componenti aggiuntivi VSTO programma](../vsto/programming-vsto-add-ins.md)
- [PowerPoint soluzioni](../vsto/powerpoint-solutions.md)
- [Office Personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md)
- [Compilare Office soluzioni](../vsto/building-office-solutions.md)
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)
- [Office dei modelli di progetto](../vsto/office-project-templates-overview.md)
