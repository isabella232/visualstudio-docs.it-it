---
title: 'Procedura dettagliata: Aggiornare i controlli in una barra multifunzione in fase di esecuzione'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- updating Ribbon controls
- Ribbon [Office development in Visual Studio], dynamic menu
- dynamic menus [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e293a0136e6ae2d8b6a6747201e484fdea43f91e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067235"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-runtime"></a>Procedura dettagliata: Aggiornare i controlli in una barra multifunzione in fase di esecuzione

Questa procedura dettagliata illustra come usare il modello a oggetti della barra multifunzione per aggiornare i controlli in una barra multifunzione dopo che è stata caricata nell'applicazione Office.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

L'esempio usa i dati del database di esempio Northwind per popolare una casella combinata e un menu in Microsoft Office Outlook. Gli elementi che selezionano automaticamente in questi controlli popolano i campi, ad esempio **al** e **Subject** in un messaggio di posta elettronica.

Questa procedura dettagliata illustra le attività seguenti:

- Creare un nuovo progetto di componente aggiuntivo VSTO di Outlook.

- Progettazione di un gruppo della barra multifunzione personalizzato.

- Aggiungere il gruppo personalizzato a una scheda incorporata.

- Aggiornare i controlli della barra multifunzione in fase di esecuzione.

> [!NOTE]
> I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti

Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Creare un nuovo progetto di componente aggiuntivo VSTO di Outlook

Prima di tutto, creare un progetto di componente aggiuntivo VSTO di Outlook.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Per creare un nuovo progetto di componente aggiuntivo VSTO di Outlook

1. Nelle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], creare un progetto di componente aggiuntivo VSTO per Outlook con il nome **Ribbon_Update_At_Runtime**.

2. Nella finestra di dialogo **Nuovo progetto** selezionare **Crea directory per soluzione**.

3. Salvare il progetto nella directory del progetto predefinita.

     Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Progettazione di un gruppo della barra multifunzione personalizzato

La barra multifunzione per questo esempio verrà visualizzato quando un utente compone un nuovo messaggio di posta elettronica. Per creare un gruppo personalizzato per la barra multifunzione, prima di tutto aggiungere un elemento barra multifunzione al progetto e quindi progettare il gruppo nella finestra di progettazione della barra multifunzione. Questo gruppo personalizzato consente di generare messaggi di posta elettronica di completamento per i clienti usando nomi e cronologie di ordine di un database.

### <a name="to-design-a-custom-group"></a>Per progettare un gruppo personalizzato

1. Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Barra multifunzione (finestra di progettazione visiva)**.

3. Modificare il nome della nuova barra multifunzione **CustomerRibbon**, quindi fare clic su **Add**.

     Il *CustomerRibbon.cs* oppure *CustomerRibbon. vb* file viene aperto nella finestra di progettazione della barra multifunzione e visualizza una scheda predefinita e un gruppo.

4. Fare clic nella finestra di progettazione per selezionarlo.

5. Nel **delle proprietà** finestra, fare clic sulla freccia giù accanto al **RibbonType** proprietà e quindi fare clic su **Compose**.

     In questo modo, la barra multifunzione viene visualizzata quando l'utente compone un nuovo messaggio di posta elettronica in Outlook.

6. Nella finestra di progettazione della barra multifunzione, fare clic su **Group1** per selezionarlo.

7. Nel **delle proprietà** impostare nella finestra **etichetta** al **Customer Purchases**.

8. Dal **controlli della barra multifunzione di Office** scheda della finestra di **della casella degli strumenti**, trascinare un **ComboBox** nel **Customer Purchases** gruppo.

9. Fare clic su **ComboBox1** per selezionarlo.

10. Nel **delle proprietà** impostare nella finestra **etichetta** a **clienti**.

11. Dal **controlli della barra multifunzione di Office** scheda della finestra di **della casella degli strumenti**, trascinare un **Menu** nel **Customer Purchases** gruppo.

12. Nel **delle proprietà** impostare nella finestra **etichetta** al **prodotto acquistato**.

13. Impostare **dinamici** al **true**.

     In questo modo è possibile aggiungere e rimuovere controlli nel menu in fase di esecuzione dopo che è stata caricata nell'applicazione Office.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Aggiungere il gruppo personalizzato a una scheda incorporata

Una scheda incorporata rappresenta una scheda già presente sulla barra multifunzione di una finestra di esplorazione Outlook o di controllo. In questa procedura, si aggiunge il gruppo personalizzato a una scheda predefinita e quindi si specifica la posizione del gruppo personalizzato nella scheda.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Per aggiungere il gruppo personalizzato a una scheda predefinita

1. Scegliere il **TabAddins (Built-)** pressione di tab per selezionarlo.

