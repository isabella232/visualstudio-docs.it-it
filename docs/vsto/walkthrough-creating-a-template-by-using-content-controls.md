---
title: 'Procedura dettagliata: Creare un modello usando i controlli contenuto'
description: Informazioni su come creare una personalizzazione a livello di documento che usa i controlli contenuto per creare contenuto strutturato e riutilizzabile in un modello Microsoft Word documento.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d977aeb7eb4b16dab4de957df2a7b908fba58b18
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075733"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>Procedura dettagliata: Creare un modello usando i controlli contenuto
  Questa procedura dettagliata mostra come creare una personalizzazione a livello di documento che usa i controlli contenuto per creare contenuti strutturati e riutilizzabili in un modello di Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Word consente di creare una raccolta di parti di documento riutilizzabili, denominate *blocchi predefiniti.* Questa procedura dettagliata mostra come creare due tabelle come blocchi predefiniti. Ogni tabella contiene diversi controlli contenuto che possono includere diversi tipi di contenuto, ad esempio testo normale o date. Una delle tabelle contiene informazioni su un dipendente, mentre un'altra contiene i suggerimenti del cliente.

 Dopo aver creato un documento dal modello, è possibile aggiungere una delle tabelle al documento usando diversi oggetti <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>, che visualizzano i blocchi predefiniti disponibili nel modello.

 Vengono illustrate le attività seguenti:

- Creazione di una tabella contenente i controlli contenuto in un modello di Word in fase di progettazione.

- Popolamento a livello di codice di un controllo contenuto della casella combinata e di un controllo contenuto dell'elenco a discesa.

- Impedire agli utenti di modificare una tabella specificata.

- Aggiunta di tabelle alla raccolta di blocchi predefiniti di un modello.

- Creazione di un controllo contenuto che visualizza i blocchi predefiniti disponibili nel modello.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-template-project"></a>Creare un nuovo progetto di modello di Word
 Creare un modello di Word in modo che gli utenti possano creare facilmente le proprie copie.

### <a name="to-create-a-new-word-template-project"></a>Per creare un nuovo progetto di modello di Word

