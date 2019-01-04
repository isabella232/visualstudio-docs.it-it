---
title: 'Procedura dettagliata: Creare una scheda personalizzata utilizzando XML della barra multifunzione'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dda5c2721d9932afd20c0b02f4a82bbbde7116ae
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955227"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Procedura dettagliata: Creare una scheda personalizzata utilizzando XML della barra multifunzione
  Questa procedura dettagliata viene illustrato come creare una scheda della barra multifunzione personalizzata usando il **sulla barra multifunzione (XML)** elemento.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Aggiunta di pulsanti per il **Add-Ins** scheda. Il **Add-Ins** scheda è la scheda predefinita che viene definita nel file XML della barra multifunzione.  
  
-   Automazione di Microsoft Office Word usando i pulsanti sul **Add-Ins** scheda.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="create-the-project"></a>Creare il progetto  
 Il primo passaggio consiste nel creare un progetto di componente aggiuntivo VSTO per Word. Successivamente si personalizzerà il **Add-Ins** scheda di questo documento.  
  
### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un **componente aggiuntivo di Word** con il nome progetto **MyRibbonAddIn**.  
  
     Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Apre la **ThisAddIn.cs** o **ThisAddIn. vb** file di codice e aggiunge i **MyRibbonAddIn** progetto al **Esplora soluzioni**.  
  
## <a name="create-the-vsto-add-ins-tab"></a>Creare la scheda componenti aggiuntivi VSTO  
 Per creare il **Add-Ins** scheda, aggiungere un **della barra multifunzione (XML)** elemento al progetto. Più avanti nella procedura dettagliata verranno aggiunti alcuni pulsanti a questa scheda.  
  
### <a name="to-create-the-add-ins-tab"></a>Per creare la scheda componenti aggiuntivi  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
2.  Nel **Aggiungi nuovo elemento** finestra di dialogo **della barra multifunzione (XML)**.  
  
3.  Modificare il nome della nuova barra multifunzione in **MyRibbon**e quindi scegliere **Aggiungi**.  
  
     Il **MyRibbon.cs** oppure **MyRibbon. vb** file viene aperto nella finestra di progettazione. Un file XML denominato **MyRibbon** viene inoltre aggiunto al progetto.  
  
4.  Nelle **Esplora soluzioni**, fare doppio clic su **ThisAddin.cs** oppure **ThisAddIn. vb**, quindi fare clic su **Visualizza codice**.  
  
5.  Aggiungere il codice seguente alla classe **ThisAddIn** . Questo codice esegue l'override del metodo `CreateRibbonExtensibilityObject` e restituisce la classe XML della barra multifunzione all'applicazione di Office.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  Nella **Esplora soluzioni**, fare doppio clic il **MyRibbonAddIn** del progetto e quindi fare clic su **compilare**. Verificare che il progetto venga compilato senza errori.  
  
