---
title: 'Procedura dettagliata: aggiornare i controlli in una barra multifunzione in fase di esecuzione'
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
ms.openlocfilehash: 425918ea32c14e6ba905d6b32864a2844d2b5a90
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255341"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-run-time"></a>Procedura dettagliata: aggiornare i controlli in una barra multifunzione in fase di esecuzione

Questa procedura dettagliata illustra come usare il modello a oggetti della barra multifunzione per aggiornare i controlli su una barra multifunzione dopo che la barra multifunzione è stata caricata nell'applicazione di Office.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

L'esempio usa i dati del database di esempio Northwind per popolare una casella combinata e un menu in Microsoft Office Outlook. Gli elementi selezionati in questi controlli compilano automaticamente i campi, ad esempio, e **sottoposti** **a un** messaggio di posta elettronica.

Vengono illustrate le attività seguenti:

- Creare un nuovo progetto di componente aggiuntivo VSTO per Outlook.

- Progettare un gruppo personalizzato della barra multifunzione.

- Aggiungere il gruppo personalizzato a una scheda incorporata.

- Aggiornare i controlli sulla barra multifunzione in fase di esecuzione.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti

Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Creare un nuovo progetto di componente aggiuntivo VSTO per Outlook

Prima di tutto, creare un progetto di componente aggiuntivo VSTO di Outlook.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Per creare un nuovo progetto di componente aggiuntivo VSTO di Outlook

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] creare un progetto di componente aggiuntivo VSTO di Outlook con il nome **Ribbon_Update_At_Runtime**.

2. Nella finestra di dialogo **Nuovo progetto** selezionare **Crea directory per soluzione**.

3. Salvare il progetto nella directory del progetto predefinita.

     Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Progettare un gruppo della barra multifunzione personalizzato

La barra multifunzione per questo esempio verrà visualizzata quando un utente compone un nuovo messaggio di posta elettronica. Per creare un gruppo personalizzato per la barra multifunzione, aggiungere prima di tutto un elemento della barra multifunzione al progetto e quindi progettare il gruppo nella finestra di progettazione della barra multifunzione. Questo gruppo personalizzato consente di creare messaggi di posta elettronica di completamento per i clienti estraendo i nomi e le cronologie degli ordini da un database.

### <a name="to-design-a-custom-group"></a>Per progettare un gruppo personalizzato

1. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Barra multifunzione (finestra di progettazione visiva)**.

3. Modificare il nome della nuova barra multifunzione in **CustomerRibbon**, quindi fare clic su **Aggiungi**.

     Il file *CustomerRibbon.cs* o *CustomerRibbon. vb* viene aperto nella finestra di progettazione della barra multifunzione e visualizza una scheda e un gruppo predefiniti.

4. Fare clic nella finestra di progettazione per selezionarlo.

5. Nella finestra **Proprietà** fare clic sulla freccia a discesa accanto alla proprietà **RibbonType** , quindi fare clic su **Microsoft. Outlook. mail. compose**.

     Ciò consente di visualizzare la barra multifunzione quando l'utente compone un nuovo messaggio di posta elettronica in Outlook.

6. Nella finestra di progettazione della barra multifunzione fare clic su **Group1** per selezionarlo.

7. Nella finestra **Proprietà** impostare **Label** su **Customer Purchases**.

8. Dalla scheda **controlli barra multifunzione di Office** della **casella degli strumenti**trascinare un controllo **ComboBox** nel gruppo **Customer Purchases** .

9. Fare clic su **ComboBox1** per selezionarlo.

10. Nella finestra **Proprietà** impostare **etichetta** su **Customers**.

11. Dalla scheda **controlli barra multifunzione di Office** della **casella degli strumenti**trascinare un **menu** nel gruppo **Customer Purchases** .

12. Nella finestra **Proprietà** impostare **etichetta** su **prodotto acquistato**.

13. Impostare **dinamico** su **true**.

     In questo modo è possibile aggiungere e rimuovere i controlli nel menu in fase di esecuzione dopo che la barra multifunzione è stata caricata nell'applicazione di Office.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Aggiungere il gruppo personalizzato a una scheda predefinita

Una scheda incorporata è una scheda già presente sulla barra multifunzione di una finestra di esplorazione o di un controllo di Outlook. In questa procedura, si aggiunge il gruppo personalizzato a una scheda predefinita e quindi si specifica la posizione del gruppo personalizzato nella scheda.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Per aggiungere il gruppo personalizzato a una scheda predefinita

1. Fare clic sulla scheda **TabAddIns (built-in)** per selezionarla.