1. Creare un progetto modello di Word con il nome **MyBuildingBlockTemplate**. Nella procedura guidata creare un nuovo documento nella soluzione. Per altre informazioni, vedere [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre il nuovo modello di Word nella finestra di progettazione e aggiunge il **progetto MyBuildingBlockTemplate** **Esplora soluzioni**.

## <a name="create-the-employee-table"></a>Creare la tabella employee
 Creare una tabella che contiene quattro tipi differenti di controlli contenuto in cui un utente può immettere le informazioni su un dipendente.

### <a name="to-create-the-employee-table"></a>Per creare la tabella dei dipendenti

1. Nella barra multifunzione del modello di Word ospitato nella finestra di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progettazione fare clic sulla **scheda** Inserisci.

2. Nel gruppo **Tabelle** fare clic su **Tabella** e inserire una tabella con due colonne e quattro righe.

3. Digitare il testo nella prima colonna in modo che sia simile alla colonna seguente:

   ||
   |-|
   |**Nome dipendente**|
   |**Data assunzione**|
   |**Title**|
   |**Immagine**|

4. Fare clic nella prima cella della seconda colonna (accanto a **Employee Name**).

5. Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .

   > [!NOTE]
   > Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: Visualizzare la scheda Sviluppatore sulla barra multifunzione.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

6. Nel gruppo **Controlli** fare clic sul **pulsante Testo** ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> oggetto alla prima cella.

7. Fare clic sulla seconda cella nella seconda colonna (accanto a **Hire Date**).

8. Nel gruppo **Controlli** fare clic sul **pulsante Selezione data** ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") per aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> alla seconda cella.

9. Fare clic sulla terza cella nella seconda colonna (accanto a **Titolo**).

10. Nel gruppo **Controlli** fare clic sul **pulsante Casella combinata** ![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl") per aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> alla terza cella.

11. Fare clic sull'ultima cella nella seconda colonna (accanto a **Immagine**).

12. Nel gruppo **Controlli** fare clic sul **pulsante Picture Content Control** ![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl") per aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.PictureContentControl> all'ultima cella.

## <a name="create-the-customer-feedback-table"></a>Creare la tabella dei commenti e suggerimenti dei clienti
 Creare una tabella che contiene tre tipi differenti di controlli contenuto in cui un utente può immettere le informazioni relative ai suggerimenti dei clienti.

### <a name="to-create-the-customer-feedback-table"></a>Per creare una tabella dei suggerimenti dei clienti

1. Nel modello di Word fare clic sulla riga dopo la tabella employee aggiunta in precedenza e premere **INVIO** per aggiungere un nuovo paragrafo.

2. Sulla barra multifunzione fare clic sulla **scheda** Inserisci.

3. Nel gruppo **Tabelle** fare clic su **Tabella** e inserire una tabella con due colonne e tre righe.

4. Digitare il testo nella prima colonna in modo che sia simile alla colonna seguente:

   ||
   |-|
   |**Nome cliente**|
   |**Valutazione soddisfazione**|
   |**Commenti**|

5. Fare clic nella prima cella della seconda colonna (accanto a **Nome cliente**).

6. Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .

7. Nel gruppo **Controlli** fare clic sul **pulsante Testo** ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> oggetto alla prima cella.

8. Fare clic nella seconda cella della seconda colonna (accanto a **Valutazione soddisfazione**).

9. Nel gruppo **Controlli** fare clic sul **pulsante Elenco** a discesa ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") per aggiungere un controllo <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> alla seconda cella.

10. Fare clic nell'ultima cella della seconda colonna (accanto a **Commenti**).

11. Nel gruppo **Controlli** fare clic sul pulsante ![RichTextContentControl richTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") per aggiungere un oggetto  <xref:Microsoft.Office.Tools.Word.RichTextContentControl> all'ultima cella.

## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>Popolare la casella combinata e l'elenco a discesa a livello di codice
 È possibile inizializzare i controlli contenuto in fase di progettazione usando la **finestra Proprietà** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . È anche possibile inizializzarli in fase di esecuzione. In questo caso gli stati iniziali possono essere impostati dinamicamente. Per questa procedura dettagliata, usare il codice per popolare le voci in e in fase di esecuzione in modo da poter <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> vedere il funzionamento di questi <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> oggetti.

### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>Per modificare l'interfaccia utente dei controlli contenuto a livello di codice

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **ThisDocument.cs** **o ThisDocument.vb** e quindi scegliere **Visualizza codice**.

2. Aggiungere il codice seguente alla classe `ThisDocument` . Questo codice dichiara diversi oggetti che verranno usati più avanti nella procedura dettagliata.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet1":::

3. Aggiungere il seguente codice al metodo `ThisDocument_Startup` della classe `ThisDocument`. Questo codice aggiunge voci a <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> e <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> nelle tabelle e imposta il testo del segnaposto visualizzato in ciascun controllo prima che l'utente apporti modifiche.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet2":::

## <a name="prevent-users-from-editing-the-employee-table"></a>Impedire agli utenti di modificare la tabella employee
 Usare l'oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> dichiarato in precedenza per proteggere la tabella dei dipendenti. Dopo aver protetto la tabella, gli utenti possono comunque modificarne i controlli contenuto. Tuttavia, non possono modificare il testo nella prima colonna o modificare la tabella in altri modi, ad esempio aggiungendo o rimuovendo righe e colonne. Per altre informazioni su come usare un oggetto per proteggere una parte <xref:Microsoft.Office.Tools.Word.GroupContentControl> di un documento, vedere [Controlli contenuto](../vsto/content-controls.md).

### <a name="to-prevent-users-from-editing-the-employee-table"></a>Per impedire agli utenti di modificare la tabella dei dipendenti

1. Aggiungere il codice seguente al metodo `ThisDocument_Startup` della classe `ThisDocument` dopo il codice aggiunto nel passaggio precedente. Questo codice impedisce agli utenti di modificare la tabella dei dipendenti inserendo la tabella all'interno dell'oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> dichiarato in precedenza.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet3":::

## <a name="add-the-tables-to-the-building-block-collection"></a>Aggiungere le tabelle alla raccolta di blocchi predefiniti
 Aggiungere le tabelle a una raccolta di blocchi predefiniti del documento nel modello in modo che gli utenti possano inserire le tabelle create all'interno di quel documento. Per altre informazioni sui blocchi predefiniti del documento, vedere [Controlli contenuto](../vsto/content-controls.md).

### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>Per aggiungere le tabelle ai blocchi predefiniti nel modello

1. Aggiungere il codice seguente al metodo `ThisDocument_Startup` della classe `ThisDocument` dopo il codice aggiunto nel passaggio precedente. Questo codice aggiunge nuovi blocchi predefiniti che contengono le tabelle a Microsoft. Office. Raccolta Interop.Word.BuildingBlockEntries, che contiene tutti i blocchi predefiniti riutilizzabili nel modello. I nuovi blocchi predefiniti sono definiti in una nuova categoria denominata **Employee and Customer Information** e vengono assegnati al tipo di blocco predefinito `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet4":::

2. Aggiungere il codice seguente al metodo `ThisDocument_Startup` della classe `ThisDocument` dopo il codice aggiunto nel passaggio precedente. Questo codice elimina le tabelle dal modello. Le tabelle non sono più necessarie perché sono state aggiunte alla raccolta di blocchi predefiniti riutilizzabili nel modello. Il codice passa innanzitutto il documento in modalità progettazione in modo che la tabella dei dipendenti protetta possa essere eliminata.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet5":::

## <a name="create-a-content-control-that-displays-the-building-blocks"></a>Creare un controllo contenuto che visualizzi i blocchi predefiniti
 Creare un controllo contenuto che fornisca l'accesso ai blocchi predefiniti (ossia, alle tabelle) create in precedenza. Gli utenti possono selezionare questo controllo per aggiungere le tabelle al documento.

### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>Per creare un controllo contenuto che visualizza i blocchi predefiniti

1. Aggiungere il codice seguente al metodo `ThisDocument_Startup` della classe `ThisDocument` dopo il codice aggiunto nel passaggio precedente. Il codice inizializza l'oggetto <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> dichiarato in precedenza. Visualizza tutti i blocchi predefiniti definiti nella categoria Employee e Customer Information e che <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> hanno il tipo di blocco predefinito  `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet6":::

## <a name="test-the-project"></a>Testare il progetto
 Gli utenti possono fare clic sui controlli della raccolta di blocchi predefiniti nel documento per inserire la tabella dei dipendenti o la tabella dei suggerimenti dei clienti. Gli utenti possono digitare o selezionare le risposte nei controlli contenuto in entrambe le tabelle. Gli utenti possono modificare altre parti della tabella dei suggerimenti dei clienti, ma non devono poter modificare altre parti della tabella dei dipendenti.

### <a name="to-test-the-employee-table"></a>Per testare la tabella dei dipendenti

1. Premere **F5** per eseguire il progetto.

2. Fare **clic su Choose your first building block (Scegli** il primo blocco predefinito) per visualizzare il primo controllo contenuto della raccolta di blocchi predefiniti.

3. Fare clic sulla freccia a discesa accanto all'intestazione Raccolta personalizzata **1** nel controllo e selezionare **Tabella dipendenti**.

4. Fare clic nella cella a destra della cella **Nome** dipendente e digitare un nome.

     Verificare di poter aggiungere solo testo alla cella. <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> consente agli utenti di aggiungere solo testo, non altri tipi di contenuto, ad esempio grafici o tabelle.

5. Fare clic nella cella a destra della cella **Hire Date** e selezionare una data nella selezione data.

6. Fare clic nella cella a destra della cella **Titolo** e selezionare uno dei titoli di mansione nella casella combinata.

     Facoltativamente, digitare il nome di un titolo professionale non presente nell'elenco. <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>, infatti, consente agli utenti di effettuare una selezione da un elenco di voci oppure di digitare le voci personalizzate.

7. Fare clic sull'icona nella cella a destra della **cella Immagine** e passare a un'immagine per visualizzarla.

8. Provare ad aggiungere e quindi a eliminare le righe o le colonne dalla tabella. Verificare che non sia possibile modificare la tabella. <xref:Microsoft.Office.Tools.Word.GroupContentControl> impedisce di apportare modifiche.

### <a name="to-test-the-customer-feedback-table"></a>Per testare la tabella dei suggerimenti dei clienti

1. Fare **clic su Choose your second building block (Scegli** il secondo blocco predefinito) per visualizzare il secondo controllo contenuto della raccolta di blocchi predefiniti.

2. Fare clic sulla freccia a discesa accanto **all'intestazione Raccolta** personalizzata 1 nel controllo e selezionare **Tabella clienti**.

3. Fare clic nella cella a destra della cella **Nome cliente** e digitare un nome.

4. Fare clic nella cella a destra della cella **Valutazione soddisfazione** e selezionare una delle opzioni disponibili.

     Verificare che non sia possibile digitare una voce personalizzata. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> consente di selezionare solo da un elenco di voci.

5. Fare clic nella cella a destra della **cella** Commenti e digitare alcuni commenti.

     Facoltativamente, aggiungere alcuni contenuti diversi dal testo, ad esempio un grafico o una tabella incorporata. <xref:Microsoft.Office.Tools.Word.RichTextContentControl> consente, infatti, agli utenti di aggiungere contenuti diversi dal testo.

6. Verificare di poter aggiungere e quindi eliminare le righe o le colonne dalla tabella. Ciò è possibile perché la tabella non è stata protetta inserendola in <xref:Microsoft.Office.Tools.Word.GroupContentControl>.

7. Chiudere il modello.

## <a name="next-steps"></a>Passaggi successivi
 Per altre informazioni sull'utilizzo dei controlli contenuto, vedere l'argomento seguente:

- Associare controlli contenuto a parti del codice XML, chiamate anche parti XML personalizzate, incorporate in un documento. Per altre informazioni, vedere [Procedura dettagliata: Associare controlli contenuto a parti XML personalizzate.](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)

## <a name="see-also"></a>Vedi anche
- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Controlli contenuto](../vsto/content-controls.md)
- [Procedura: Aggiungere controlli contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Procedura: Proteggere parti di documenti usando i controlli contenuto](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Aggiungere controlli ai Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
