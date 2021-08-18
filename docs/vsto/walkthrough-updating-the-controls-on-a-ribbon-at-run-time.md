---
title: 'Procedura dettagliata: Aggiornare i controlli in una barra multifunzione in fase di esecuzione'
description: Informazioni su come usare il modello a oggetti della barra multifunzione per aggiornare i controlli in una barra multifunzione dopo il caricamento della barra multifunzione nell'applicazione Office barra multifunzione.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2d53e3ca57781052cf4691dd010496246a6010f7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046074"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-run-time"></a>Procedura dettagliata: Aggiornare i controlli in una barra multifunzione in fase di esecuzione

Questa procedura dettagliata illustra come usare il modello a oggetti della barra multifunzione per aggiornare i controlli in una barra multifunzione dopo il caricamento della barra multifunzione nell'Office app.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

L'esempio usa i dati del database di esempio Northwind per popolare una casella combinata e un menu in Microsoft Office Outlook. Gli elementi selezionati in questi controlli popolano automaticamente campi come **A** e **Oggetto** in un messaggio di posta elettronica.

Vengono illustrate le attività seguenti:

- Creare un nuovo Outlook VSTO di componente aggiuntivo.

- Progettare un gruppo personalizzato della barra multifunzione.

- Aggiungere il gruppo personalizzato a una scheda incorporata.

- Aggiornare i controlli sulla barra multifunzione in fase di esecuzione.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti

Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Creare un nuovo Outlook VSTO di componente aggiuntivo

Prima di tutto, creare un progetto di componente aggiuntivo VSTO di Outlook.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Per creare un nuovo progetto di componente aggiuntivo VSTO di Outlook

1. In creare un progetto Outlook VSTO componente aggiuntivo con il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nome **Ribbon_Update_At_Runtime**.

2. Nella finestra di dialogo **Nuovo progetto** selezionare **Crea directory per soluzione**.