2. Nella finestra **Proprietà** espandere la proprietà **ControlID** , quindi impostare **OfficeId** su **TabNewMailMessage**.

     Il gruppo **Customer Purchases** viene aggiunto alla scheda **messaggi** della barra multifunzione visualizzata in un nuovo messaggio di posta elettronica.

3. Fare clic sul gruppo **Customer Purchases** per selezionarlo.

4. Nella finestra **Proprietà** espandere la proprietà **posizione** , fare clic sulla freccia a discesa accanto alla proprietà **PositionType** , quindi fare clic su **BeforeOfficeId**.

5. Impostare la proprietà **OfficeId** su **GroupClipboard**.

     Il gruppo **Customer Purchases** viene posizionato prima del gruppo **Appunti** della scheda **messaggi** .

## <a name="create-the-data-source"></a>Creare l'origine dati

Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.

### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1. Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.

     Viene avviata la **Configurazione guidata origine dati**.

2. Selezionare **database**, quindi fare clic su **Avanti**.

3. Selezionare **DataSet**, quindi fare clic su **Avanti**.

4. Selezionare una connessione dati all'esempio Northwind Microsoft SQL Server Compact database 4,0 o aggiungere una nuova connessione usando il pulsante **nuova connessione** .

5. Dopo aver selezionato o creato una connessione, fare clic su **Avanti**.

6. Fare clic su **Avanti** per salvare la stringa di connessione.

7. Nella pagina **Seleziona oggetti di database** espandere **tabelle**.

8. Selezionare la casella di controllo accanto a ciascuna delle seguenti tabelle:

    1. **Clienti**

    2. **Dettagli ordine**

    3. **Orders**

    4. **Prodotti**

9. Fare clic su **Fine**.

## <a name="update-controls-in-the-custom-group-at-run-time"></a>Aggiornare i controlli nel gruppo personalizzato in fase di esecuzione

Usare il modello a oggetti della barra multifunzione per effettuare le seguenti attività:

- Aggiungere i nomi dei clienti alla casella combinata **Customers** .

- Aggiungere i controlli menu e Button al menu **prodotti acquistati** che rappresentano gli ordini di vendita e i prodotti venduti.

- Consente di popolare i campi a, oggetto e corpo dei nuovi messaggi di posta elettronica utilizzando i dati della casella combinata **clienti** e il menu **prodotti acquistati** .

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Per aggiornare i controlli nel gruppo personalizzato usando il modello a oggetti della barra multifunzione

1. Scegliere **Aggiungi riferimento** dal menu **Progetto**.

2. Nella finestra di dialogo **Aggiungi riferimento** fare clic sulla scheda **.NET** , selezionare l'assembly **System. Data. Linq** , quindi fare clic su **OK**.

    Questo assembly contiene le classi per l'uso di Language-Integrated Queries (LINQ). LINQ viene usato per popolare i controlli nel gruppo personalizzato con i dati del database Northwind.

3. In **Esplora soluzioni**fare clic su **CustomerRibbon.cs** o **CustomerRibbon. vb** per selezionarlo.

4. Scegliere **Codice** dal menu **Visualizza**.

    Il file di codice della barra multifunzione viene aperto nell'editor di codice.

5. Aggiungere le seguenti istruzioni alla parte iniziale del file di codice della barra multifunzione. Queste istruzioni forniscono l'accesso agli spazi dei nomi LINQ e allo spazio dei nomi dell'assembly di interoperabilità primario (PIA) di Outlook.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. Aggiungere il codice seguente all'interno della `CustomerRibbon` classe. Il codice dichiara la tabella dati e gli adattatori di tabella che verranno usati per archiviare le informazioni delle tabelle Clienti, Ordini, Dettagli sugli ordini e Prodotti del database Northwind.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7.  Aggiungere il seguente blocco di codice alla classe `CustomerRibbon`. Questo codice aggiunge tre metodi helper per la creazione di controlli per la barra multifunzione in fase di esecuzione.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. Sostituire il metodo del gestore eventi `CustomerRibbon_Load` con il codice seguente. Questo codice usa una query LINQ per eseguire le attività seguenti:

   - Popolare la casella combinata **Customers** usando l'ID e il nome di 20 clienti nel database Northwind.

   - Chiama il metodo di supporto `PopulateSalesOrderInfo`. Questo metodo aggiorna il menu **ProductsPurchased** con i numeri degli ordini di vendita relativi al cliente attualmente selezionato.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. Aggiungere il codice seguente alla classe `CustomerRibbon` . Questo codice usa le query LINQ per eseguire le attività seguenti:

   - Aggiunge un sottomenu al menu **ProductsPurchased** per ogni ordine di vendita correlato al cliente selezionato.

   - Aggiungere pulsanti a ogni sottomenu per i prodotti relativi all'ordine di vendita.

   - Aggiungere gestori eventi a ogni pulsante.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. In **Esplora soluzioni**fare doppio clic sul file di codice della barra multifunzione.

     La finestra di progettazione della barra multifunzione viene aperta.

