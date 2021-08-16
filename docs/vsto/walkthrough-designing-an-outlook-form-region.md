---
title: "Procedura dettagliata: Progettare un'Outlook del modulo"
description: Informazioni su come progettare un'area del modulo Outlook Microsoft personalizzata che viene visualizzata come nuova pagina nella finestra Di controllo di un elemento contatto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a230d5998a71cf9830fec9731aa825a612c9cfb82d779f796c6c108385e33462
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121267403"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>Procedura dettagliata: Progettare un'Outlook del modulo
  Le aree del modulo personalizzate estendono i moduli standard o personalizzati di Microsoft Office Outlook. In questa procedura dettagliata verrà progettata un'area del modulo personalizzata che viene visualizzata come una nuova pagina nella finestra di controllo di un contatto. Quest'area del modulo visualizza una mappa di ogni indirizzo elencato per il contatto, inviando le informazioni sull'indirizzo al sito Web di ricerca locale di Windows Live. Per informazioni sulle aree del modulo, vedere [Creare Outlook modulo.](../vsto/creating-outlook-form-regions.md)

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Vengono illustrate le attività seguenti:

- Creazione di un nuovo progetto di componente aggiuntivo VSTO per Outlook.

- Aggiunta di un'area del modulo al progetto di componente aggiuntivo VSTO.

- Progettazione del layout dell'area del modulo.

- Personalizzazione del comportamento dell'area del modulo.

- Test dell'area del modulo di Outlook.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)] o versione più recente.

  ![collegamento al video](../vsto/media/playvideo.gif "Collegamento a video") Per una versione video di questo argomento, vedere [Video how to: Design an Outlook form region](/previous-versions/visualstudio/visual-studio-2008/cc837160(v=vs.90)).

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Creare un nuovo Outlook VSTO di componente aggiuntivo
 Creare prima un progetto di componente aggiuntivo VSTO di base.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Per creare un nuovo progetto di componente aggiuntivo VSTO di Outlook

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] creare un progetto Outlook VSTO progetto di componente aggiuntivo con il nome **MapItAddIn**.

2. Nella finestra di dialogo **Nuovo progetto** selezionare **Crea directory per soluzione**.