3. Salvare il progetto nella directory del progetto predefinita.

     Per altre informazioni, vedere [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Progettare un gruppo personalizzato della barra multifunzione

La barra multifunzione per questo esempio verrà visualizzata quando un utente compone un nuovo messaggio di posta elettronica. Per creare un gruppo personalizzato per la barra multifunzione, aggiungere prima un elemento Barra multifunzione al progetto e quindi progettare il gruppo nella finestra di progettazione della barra multifunzione. Questo gruppo personalizzato consente di generare messaggi di posta elettronica di follow-up ai clienti estraendo nomi e cronologie degli ordini da un database.

### <a name="to-design-a-custom-group"></a>Per progettare un gruppo personalizzato

1. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Barra multifunzione (finestra di progettazione visiva)**.

3. Modificare il nome della nuova barra multifunzione in **CustomerRibbon** e quindi fare clic su **Aggiungi**.

     Il file *CustomerRibbon.cs* o *CustomerRibbon.vb* viene aperto nella finestra di progettazione della barra multifunzione e visualizza una scheda e un gruppo predefiniti.

4. Fare clic nella finestra di progettazione per selezionarlo.

5. Nella finestra **Proprietà** fare clic sulla freccia a discesa accanto alla proprietà **RibbonType** e quindi fare clic su **Microsoft.Outlook.Mail.Compose**.

     In questo modo la barra multifunzione viene visualizzata quando l'utente compone un nuovo messaggio di posta Outlook.

6. Nella finestra di progettazione della barra multifunzione fare **clic su Group1** per selezionarla.

7. Nella finestra **Proprietà** impostare **Etichetta** su **Customer Purchases**.

8. Dalla scheda **Office Controlli barra** multifunzione della Casella degli strumenti trascinare un controllo **ComboBox** nel **gruppo Customer Purchases.** 

9. Fare **clic su ComboBox1** per selezionarlo.

10. Nella finestra **Proprietà** impostare **Etichetta** su **Clienti**.

11. Dalla scheda **Office controlli barra** multifunzione della Casella **degli** strumenti trascinare un **menu** nel gruppo **Customer Purchases.**

12. Nella finestra **Proprietà** impostare **Etichetta** su **Prodotto acquistato**.

13. Impostare **Dynamic** su **true.**

     In questo modo è possibile aggiungere e rimuovere controlli nel menu in fase di esecuzione dopo che la barra multifunzione è stata caricata nell Office app.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Aggiungere il gruppo personalizzato a una scheda incorporata

Una scheda incorporata è una scheda già presente nella barra multifunzione di un Outlook Explorer o Inspector. In questa procedura, si aggiunge il gruppo personalizzato a una scheda predefinita e quindi si specifica la posizione del gruppo personalizzato nella scheda.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Per aggiungere il gruppo personalizzato a una scheda predefinita

1. Fare clic **sulla scheda TabAggiungi (predefiniti)** per selezionarla.

2. Nella finestra **Proprietà** espandere la **proprietà ControlId** e quindi impostare **OfficeId** su **TabNewMailMessage**.

     Il gruppo **Customer Purchases verrà** aggiunto alla scheda **Messaggi** della barra multifunzione visualizzata in un nuovo messaggio di posta elettronica.

3. Fare clic **sul gruppo Customer Purchases** (Acquisti clienti) per selezionarlo.

4. Nella finestra **Proprietà** espandere la **proprietà Position,** fare clic sulla freccia a discesa accanto alla **proprietà PositionType** e quindi fare clic **su BeforeOfficeId**.

5. Impostare la **proprietà OfficeId** su **GroupClipboard**.

     In questo modo il **gruppo Customer Purchases** viene posizionato prima **del gruppo Appunti** della **scheda** Messaggi.

## <a name="create-the-data-source"></a>Creare l'origine dati

Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.

### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1. Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.

     Verrà avviata la **Configurazione guidata origine dati**.

2. Selezionare **Database** e quindi fare clic su **Avanti.**

3. Selezionare **Set di** dati e quindi fare clic su **Avanti.**

4. Selezionare una connessione dati al database di esempio Northwind Microsoft SQL Server Compact 4.0 oppure aggiungere una nuova connessione usando il **pulsante Nuova** connessione.

5. Dopo aver selezionato o creato una connessione, fare clic su **Avanti.**

6. Fare **clic su** Avanti per salvare la stringa di connessione.

7. Nella pagina **Scegliere gli oggetti di database** espandere **Tabelle**.

8. Selezionare la casella di controllo accanto a ciascuna delle seguenti tabelle:

    1. **Clienti**

    2. **Dettagli dell'ordine**

    3. **Orders**

    4. **Prodotti**

9. Fare clic su **Fine**.

## <a name="update-controls-in-the-custom-group-at-run-time"></a>Aggiornare i controlli nel gruppo personalizzato in fase di esecuzione

Usare il modello a oggetti della barra multifunzione per effettuare le seguenti attività:

- Aggiungere i nomi dei clienti **alla casella combinata** Customers.

- Aggiungere i controlli menu e pulsante al menu **Prodotti acquistati** che rappresentano gli ordini di vendita e i prodotti venduti.

- Popolare i campi A, Oggetto e Corpo dei nuovi messaggi di posta elettronica usando i dati della casella combinata **Clienti** e del menu **Prodotti acquistati.**

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Per aggiornare i controlli nel gruppo personalizzato usando il modello a oggetti della barra multifunzione

1. Scegliere **Aggiungi riferimento** dal menu **Progetto**.

2. Nella finestra **di dialogo Aggiungi** riferimento fare clic sulla scheda **.NET,** selezionare l'assembly **System.Data.Linq** e quindi fare clic su **OK.**

    Questo assembly contiene le classi per l'uso di Language-Integrated Queries (LINQ). LINQ viene usato per popolare i controlli nel gruppo personalizzato con i dati del database Northwind.

3. In **Esplora soluzioni** fare clic **su CustomerRibbon.cs** o **CustomerRibbon.vb** per selezionarlo.

4. Scegliere **Codice** dal menu **Visualizza**.

    Il file di codice della barra multifunzione viene aperto nell'editor di codice.

5. Aggiungere le seguenti istruzioni alla parte iniziale del file di codice della barra multifunzione. Queste istruzioni forniscono l'accesso agli spazi dei nomi LINQ e allo spazio dei nomi dell'assembly di interoperabilità primario (PIA) di Outlook.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet1":::

6. Aggiungere il codice seguente all'interno della `CustomerRibbon` classe . Il codice dichiara la tabella dati e gli adattatori di tabella che verranno usati per archiviare le informazioni delle tabelle Clienti, Ordini, Dettagli sugli ordini e Prodotti del database Northwind.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet2":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet2":::

7.  Aggiungere il seguente blocco di codice alla classe `CustomerRibbon`. Questo codice aggiunge tre metodi helper che creano controlli per la barra multifunzione in fase di esecuzione.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet3":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet3":::

8. Sostituire il metodo del gestore eventi `CustomerRibbon_Load` con il codice seguente. Questo codice usa una query LINQ per eseguire le attività seguenti:

   - Popolare la casella **combinata Customers** usando l'ID e il nome di 20 clienti nel database Northwind.

   - Chiama il metodo di supporto `PopulateSalesOrderInfo`. Questo metodo aggiorna il menu **ProductsPurchased** con i numeri degli ordini di vendita relativi al cliente attualmente selezionato.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet4":::

9. Aggiungere il codice seguente alla classe `CustomerRibbon` . Questo codice usa le query LINQ per eseguire le attività seguenti:

   - Aggiunge un sottomenu al menu **ProductsPurchased** per ogni ordine di vendita correlato al cliente selezionato.

   - Aggiungere pulsanti a ogni sottomenu per i prodotti relativi all'ordine di vendita.

   - Aggiungere gestori eventi a ogni pulsante.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet6":::

10. In **Esplora soluzioni** fare doppio clic sul file di codice della barra multifunzione.

     La finestra di progettazione della barra multifunzione viene aperta.

11. Nella finestra di progettazione della barra multifunzione fare doppio clic sulla **casella combinata** Customers.

     Nell'editor di codice viene aperto il file di codice della barra multifunzione e viene visualizzato il gestore eventi `ComboBox1_TextChanged`.

12. Sostituire il gestore eventi `ComboBox1_TextChanged` con il codice seguente. Il codice esegue queste operazioni:

    - Chiama il metodo di supporto `PopulateSalesOrderInfo`. Questo metodo aggiorna il menu **Prodotti acquistati** con gli ordini di vendita correlati al cliente selezionato.

    - Chiama il metodo di supporto `PopulateMailItem` e passa al testo corrente, ossia il nome del cliente selezionato. Questo metodo popola i campi A, Oggetto e Corpo dei nuovi messaggi di posta elettronica.

      :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet5":::
      :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet5":::

13. Aggiungere il gestore eventi `Click` seguente alla classe `CustomerRibbon` . Questo codice aggiunge il nome dei prodotti selezionati al campo Corpo dei nuovi messaggi di posta elettronica.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet8":::

14. Aggiungere il codice seguente alla classe `CustomerRibbon` . Il codice esegue queste operazioni:

    - Popola la riga A dei nuovi messaggi di posta elettronica usando l'indirizzo di posta elettronica del cliente attualmente selezionato.

    - Aggiunge testo ai campi Oggetto e Corpo dei nuovi messaggi di posta elettronica.

      :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet7":::
      :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet7":::

## <a name="test-the-controls-in-the-custom-group"></a>Testare i controlli nel gruppo personalizzato

Quando si apre un nuovo modulo di posta elettronica in Outlook,  nella scheda Messaggi della barra multifunzione viene visualizzato un gruppo personalizzato denominato **Customer Purchases.**

Per creare un messaggio di posta elettronica di follow-up del cliente, selezionare un cliente e quindi selezionare i prodotti acquistati dal cliente. I controlli nel **gruppo Customer Purchases** vengono aggiornati in fase di esecuzione con i dati del database Northwind.

### <a name="to-test-the-controls-in-the-custom-group"></a>Per testare i controlli nel gruppo personalizzato

1. Premere **F5** per eseguire il progetto.

     Viene avviato Outlook.

2. Nel Outlook scegliere Nuovo  dal menu File **e** quindi fare clic su **Messaggio di posta**.

     Si verificano le azioni seguenti:

    - Viene visualizzata una nuova finestra di controllo del messaggio di posta.

    - Nella scheda **Messaggio** della barra multifunzione il **gruppo Customer Purchases** viene visualizzato prima del **gruppo Appunti.**

    - La **casella** combinata Customers nel gruppo viene aggiornata con i nomi dei clienti nel database Northwind.

3. Nel **gruppo** Customer **Purchases** della scheda Messaggio della barra multifunzione selezionare un cliente dalla **casella combinata** Clienti.

     Si verificano le azioni seguenti:

    - Il menu **Prodotti acquistati** viene aggiornato per visualizzare ogni ordine di vendita per il cliente selezionato.

    - Ogni sottomenu dell'ordine di vendita viene aggiornato in modo da visualizzare i prodotti acquistati in quell'ordine.

    - L'indirizzo di posta elettronica del cliente selezionato viene aggiunto alla riga **A** del messaggio di posta elettronica e l'oggetto e il corpo del messaggio di posta elettronica vengono popolati con testo.

4. Fare clic sul menu **Products Purchases** ,scegliere qualsiasi ordine di vendita e quindi fare clic su un prodotto nell'ordine di vendita.

     Il nome di prodotto viene aggiunto al corpo del messaggio di posta.

## <a name="next-steps"></a>Passaggi successivi

È possibile trovare ulteriori informazioni sulla personalizzazione dell'interfaccia utente di Office nei seguenti argomenti:

- Aggiunta di un'interfaccia utente basata sul contesto a una personalizzazione a livello di documento. Per altre informazioni, vedere Panoramica [del riquadro Azioni](../vsto/actions-pane-overview.md).

- Estensione di un modulo standard o personalizzato di Microsoft Office Outlook. Per altre informazioni, vedere [Procedura dettagliata: Progettare un'area Outlook modulo](../vsto/walkthrough-designing-an-outlook-form-region.md).

- Aggiungere un riquadro attività personalizzato a Outlook. Per altre informazioni, vedere [Riquadri attività personalizzati](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Vedi anche

- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/index)
- [Procedura: Iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)
- [Personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Procedura: Modificare la posizione di una scheda sulla barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Procedura: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)
- [Procedura: Aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Procedura: Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione al codice XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Procedura: Visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)