2. Nel **delle proprietà** finestra, espandere il **ControlId** proprietà e quindi impostare **OfficeId** a **TabNewMailMessage**.

     Verrà aggiunta la **Customer Purchases** gruppo per il **messaggi** della barra multifunzione che viene visualizzato in un nuovo messaggio di posta elettronica.

3. Scegliere il **Customer Purchases** gruppo per selezionarlo.

4. Nel **delle proprietà** finestra, espandere il **posizione** proprietà, fare clic sulla freccia giù accanto al **PositionType** proprietà e quindi fare clic su  **BeforeOfficeId**.

5. Impostare il **OfficeId** proprietà **GroupClipboard**.

     Si posiziona il **Customer Purchases** gruppo prima del **negli Appunti** gruppo o la **messaggi** scheda.

## <a name="create-the-data-source"></a>Creare l'origine dati

Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.

### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1. Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.

     Verrà avviata il **configurazione guidata origine dati**.

2. Selezionare **Database**, quindi fare clic su **successivo**.

3. Selezionare **set di dati**, quindi fare clic su **successivo**.

4. Selezionare una connessione dati al database Northwind di esempio Microsoft SQL Server Compact 4.0 oppure aggiungere una nuova connessione utilizzando il **nuova connessione** pulsante.

5. Dopo che una connessione è stata selezionata o creata, fare clic su **successivo**.

6. Fare clic su **successivo** per salvare la stringa di connessione.

7. Nel **Scegli oggetti di Database** , espandere **tabelle**.

8. Selezionare la casella di controllo accanto a ciascuna delle seguenti tabelle:

    1. **Clienti**

    2. **Dettagli dell'ordine**

    3. **Ordini**

    4. **Prodotti**

9. Scegliere **Fine**.

## <a name="update-controls-in-the-custom-group-at-runtime"></a>Aggiornare i controlli nel gruppo personalizzato in fase di esecuzione

Usare il modello a oggetti della barra multifunzione per effettuare le seguenti attività:

- Aggiungere i nomi dei clienti per il **clienti** casella combinata.

- Aggiungere i controlli menu e pulsante di **Products Purchased** menu che rappresentano gli ordini di vendita e i prodotti venduti.

- Popolare a, oggetto e corpo campi dei nuovi messaggi di posta elettronica con i dati di **i clienti** casella combinata e **Products Purchased** menu.

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Per aggiornare i controlli nel gruppo personalizzato usando il modello a oggetti della barra multifunzione

1. Scegliere **Aggiungi riferimento** dal menu **Progetto**.

2. Nel **Aggiungi riferimento** della finestra di dialogo fare clic sul **.NET** scheda, seleziona il **LINQ** assembly e quindi fare clic su **OK**.

    Questo assembly contiene le classi per l'uso di Language-Integrated Queries (LINQ). LINQ viene usato per popolare i controlli nel gruppo personalizzato con i dati del database Northwind.

3. Nelle **Esplora soluzioni**, fare clic su **CustomerRibbon.cs** oppure **CustomerRibbon. vb** per selezionarlo.

4. Nel **View** menu, fare clic su **codice**.

    Il file di codice della barra multifunzione viene aperto nell'editor di codice.

5. Aggiungere le seguenti istruzioni alla parte iniziale del file di codice della barra multifunzione. Queste istruzioni forniscono l'accesso agli spazi dei nomi LINQ e allo spazio dei nomi dell'assembly di interoperabilità primario (PIA) di Outlook.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. Aggiungere il codice seguente all'interno di `CustomerRibbon` classe. Il codice dichiara la tabella dati e gli adattatori di tabella che verranno usati per archiviare le informazioni delle tabelle Clienti, Ordini, Dettagli sugli ordini e Prodotti del database Northwind.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7.  Aggiungere il seguente blocco di codice alla classe `CustomerRibbon`. Questo codice aggiunge tre metodi di supporto che creano i controlli per la barra multifunzione in fase di esecuzione.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. Sostituire il metodo del gestore eventi `CustomerRibbon_Load` con il codice seguente. Questo codice usa una query LINQ per eseguire le attività seguenti:

   - Popolare la **clienti** casella combinata con l'ID e nome di 20 clienti del database Northwind.

   - Chiama il metodo di supporto `PopulateSalesOrderInfo`. Questo metodo aggiorna il **ProductsPurchased** menu con i numeri di ordine di vendita relativi al cliente attualmente selezionato.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. Aggiungere il codice seguente alla classe `CustomerRibbon` . Questo codice usa le query LINQ per eseguire le attività seguenti:

   - Aggiungere un sottomenu per il **ProductsPurchased** menu per ogni ordine di vendita correlati al cliente selezionato.

   - Aggiungere pulsanti a ogni sottomenu per i prodotti relativi all'ordine di vendita.

   - Aggiungere gestori eventi a ogni pulsante.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. Nelle **Esplora soluzioni**, fare doppio clic sul file di codice della barra multifunzione.

     La finestra di progettazione della barra multifunzione viene aperta.