11. Nella finestra di progettazione della barra multifunzione fare doppio clic sulla casella combinata **Customers** .

     Nell'editor di codice viene aperto il file di codice della barra multifunzione e viene visualizzato il gestore eventi `ComboBox1_TextChanged`.

12. Sostituire il gestore eventi `ComboBox1_TextChanged` con il codice seguente. Il codice esegue queste operazioni:

    - Chiama il metodo di supporto `PopulateSalesOrderInfo`. Questo metodo aggiorna il menu **prodotti acquistati** con gli ordini di vendita correlati al cliente selezionato.

    - Chiama il metodo di supporto `PopulateMailItem` e passa al testo corrente, ossia il nome del cliente selezionato. Questo metodo popola i campi a, oggetto e corpo dei nuovi messaggi di posta elettronica.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. Aggiungere il gestore eventi `Click` seguente alla classe `CustomerRibbon` . Questo codice aggiunge il nome dei prodotti selezionati al campo body dei nuovi messaggi di posta elettronica.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. Aggiungere il codice seguente alla classe `CustomerRibbon` . Il codice esegue queste operazioni:

    - Popola la riga a dei nuovi messaggi di posta elettronica utilizzando l'indirizzo di posta elettronica del cliente attualmente selezionato.

    - Aggiunge testo ai campi oggetto e corpo dei nuovi messaggi di posta elettronica.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>Testare i controlli nel gruppo personalizzato

Quando si apre un nuovo modulo di posta elettronica in Outlook, un gruppo personalizzato denominato **Customer Purchases** viene visualizzato nella scheda **messaggi** della barra multifunzione.

Per creare un messaggio di posta elettronica di completamento per i clienti, selezionare un cliente, quindi selezionare i prodotti acquistati dal cliente. I controlli del gruppo **Customer Purchases** vengono aggiornati in fase di esecuzione con i dati del database Northwind.

### <a name="to-test-the-controls-in-the-custom-group"></a>Per testare i controlli nel gruppo personalizzato

1. Premere **F5** per eseguire il progetto.

     Viene avviato Outlook.

2. In Outlook scegliere **nuovo**dal menu **file** , quindi fare clic su **messaggio di posta elettronica**.

     Si verificano le azioni seguenti:

    - Viene visualizzata una nuova finestra di controllo del messaggio di posta.

    - Nella scheda **messaggio** della barra multifunzione, il gruppo **Customer Purchases** viene visualizzato prima del gruppo **Clipboard** .

    - La casella combinata **Customers** del gruppo viene aggiornata con i nomi dei clienti nel database Northwind.

3. Nella scheda **messaggio** della barra multifunzione, nel gruppo **Customer Purchases** , selezionare un cliente dalla casella combinata **Customers** .

     Si verificano le azioni seguenti:

    - Il menu **prodotti acquistati** viene aggiornato per visualizzare ogni ordine di vendita per il cliente selezionato.

    - Ogni sottomenu dell'ordine di vendita viene aggiornato in modo da visualizzare i prodotti acquistati in quell'ordine.

    - L'indirizzo di posta elettronica del cliente selezionato viene aggiunto alla riga **a** del messaggio di posta elettronica e l'oggetto e il corpo del messaggio di posta elettronica vengono popolati con il testo.

4. Fare clic sul menu **Products Purchases** , scegliere un ordine di vendita e quindi fare clic su un prodotto dell'ordine di vendita.

     Il nome di prodotto viene aggiunto al corpo del messaggio di posta.

## <a name="next-steps"></a>Passaggi successivi

È possibile trovare ulteriori informazioni sulla personalizzazione dell'interfaccia utente di Office nei seguenti argomenti:

- Aggiunta di un'interfaccia utente basata sul contesto a una personalizzazione a livello di documento. Per altre informazioni, vedere [Cenni preliminari sul riquadro azioni](../vsto/actions-pane-overview.md).

- Estensione di un modulo standard o personalizzato di Microsoft Office Outlook. Per altre informazioni, vedere [procedura dettagliata: progettare un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

- Aggiungere un riquadro attività personalizzato a Outlook. Per ulteriori informazioni, vedere [riquadri attività personalizzati](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Vedere anche

- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/index)
- [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Procedura dettagliata: creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)
- [Personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Procedura: modificare la posizione di una scheda nella barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)
- [Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Procedura: esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione a XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Procedura: visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)