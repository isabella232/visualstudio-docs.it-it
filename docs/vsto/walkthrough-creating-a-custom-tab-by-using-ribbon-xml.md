---
title: 'Procedura dettagliata: creare una scheda personalizzata usando il codice XML della barra multifunzione'
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e05bd9173b83ec3303a058dcf61ea48a7ef7675c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839380"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Procedura dettagliata: creare una scheda personalizzata usando il codice XML della barra multifunzione
  Questa procedura dettagliata illustra come creare una scheda personalizzata della barra multifunzione usando l'elemento **barra multifunzione (XML)** .

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Vengono illustrate le attività seguenti:

- Aggiunta di pulsanti alla scheda **componenti** aggiuntivi. La scheda **componenti** aggiuntivi è la scheda predefinita definita nel file XML della barra multifunzione.

- Automazione di Microsoft Office Word usando i pulsanti nella scheda **componenti** aggiuntivi.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-the-project"></a>Creare il progetto
 Il primo passaggio consiste nel creare un progetto di componente aggiuntivo VSTO per Word. In un secondo momento verrà personalizzata la scheda **componenti** aggiuntivi di questo documento.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di **componente aggiuntivo di Word** con il nome **MyRibbonAddIn**.

     Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre il file di codice **ThisAddIn.cs** o **ThisAddIn. vb** e aggiunge il progetto **MyRibbonAddIn** a **Esplora soluzioni**.

## <a name="create-the-vsto-add-ins-tab"></a>Creare la scheda dei componenti aggiuntivi VSTO
 Per creare la scheda **componenti** aggiuntivi, aggiungere un elemento **barra multifunzione (XML)** al progetto. Più avanti nella procedura dettagliata verranno aggiunti alcuni pulsanti a questa scheda.

### <a name="to-create-the-add-ins-tab"></a>Per creare la scheda componenti aggiuntivi

1. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **barra multifunzione (XML)**.

3. Modificare il nome della nuova barra multifunzione in **MyRibbon**e quindi scegliere **Aggiungi**.

     Il file **MyRibbon.cs** o **Ribbon. vb** viene aperto nella finestra di progettazione. Al progetto viene aggiunto anche un file XML denominato **MyRibbon.xml** .

4. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **ThisAddIn.cs** o **ThisAddIn. vb**, quindi scegliere **Visualizza codice**.

5. Aggiungere il codice seguente alla classe **ThisAddIn** . Questo codice esegue l'override del metodo `CreateRibbonExtensibilityObject` e restituisce la classe XML della barra multifunzione all'applicazione Office.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto **MyRibbonAddIn** , quindi scegliere **Compila**. Verificare che il progetto venga compilato senza errori.

## <a name="add-buttons-to-the-add-ins-tab"></a>Aggiungere pulsanti alla scheda componenti aggiuntivi
 L'obiettivo di questo componente aggiuntivo VSTO consiste nell'offrire all'utente un modo per aggiungere testo standard e una tabella specifica al documento attivo. Per fornire l'interfaccia utente, aggiungere due pulsanti alla scheda **componenti** aggiuntivi modificando il file XML della barra multifunzione. Più avanti nella procedura dettagliata verranno definiti i metodi di callback per i pulsanti. Per ulteriori informazioni sul file XML della barra multifunzione, vedere [Ribbon XML](../vsto/ribbon-xml.md).

### <a name="to-add-buttons-to-the-add-ins-tab"></a>Per aggiungere pulsanti alla scheda componenti aggiuntivi

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **MyRibbon.xml** , quindi scegliere **Apri**.

2. Sostituire il contenuto dell'elemento **Tab** con il codice XML seguente. Questo XML modifica l'etichetta del gruppo di controlli predefinito in **contenuto**e aggiunge due nuovi pulsanti con le etichette **Inserisci testo** e **Inserisci tabella**.

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
 È necessario aggiungere `onAction` metodi di callback per i pulsanti **Inserisci testo** e **Inserisci tabella** per eseguire azioni quando l'utente fa clic su di essi. Per ulteriori informazioni sui metodi di callback per i controlli della barra multifunzione, vedere [Ribbon XML](../vsto/ribbon-xml.md).

### <a name="to-add-callback-methods-for-the-buttons"></a>Per aggiungere i metodi di callback per i pulsanti

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **MyRibbon.cs** o **Ribbon. vb**, quindi scegliere **Apri**.

2. Aggiungere il codice seguente all'inizio del file **MyRibbon.cs** o **Ribbon. vb** . Tramite questo codice viene creato un alias per lo spazio dei nomi <xref:Microsoft.Office.Interop.Word>.

     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]

3. Aggiungere il metodo seguente alla classe `MyRibbon`. Si tratta di un metodo di callback per il pulsante **Inserisci testo** che aggiunge una stringa al documento attivo nella posizione corrente del cursore.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]

4. Aggiungere il metodo seguente alla classe `MyRibbon`. Si tratta di un metodo di callback per il pulsante **Inserisci tabella** che aggiunge una tabella al documento attivo nella posizione corrente del cursore.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]

## <a name="testing-the-vsto-add-in"></a>Test del componente aggiuntivo VSTO
 Quando si esegue il progetto, Word viene aperto e la scheda denominata **componenti** aggiuntivi viene visualizzata sulla barra multifunzione. Fare clic sui pulsanti **Inserisci testo** e **Inserisci tabella** nella scheda **componenti** aggiuntivi per testare il codice.

### <a name="to-test-your-vsto-add-in"></a>Per testare il componente aggiuntivo VSTO

1. Premere **F5** per eseguire il progetto.

2. Verificare che la scheda **componenti** aggiuntivi sia visibile nella barra multifunzione.

3. Fare clic sulla scheda **Componenti aggiuntivi** .

4. Verificare che il gruppo di **contenuto** sia visibile nella barra multifunzione.

5. Fare clic sul pulsante **Inserisci testo** nel gruppo di **contenuto** .

     Verrà aggiunta una stringa in corrispondenza della posizione corrente del cursore nel documento.

6. Fare clic sul pulsante **Inserisci tabella** nel gruppo di **contenuto** .

     Verrà aggiunta una tabella in corrispondenza della posizione corrente del cursore nel documento.

## <a name="next-steps"></a>Passaggi successivi
 È possibile trovare ulteriori informazioni sulla personalizzazione dell'interfaccia utente di Office nei seguenti argomenti:

- Personalizzare la barra multifunzione di un'applicazione di Office diversa. Per ulteriori informazioni sulle applicazioni che supportano la personalizzazione della barra multifunzione, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).

- Personalizzare la barra multifunzione di un'applicazione di Office usando la finestra di progettazione della barra multifunzione. Per altre informazioni, vedere [Ribbon Designer](../vsto/ribbon-designer.md).

- Creare un riquadro azioni personalizzato. Per altre informazioni, vedere [Cenni preliminari sul riquadro azioni](../vsto/actions-pane-overview.md).

- Personalizzare l'interfaccia utente di Microsoft Office Outlook usando le aree del modulo di Outlook. Per altre informazioni, vedere [procedura dettagliata: progettare un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>Vedere anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura dettagliata: creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
