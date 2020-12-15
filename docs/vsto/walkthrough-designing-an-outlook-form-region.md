---
title: "Procedura dettagliata: progettare un'area del modulo di Outlook"
description: Informazioni su come progettare un'area del modulo di Microsoft Outlook personalizzata visualizzata come nuova pagina nella finestra di controllo di un elemento di contatto.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e306814512c6cab2d331a26128f22bb94d7dbbf4
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524205"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>Procedura dettagliata: progettare un'area del modulo di Outlook
  Le aree del modulo personalizzate estendono i moduli standard o personalizzati di Microsoft Office Outlook. In questa procedura dettagliata verrà progettata un'area del modulo personalizzata che viene visualizzata come una nuova pagina nella finestra di controllo di un contatto. Quest'area del modulo visualizza una mappa di ogni indirizzo elencato per il contatto, inviando le informazioni sull'indirizzo al sito Web di ricerca locale di Windows Live. Per informazioni sulle aree del modulo, vedere [creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Vengono illustrate le attività seguenti:

- Creazione di un nuovo progetto di componente aggiuntivo VSTO per Outlook.

- Aggiunta di un'area del modulo al progetto di componente aggiuntivo VSTO.

- Progettazione del layout dell'area del modulo.

- Personalizzazione del comportamento dell'area del modulo.

- Test dell'area del modulo di Outlook.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)] o versione successiva.

  ![collegamento al video](../vsto/media/playvideo.gif "Collegamento a video") Per una versione video di questo argomento, vedere [video procedura: progettare un'area del modulo di Outlook](/previous-versions/visualstudio/visual-studio-2008/cc837160(v=vs.90)).

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Creare un nuovo progetto di componente aggiuntivo VSTO per Outlook
 Creare prima un progetto di componente aggiuntivo VSTO di base.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Per creare un nuovo progetto di componente aggiuntivo VSTO di Outlook

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] creare un progetto di componente aggiuntivo VSTO per Outlook con il nome **MapItAddIn**.

2. Nella finestra di dialogo **Nuovo progetto** selezionare **Crea directory per soluzione**.

3. Salvare il progetto in qualsiasi directory.

     Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Aggiungere un'area del modulo al progetto di componente aggiuntivo VSTO per Outlook
 Una soluzione di componente aggiuntivo VSTO di Outlook può contenere uno o più elementi dell'area del modulo di Outlook. Aggiungere un elemento dell'area del modulo al progetto tramite la procedura guidata **nuova area del modulo di Outlook** .

### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Per aggiungere un'area del modulo al progetto di componente aggiuntivo VSTO di Outlook

1. In **Esplora soluzioni** selezionare il progetto **MapItAddIn** .

2. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

3. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **area del modulo di Outlook**, assegnare al file il nome **MapIt**, quindi fare clic su **Aggiungi**.

     Viene avviata la procedura guidata **area del modulo NewOutlook** .

4. Nella pagina **selezionare la modalità di creazione dell'area del modulo** fare clic su **progetta una nuova area del modulo**, quindi fare clic su **Avanti**.

5. Nella pagina **selezionare il tipo di area del modulo che si vuole creare** fare clic su **separato** e quindi su **Avanti**.

     Un'area del modulo *separata* aggiunge una nuova pagina a un modulo di Outlook. Per altre informazioni sui tipi di area del modulo, vedere [creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md).

6. Nella pagina **fornire un testo descrittivo e selezionare le preferenze di visualizzazione** digitare **map it** nella casella **nome** .

     Questo nome viene visualizzato sulla barra multifunzione della finestra del controllo quando il contatto è aperto.

7. Selezionare **controlli che sono in modalità di composizione** e **controlli in modalità di lettura**, quindi fare clic su **Avanti**.

8. Nella pagina **identificare le classi di messaggi per la visualizzazione dell'area del modulo** deselezionare **messaggio di posta elettronica**, selezionare **contatto**, quindi fare clic su **fine**.

     Un file *MapIt.cs* o *MapIt. vb* viene aggiunto al progetto.

## <a name="design-the-layout-of-the-form-region"></a>Progettare il layout dell'area del modulo
 Sviluppare aree del modulo visivamente utilizzando la *finestra di progettazione dell'area del modulo*. È possibile trascinare i controlli gestiti sull'area di progettazione aree del modulo. Utilizzare la finestra di progettazione e la finestra **Proprietà** per modificare il layout e l'aspetto del controllo.

### <a name="to-design-the-layout-of-the-form-region"></a>Per progettare il layout dell'area del modulo

1. In **Esplora soluzioni** espandere il progetto **MapItAddIn** , quindi fare doppio clic su *MapIt.cs* o *MapIt. vb* per aprire la finestra di progettazione dell'area del modulo.

2. Fare clic con il pulsante destro del mouse sulla finestra di progettazione, quindi scegliere **Proprietà**.