11. Nella finestra di progettazione della barra multifunzione, fare doppio clic il **clienti** casella combinata.

     Nell'editor di codice viene aperto il file di codice della barra multifunzione e viene visualizzato il gestore eventi `ComboBox1_TextChanged`.

12. Sostituire il gestore eventi `ComboBox1_TextChanged` con il codice seguente. Mediante il codice vengono effettuate le seguenti attività:

    - Chiama il metodo di supporto `PopulateSalesOrderInfo`. Questo metodo aggiorna il **Products Purchased** menu con gli ordini di vendita relativi al cliente selezionato.

    - Chiama il metodo di supporto `PopulateMailItem` e passa al testo corrente, ossia il nome del cliente selezionato. Questo metodo popola a, oggetto e corpo campi dei nuovi messaggi di posta elettronica.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. Aggiungere il gestore eventi `Click` seguente alla classe `CustomerRibbon` . Questo codice aggiunge il nome dei prodotti selezionati per il campo del corpo dei nuovi messaggi di posta elettronica.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. Aggiungere il codice seguente alla classe `CustomerRibbon` . Mediante il codice vengono effettuate le seguenti attività:

    - Popola la riga a dei nuovi messaggi di posta elettronica usando l'indirizzo di posta elettronica del cliente attualmente selezionato.

    - Aggiunge il testo per i campi oggetto e corpo di nuovi messaggi di posta elettronica.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>Testare i controlli nel gruppo personalizzato

Quando si apre un nuovo modulo di posta elettronica in Outlook, un gruppo personalizzato denominato **Customer Purchases** viene visualizzato nella **messaggi** della barra multifunzione.

Per creare un messaggio di posta elettronica di follow-up dei clienti, selezionare un cliente e quindi selezionare i prodotti acquistati dal cliente. I controlli di **Customer Purchases** gruppo vengono aggiornati in fase di esecuzione con i dati dal database Northwind.

### <a name="to-test-the-controls-in-the-custom-group"></a>Per testare i controlli nel gruppo personalizzato

1. Premere **F5** per eseguire il progetto.

     Viene avviato Outlook.

2. In Outlook sul **File** dal menu **New**e quindi fare clic su **messaggio di posta elettronica**.

     Eseguire le azioni seguenti:

    - Viene visualizzata una nuova finestra di controllo del messaggio di posta.

    - Nel **messaggio** della barra multifunzione, il **Customer Purchases** viene posizionato prima il **negli Appunti** gruppo.

    - Il **clienti** casella combinata del gruppo viene aggiornato con i nomi dei clienti nel database Northwind.

3. Nel **messaggio** della barra multifunzione, nel **Customer Purchases** gruppo, selezionare un cliente dal **clienti** casella combinata.

     Eseguire le azioni seguenti:

    - Il **Products Purchased** menu viene aggiornato per mostrare ogni ordine di vendita per il cliente selezionato.

    - Ogni sottomenu dell'ordine di vendita viene aggiornato in modo da visualizzare i prodotti acquistati in quell'ordine.

    - Indirizzo di posta elettronica al cliente selezionato viene aggiunto per il **a** riga del messaggio di posta elettronica e l'oggetto e corpo del messaggio di posta vengono popolati con il testo.

4. Scegliere il **Products Purchases** menu, selezionare un ordine di vendita e quindi fare clic su un prodotto dall'ordine di vendita.

     Il nome di prodotto viene aggiunto al corpo del messaggio di posta.

## <a name="next-steps"></a>Passaggi successivi

È possibile trovare ulteriori informazioni sulla personalizzazione dell'interfaccia utente di Office nei seguenti argomenti:

- Aggiunta di un'interfaccia utente basata sul contesto a una personalizzazione a livello di documento. Per altre informazioni, vedere [Cenni preliminari sul riquadro azioni](../vsto/actions-pane-overview.md).

- Estensione di un modulo standard o personalizzato di Microsoft Office Outlook. Per altre informazioni, vedere [Procedura dettagliata: Progettare un'area del modulo Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

- Aggiungere un riquadro attività personalizzato a Outlook. Per altre informazioni, vedere [riquadri attività personalizzati](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Vedere anche

- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/index)
- [Procedura: Introduzione alla personalizzazione della barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)
- [Personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Procedura: Modificare la posizione di una scheda della barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Procedura: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)
- [Procedura: Aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Procedura: Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Procedura: Mostra errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)