## <a name="add-buttons-to-the-add-ins-tab"></a>Aggiungere pulsanti alla scheda componenti aggiuntivi  
 L'obiettivo di questo componente aggiuntivo VSTO consiste nell'offrire all'utente un modo per aggiungere testo standard e una tabella specifica al documento attivo. Per fornire l'interfaccia utente, aggiungere due pulsanti per il **Add-Ins** tab, modificando il file XML della barra multifunzione. Più avanti nella procedura dettagliata verranno definiti i metodi di callback per i pulsanti. Per altre informazioni sul file XML della barra multifunzione, vedere [XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
### <a name="to-add-buttons-to-the-add-ins-tab"></a>Per aggiungere pulsanti alla scheda componenti aggiuntivi  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic su **MyRibbon. XML** e quindi fare clic su **Open**.  
  
2.  Sostituire il contenuto del **scheda** elemento con il codice XML seguente. Questo XML modificano l'etichetta del gruppo di controllo predefinito per **contenuti**, e aggiunge due nuovi pulsanti con le etichette **Insert Text** e **Inserisci tabella**.  
  
    ```xml  
    <tab idMso="TabAddIns">  
        <group id="ContentGroup" label="Content">  
            <button id="textButton" label="Insert Text"  
                 screentip="Text" onAction="OnTextButton"  
                 supertip="Inserts text at the cursor location."/>  
            <button id="tableButton" label="Insert Table"  
                 screentip="Table" onAction="OnTableButton"  
                 supertip="Inserts a table at the cursor location."/>  
        </group>  
    </tab>  
    ```  
  
## <a name="automate-the-document-by-using-the-buttons"></a>Automatizzare il documento usando i pulsanti  
 È necessario aggiungere `onAction` metodi di callback per il **Insert Text** e **Insert Table** pulsanti per eseguire azioni quando l'utente fa clic su essi. Per altre informazioni sui metodi di callback per i controlli della barra multifunzione, vedere [XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
### <a name="to-add-callback-methods-for-the-buttons"></a>Per aggiungere i metodi di callback per i pulsanti  
  
1.  Nella **Esplora soluzioni**, fare doppio clic su **MyRibbon.cs** oppure **MyRibbon. vb**, quindi fare clic su **Open**.  
  
2.  Aggiungere il codice seguente all'inizio del **MyRibbon.cs** oppure **MyRibbon. vb** file. Tramite questo codice viene creato un alias per lo spazio dei nomi <xref:Microsoft.Office.Interop.Word>.  
  
     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]  
  
3.  Aggiungere il metodo seguente alla classe `MyRibbon` . Si tratta di un metodo di callback per il **Insert Text** pulsante che aggiunge una stringa al documento attivo nella posizione corrente del cursore.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]  
  
4.  Aggiungere il metodo seguente alla classe `MyRibbon` . Si tratta di un metodo di callback per il **Inserisci tabella** pulsante che aggiunge una tabella al documento attivo nella posizione corrente del cursore.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]  
  
## <a name="testing-the-vsto-add-in"></a>Test del componente aggiuntivo VSTO  
 Quando si esegue il progetto, si apre Word e la scheda denominata **Add-Ins** viene visualizzato sulla barra multifunzione. Fare clic sui **Insert Text** e **Insert Table** i pulsanti sul **Add-Ins** pressione di tab per testare il codice.  
  
### <a name="to-test-your-vsto-add-in"></a>Per testare il componente aggiuntivo VSTO  
  
1.  Premere **F5** per eseguire il progetto.  
  
2.  Verificare che il **Add-Ins** scheda è visibile sulla barra multifunzione.  
  
3.  Fare clic sulla scheda **Componenti aggiuntivi** .  
  
4.  Verificare che il **contenuto** gruppo è visibile sulla barra multifunzione.  
  
5.  Fare clic sui **Insert Text** pulsante il **contenuto** gruppo.  
  
     Verrà aggiunta una stringa in corrispondenza della posizione corrente del cursore nel documento.  
  
6.  Fare clic sui **Insert Table** pulsante il **contenuto** gruppo.  
  
     Verrà aggiunta una tabella in corrispondenza della posizione corrente del cursore nel documento.  
  
## <a name="next-steps"></a>Passaggi successivi  
 È possibile trovare ulteriori informazioni sulla personalizzazione dell'interfaccia utente di Office nei seguenti argomenti:  
  
-   Personalizzare la barra multifunzione di un'altra applicazione di Office. Per altre informazioni sulle applicazioni che supportano la personalizzazione della barra multifunzione, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md).  
  
-   Personalizzare la barra multifunzione di un'applicazione di Office usando la finestra di progettazione della barra multifunzione. Per altre informazioni, vedere [Ribbon Designer](../vsto/ribbon-designer.md).  
  
-   Creare un riquadro azioni personalizzato. Per altre informazioni, vedere [Cenni preliminari sul riquadro azioni](../vsto/actions-pane-overview.md).  
  
-   Personalizzare l'interfaccia utente di Microsoft Office Outlook usando le aree del modulo di Outlook. Per altre informazioni, vedere [Procedura dettagliata: Progettare un'area del modulo Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [XML della barra multifunzione](../vsto/ribbon-xml.md)   
 [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