3. Nella finestra **Proprietà** impostare **dimensioni** su **664, 469**.

     Ciò garantisce che l'area del modulo sia sufficiente grande per visualizzare una mappa.

4. Scegliere **Casella degli strumenti** dal menu **Visualizza**.

5. Dalla scheda **controlli comuni** della **casella degli strumenti** aggiungere un oggetto **WebBrowser** all'area del modulo.

     Il **WebBrowser** visualizzerà una mappa di ogni indirizzo elencato per il contatto.

## <a name="customize-the-behavior-of-the-form-region"></a>Personalizzare il comportamento dell'area del modulo
 Aggiungere codice ai gestori eventi dell'area del modulo per personalizzare il modo in cui un'area del modulo si comporta in fase di esecuzione. Per questa area del modulo il codice esamina le proprietà di un elemento di Outlook e determina se visualizzare l'area del modulo Map It. Se viene visualizzata l'area del modulo, il codice consente di passare alla ricerca locale di Windows Live e caricare una mappa di ogni indirizzo elencato nel contatto di Outlook.

### <a name="to-customize-the-behavior-of-the-form-region"></a>Per personalizzare il comportamento dell'area del modulo

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su *MapIt.cs* o *MapIt. vb*, quindi scegliere **Visualizza codice**.

    *MapIt.cs* o *MapIt. vb* viene aperto nell'editor di codice.

2. Espandere l'area del codice **Factory dell'area del modulo** .

    La classe della factory area del modulo denominata `MapItFactory` viene esposta.

3. Aggiungere il codice seguente al gestore eventi `MapItFactory_FormRegionInitializing`. Questo gestore eventi viene chiamato quando l'utente apre un contatto. Il codice seguente determina se il contatto contiene un indirizzo. Se l'elemento contatto non contiene un indirizzo, il codice imposta la <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> proprietà della <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> classe su **true** e l'area del modulo non viene visualizzata. In alternativa, il componente aggiuntivo VSTO genere l'evento <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> e visualizza l'area del modulo.

    [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
    [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

4. Aggiungere il codice seguente al gestore eventi <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>. Il codice esegue queste operazioni:

   - Concatena ogni indirizzo nel contatto e crea una stringa URL.

   - Chiama il metodo <xref:System.Windows.Forms.WebBrowser.Navigate%2A> dell'oggetto <xref:System.Windows.Forms.WebBrowser> e passa la stringa URL come parametro.

     Il sito Web di ricerca locale viene visualizzato nell'area del modulo Map It e presenta ogni indirizzo nel riquadro di lavoro.

     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]

## <a name="test-the-outlook-form-region"></a>Testare l'area del modulo di Outlook
 Quando si esegue il progetto, Visual Studio apre Outlook. Aprire un contatto per visualizzare l'area del modulo Map It. L'area del modulo Map It viene visualizzata nel modulo di qualsiasi contatto che contiene un indirizzo.

### <a name="to-test-the-map-it-form-region"></a>Per eseguire il test dell'area del modulo Map It

1. Premere **F5** per eseguire il progetto.

     Viene aperto Outlook.

2. In Outlook, nella scheda **Home** , fare clic su **nuovi elementi**, quindi fare clic su **contatto**.

3. Nel modulo contatto digitare **Ann Beebe** come nome del contatto, quindi specificare i tre indirizzi seguenti.

    |Tipo di indirizzo|Indirizzo|
    |------------------|-------------|
    |**Business**|**4567 Main St. Buffalo, NY**|
    |**Home**|**1234 North St. Buffalo, NY**|
    |**Altri**|**3456 Main St. Seattle, WA**|

4. Salvare e chiudere il contatto.

5. Riaprire l'elemento contatto **Ann Beebe** .

    In Outlook, questa operazione può essere eseguita nel gruppo **trova** aprendo la Rubrica per i contatti o digitando Ann Beebe in **Cerca persone**.

6. Nel gruppo **Mostra** della barra multifunzione dell'elemento fare clic su **mappa** per aprire l'area del modulo Map it.

     Viene visualizzata l'area del modulo Map It insieme al sito Web di ricerca locale. Gli indirizzi **Business**, **Home** e **altri** vengono visualizzati nel riquadro Scratch. Nel riquadro di lavoro selezionare un indirizzo da mappare.

## <a name="next-steps"></a>Passaggi successivi
 È possibile trovare altre informazioni sulla personalizzazione dell'interfaccia utente di un'applicazione di Outlook negli argomenti seguenti:

- Per informazioni su come personalizzare la barra multifunzione di un elemento di Outlook, vedere [personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

## <a name="see-also"></a>Vedere anche
- [Accedere a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)
- [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)
- [Linee guida per la creazione di aree del modulo di Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Procedura dettagliata: importare un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Associare un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Azioni personalizzate nelle aree del modulo di Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Procedura: impedire la visualizzazione di un'area del modulo in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