3. Salvare il progetto in qualsiasi directory.

     Per altre informazioni, [vedere Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Aggiungere un'area del modulo Outlook VSTO progetto di componente aggiuntivo
 Una soluzione di componente aggiuntivo VSTO di Outlook può contenere uno o più elementi dell'area del modulo di Outlook. Aggiungere un elemento dell'area del modulo al progetto usando la **procedura guidata Outlook'area del modulo.**

### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Per aggiungere un'area del modulo al progetto di componente aggiuntivo VSTO di Outlook

1. Nella **Esplora soluzioni** selezionare il **progetto MapItAddIn.**

2. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

3. Nella finestra **di dialogo Aggiungi nuovo elemento** selezionare Outlook **Modulo,** assegnare al file il nome **MapIt** e quindi fare clic su **Aggiungi**.

     Verrà **avviata la procedura guidata Area del modulo NewOutlook.**

4. Nella pagina **Selezionare la modalità di creazione dell'area del** modulo fare clic su Progetta una nuova area del **modulo** e quindi su **Avanti.**

5. Nella pagina **Selezionare il tipo di area del modulo da creare** fare clic su **Separa** e quindi su **Avanti.**

     *Un'area* del modulo separata aggiunge una nuova pagina a un Outlook modulo. Per altre informazioni sui tipi di aree del modulo, vedere [Creare Outlook modulo.](../vsto/creating-outlook-form-regions.md)

6. Nella pagina **Fornire testo descrittivo e selezionare le preferenze di** visualizzazione digitare **Mappa** nella **casella** Nome.

     Questo nome viene visualizzato sulla barra multifunzione della finestra del controllo quando il contatto è aperto.

7. Selezionare **Inspectors that are in compose mode** (Controlli in modalità composizione) **e Inspectors that are in read mode**(Controlli in modalità lettura) e quindi fare clic su Next **(Avanti).**

8. Nella pagina **Identificare le classi di messaggio che verranno visualizzate nell'area del** modulo deselezionare **Messaggio** di posta elettronica , selezionare **Contatto** e quindi fare clic su **Fine.**

     Un file *MapIt.cs* *o MapIt.vb* viene aggiunto al progetto.

## <a name="design-the-layout-of-the-form-region"></a>Progettare il layout dell'area del modulo
 Sviluppare visivamente le aree del modulo usando la finestra *di progettazione dell'area del modulo.* È possibile trascinare i controlli gestiti sull'area di progettazione aree del modulo. Usare la finestra di progettazione e la **finestra Proprietà** per regolare il layout e l'aspetto del controllo.

### <a name="to-design-the-layout-of-the-form-region"></a>Per progettare il layout dell'area del modulo

1. In **Esplora soluzioni** espandere il **progetto MapItAddIn** e quindi fare doppio clic su *MapIt.cs* o *MapIt.vb* per aprire Progettazione aree del modulo.

2. Fare clic con il pulsante destro del mouse sulla finestra di progettazione e quindi **scegliere Proprietà**.

3. Nella finestra **Proprietà** impostare **Dimensioni su** **664, 469.**

     Ciò garantisce che l'area del modulo sia sufficiente grande per visualizzare una mappa.

4. Scegliere **Casella degli strumenti** dal menu **Visualizza**.

5. Dalla scheda **Controlli comuni** della casella degli **strumenti** aggiungere un **controllo WebBrowser** all'area del modulo.

     **WebBrowser** visualizza una mappa di ogni indirizzo elencato per il contatto.

## <a name="customize-the-behavior-of-the-form-region"></a>Personalizzare il comportamento dell'area del modulo
 Aggiungere codice ai gestori eventi dell'area del modulo per personalizzare il modo in cui un'area del modulo si comporta in fase di esecuzione. Per questa area del modulo il codice esamina le proprietà di un elemento di Outlook e determina se visualizzare l'area del modulo Map It. Se viene visualizzata l'area del modulo, il codice consente di passare alla ricerca locale di Windows Live e caricare una mappa di ogni indirizzo elencato nel contatto di Outlook.

### <a name="to-customize-the-behavior-of-the-form-region"></a>Per personalizzare il comportamento dell'area del modulo

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse *su MapIt.cs* *o MapIt.vb* e quindi **scegliere Visualizza codice.**

    *MapIt.cs o* *MapIt.vb* viene aperto nell'editor del codice.

2. Espandere **l'area del codice factory dell'area** del modulo.

    La classe della factory area del modulo denominata `MapItFactory` viene esposta.

3. Aggiungere il codice seguente al gestore eventi `MapItFactory_FormRegionInitializing`. Questo gestore eventi viene chiamato quando l'utente apre un contatto. Il codice seguente determina se il contatto contiene un indirizzo. Se l'elemento contatto non contiene un indirizzo, questo codice imposta la proprietà della classe su <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> **true** e l'area del modulo non viene visualizzata. In alternativa, il componente aggiuntivo VSTO genere l'evento <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> e visualizza l'area del modulo.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet1":::

4. Aggiungere il codice seguente al gestore eventi <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>. Il codice esegue queste operazioni:

   - Concatena ogni indirizzo nel contatto e crea una stringa URL.

   - Chiama il metodo <xref:System.Windows.Forms.WebBrowser.Navigate%2A> dell'oggetto <xref:System.Windows.Forms.WebBrowser> e passa la stringa URL come parametro.

     Il sito Web di ricerca locale viene visualizzato nell'area del modulo Map It e presenta ogni indirizzo nel riquadro di lavoro.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet2":::

## <a name="test-the-outlook-form-region"></a>Testare l'Outlook del modulo
 Quando si esegue il progetto, Visual Studio apre Outlook. Aprire un contatto per visualizzare l'area del modulo Map It. L'area del modulo Map It viene visualizzata nel modulo di qualsiasi contatto che contiene un indirizzo.

### <a name="to-test-the-map-it-form-region"></a>Per eseguire il test dell'area del modulo Map It

1. Premere **F5** per eseguire il progetto.

     Viene aperto Outlook.

2. Nella Outlook Home **fare** clic su Nuovi **elementi** e quindi su **Contatto.**

3. Nel modulo del contatto digitare **Ann Beebe** come nome del contatto e quindi specificare i tre indirizzi seguenti.

    |Tipo di indirizzo|Indirizzo|
    |------------------|-------------|
    |**Business**|**4567 Main St. Ny, NY**|
    |**Home**|**1234 North St. Ny, NY**|
    |**Altri**|**3456 Main St. Seattle, WA**|

4. Salvare e chiudere il contatto.

5. Riaprire **l'elemento contatto di Ann Beebe.**

    In Outlook questa operazione può essere  eseguita nel gruppo Trova aprendo il Rubrica per Contatti o digitando Ann Beebe in **Cerca persone.**

6. Nel gruppo **Mostra** della barra multifunzione dell'elemento fare clic **su** Mappa per aprire l'area del modulo Map It.

     Viene visualizzata l'area del modulo Map It insieme al sito Web di ricerca locale. Gli **indirizzi Business**, **Home** e **Other** vengono visualizzati nel blocco scratch. Nel riquadro di lavoro selezionare un indirizzo da mappare.

## <a name="next-steps"></a>Passaggi successivi
 È possibile trovare altre informazioni sulla personalizzazione dell'interfaccia utente di un'applicazione di Outlook negli argomenti seguenti:

- Per informazioni su come personalizzare la barra multifunzione di un elemento Outlook, vedere [Personalizzare una barra](../vsto/customizing-a-ribbon-for-outlook.md)multifunzione per Outlook .

## <a name="see-also"></a>Vedi anche
- [Accedere a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)
- [Creare aree Outlook modulo](../vsto/creating-outlook-form-regions.md)
- [Linee guida per la creazione Outlook aree del modulo](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Procedura dettagliata: Importare un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Procedura: Aggiungere un'area del modulo a un Outlook di componente aggiuntivo](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Associare un'area del modulo a una Outlook di messaggio](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Azioni personalizzate nelle aree Outlook modulo](../vsto/custom-actions-in-outlook-form-regions.md)
- [Procedura: Impedire Outlook visualizzare un'area del modulo](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
