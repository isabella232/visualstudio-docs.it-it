---
title: 'Procedura dettagliata: Creare una scheda personalizzata usando xml della barra multifunzione'
description: Informazioni su come aggiungere pulsanti alla scheda Add-Ins e automatizzare le Microsoft Word usando la barra multifunzione (XML).
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 49d93a5251c0eb45b3ea9246b0850ad57ae9b1bd2590d681ba44dd3f995025d7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121225907"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Procedura dettagliata: Creare una scheda personalizzata usando xml della barra multifunzione
  Questa procedura dettagliata illustra come creare una scheda personalizzata della barra multifunzione usando **l'elemento Barra multifunzione (XML).**

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Vengono illustrate le attività seguenti:

- Aggiunta di pulsanti **alla scheda Componenti** aggiuntivi. La **scheda Componenti aggiuntivi è** la scheda predefinita definita nel file XML della barra multifunzione.

- Automazione Microsoft Office Word usando i pulsanti nella **scheda Componenti** aggiuntivi.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-the-project"></a>Creare il progetto
 Il primo passaggio consiste nel creare un progetto di componente aggiuntivo VSTO per Word. In seguito si personalizza **la scheda Componenti aggiuntivi** di questo documento.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un **progetto di componente aggiuntivo di Word** con il nome **MyRibbonAddIn**.

     Per altre informazioni, [vedere Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre il file di codice **ThisAddIn.cs** o **ThisAddIn.vb** e aggiunge il **progetto MyRibbonAddIn** **Esplora soluzioni**.

## <a name="create-the-vsto-add-ins-tab"></a>Creare la VSTO dei componenti aggiuntivi
 Per creare **la scheda Componenti aggiuntivi,** aggiungere un elemento Barra multifunzione **(XML)** al progetto. Più avanti nella procedura dettagliata verranno aggiunti alcuni pulsanti a questa scheda.

### <a name="to-create-the-add-ins-tab"></a>Per creare la scheda Componenti aggiuntivi

1. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2. Nella finestra **di dialogo Aggiungi nuovo** elemento selezionare Barra multifunzione **(XML).**

3. Modificare il nome della nuova barra multifunzione in **MyRibbon** e quindi scegliere **Aggiungi**.

     Il file **MyRibbon.cs** o **MyRibbon.vb** viene aperto nella finestra di progettazione. Anche un file XML denominato **MyRibbon.xml** viene aggiunto al progetto.

4. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **ThisAddin.cs** o **ThisAddin.vb** e quindi **scegliere Visualizza codice.**

5. Aggiungere il codice seguente alla classe **ThisAddIn** . Questo codice esegue l'override del metodo `CreateRibbonExtensibilityObject` e restituisce la classe XML della barra multifunzione all'applicazione Office.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb" id="Snippet1":::

6. In **Esplora soluzioni** fare clic con il pulsante destro **del mouse sul progetto MyRibbonAddIn** e quindi scegliere **Compila.** Verificare che il progetto venga compilato senza errori.

## <a name="add-buttons-to-the-add-ins-tab"></a>Aggiungere pulsanti alla scheda Componenti aggiuntivi
 L'obiettivo di questo componente aggiuntivo VSTO consiste nell'offrire all'utente un modo per aggiungere testo standard e una tabella specifica al documento attivo. Per fornire l'interfaccia utente,  aggiungere due pulsanti alla scheda Componenti aggiuntivi modificando il file XML della barra multifunzione. Più avanti nella procedura dettagliata verranno definiti i metodi di callback per i pulsanti. Per altre informazioni sul file XML della barra multifunzione, vedere [XML della barra multifunzione.](../vsto/ribbon-xml.md)

### <a name="to-add-buttons-to-the-add-ins-tab"></a>Per aggiungere pulsanti alla scheda Componenti aggiuntivi

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse **MyRibbon.xml** quindi scegliere **Apri.**

2. Sostituire il contenuto **dell'elemento tab** con il codice XML seguente. Questo codice XML modifica l'etichetta del gruppo di controlli predefinito in **Content** e aggiunge due nuovi pulsanti con le etichette **Insert Text (Inserisci** testo) **e Insert Table (Inserisci tabella).**

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
 È necessario aggiungere metodi di callback per i pulsanti Inserisci testo e Inserisci tabella `onAction` per eseguire azioni quando l'utente fa clic su di essi.   Per altre informazioni sui metodi di callback per i controlli della barra multifunzione, vedere [XML della barra multifunzione.](../vsto/ribbon-xml.md)

### <a name="to-add-callback-methods-for-the-buttons"></a>Per aggiungere i metodi di callback per i pulsanti

1. In **Esplora soluzioni** fare clic con il pulsante **destro del mouse su MyRibbon.cs** **o MyRibbon.vb** e quindi scegliere **Apri.**

2. Aggiungere il codice seguente all'inizio del file **MyRibbon.cs** **o MyRibbon.vb.** Tramite questo codice viene creato un alias per lo spazio dei nomi <xref:Microsoft.Office.Interop.Word>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb" id="Snippet1":::

3. Aggiungi alla classe `MyRibbon` il metodo seguente. Si tratta di un metodo di callback per il **pulsante Inserisci** testo che aggiunge una stringa al documento attivo nella posizione corrente del cursore.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb" id="Snippet2":::

4. Aggiungi alla classe `MyRibbon` il metodo seguente. Si tratta di un metodo di callback **per** il pulsante Inserisci tabella che aggiunge una tabella al documento attivo nella posizione corrente del cursore.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb" id="Snippet3":::

## <a name="testing-the-vsto-add-in"></a>Test del componente aggiuntivo VSTO
 Quando si esegue il progetto, word viene aperto e la scheda denominata Componenti **aggiuntivi viene** visualizzata sulla barra multifunzione. Fare clic **sui pulsanti** Inserisci **testo e** Inserisci tabella nella scheda **Componenti** aggiuntivi per testare il codice.

### <a name="to-test-your-vsto-add-in"></a>Per testare il componente aggiuntivo VSTO

1. Premere **F5** per eseguire il progetto.

2. Verificare che **la scheda Componenti aggiuntivi** sia visibile sulla barra multifunzione.

3. Fare clic sulla scheda **Componenti aggiuntivi** .

4. Verificare che il **gruppo Contenuto** sia visibile sulla barra multifunzione.

5. Fare clic **sul pulsante Inserisci** testo nel **gruppo** Contenuto.

     Verrà aggiunta una stringa in corrispondenza della posizione corrente del cursore nel documento.

6. Fare clic **sul pulsante Inserisci** tabella nel **gruppo** Contenuto.

     Verrà aggiunta una tabella in corrispondenza della posizione corrente del cursore nel documento.

## <a name="next-steps"></a>Passaggi successivi
 È possibile trovare ulteriori informazioni sulla personalizzazione dell'interfaccia utente di Office nei seguenti argomenti:

- Personalizzare la barra multifunzione di un'applicazione Office diversa. Per altre informazioni sulle applicazioni che supportano la personalizzazione della barra multifunzione, vedere Panoramica [della barra multifunzione.](../vsto/ribbon-overview.md)

- Personalizzare la barra multifunzione di un Office appalto usando la finestra di progettazione della barra multifunzione. Per altre informazioni, vedere [Ribbon Designer](../vsto/ribbon-designer.md).

- Creare un riquadro azioni personalizzato. Per altre informazioni, vedere Panoramica [del riquadro Azioni.](../vsto/actions-pane-overview.md)

- Personalizzare l'interfaccia utente di Microsoft Office Outlook usando le aree del modulo di Outlook. Per altre informazioni, vedere [Procedura dettagliata: Progettare un'area Outlook modulo.](../vsto/walkthrough-designing-an-outlook-form-region.md)

## <a name="see-also"></a>Vedi anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
