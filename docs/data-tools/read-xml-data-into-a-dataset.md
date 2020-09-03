---
title: Leggere dati XML in un set di dati
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6cceca336403bdd8907cf0e28e36387eb25a2402
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281786"
---
# <a name="read-xml-data-into-a-dataset"></a>Leggere dati XML in un set di dati

ADO.NET fornisce semplici metodi per l'utilizzo di dati XML. In questa procedura dettagliata viene creata un'applicazione Windows che carica i dati XML in un set di dati. Il set di dati viene quindi visualizzato in un <xref:System.Windows.Forms.DataGridView> controllo. Infine, un XML Schema in base al contenuto del file XML viene visualizzato in una casella di testo.

## <a name="create-a-new-project"></a>Creare un nuovo progetto

Creare un nuovo progetto di **App Windows Forms** per C# o Visual Basic. Denominare il progetto **ReadingXML**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Genera il file XML da leggere nel set di dati

Poiché questa procedura dettagliata è incentrata sulla lettura dei dati XML in un set di dati, viene fornito il contenuto di un file XML.

1. Nel menu **Progetto** selezionare **Aggiungi nuovo elemento**.

2. Selezionare **file XML**, denominare il file **authors.xml**e quindi selezionare **Aggiungi**.

   Il file XML viene caricato nella finestra di progettazione ed è pronto per la modifica.

3. Incollare i dati XML seguenti nell'editor sotto la dichiarazione XML:

   ```xml
   <Authors_Table>
     <authors>
       <au_id>172-32-1176</au_id>
       <au_lname>White</au_lname>
       <au_fname>Johnson</au_fname>
       <phone>408 496-7223</phone>
       <address>10932 Bigge Rd.</address>
       <city>Menlo Park</city>
       <state>CA</state>
       <zip>94025</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>213-46-8915</au_id>
       <au_lname>Green</au_lname>
       <au_fname>Margie</au_fname>
       <phone>415 986-7020</phone>
       <address>309 63rd St. #411</address>
       <city>Oakland</city>
       <state>CA</state>
       <zip>94618</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>238-95-7766</au_id>
       <au_lname>Carson</au_lname>
       <au_fname>Cheryl</au_fname>
       <phone>415 548-7723</phone>
       <address>589 Darwin Ln.</address>
       <city>Berkeley</city>
       <state>CA</state>
       <zip>94705</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>267-41-2394</au_id>
       <au_lname>Hunter</au_lname>
       <au_fname>Anne</au_fname>
       <phone>408 286-2428</phone>
       <address>22 Cleveland Av. #14</address>
       <city>San Jose</city>
       <state>CA</state>
       <zip>95128</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>274-80-9391</au_id>
       <au_lname>Straight</au_lname>
       <au_fname>Dean</au_fname>
       <phone>415 834-2919</phone>
       <address>5420 College Av.</address>
       <city>Oakland</city>
       <state>CA</state>
       <zip>94609</zip>
       <contract>true</contract>
     </authors>
   </Authors_Table>
   ```

4. Scegliere **salva authors.xml**dal menu **file** .

## <a name="create-the-user-interface"></a>Creare l'interfaccia utente

L'interfaccia utente per questa applicazione è costituita dagli elementi seguenti:

- <xref:System.Windows.Forms.DataGridView>Controllo che Visualizza il contenuto del file XML come dati.

- <xref:System.Windows.Forms.TextBox>Controllo che Visualizza il XML Schema per il file XML.

- Due <xref:System.Windows.Forms.Button> controlli.

  - Un pulsante legge il file XML nel set di dati e lo Visualizza nel <xref:System.Windows.Forms.DataGridView> controllo.

  - Un secondo pulsante estrae lo schema dal set di dati e tramite un oggetto <xref:System.IO.StringWriter> lo Visualizza nel <xref:System.Windows.Forms.TextBox> controllo.

### <a name="to-add-controls-to-the-form"></a>Per aggiungere controlli al form

1. Apri `Form1` in visualizzazione progettazione.

2. Dalla **casella degli strumenti**trascinare i controlli seguenti nel form:

    - Un <xref:System.Windows.Forms.DataGridView> controllo

    - Un <xref:System.Windows.Forms.TextBox> controllo

    - Due <xref:System.Windows.Forms.Button> controlli

3. Impostare le proprietà seguenti:

    |Controllo|Proprietà|Impostazione|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**BarreScorrimento**|**Vertical**|
    |`Button1`|**Name**|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**Name**|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Creare il set di dati che riceve i dati XML

In questo passaggio viene creato un nuovo set di dati denominato `authors` . Per altre informazioni sui set di dati, vedere [DataSet Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

1. In **Esplora soluzioni**selezionare il file di origine per **Form1**, quindi selezionare il pulsante **Progettazione viste** sulla barra degli strumenti **Esplora soluzioni** .

2. Dalla [casella degli strumenti, scheda dati](../ide/reference/toolbox-data-tab.md), trascinare un **set** di dati in **Form1**.

3. Nella finestra di dialogo **Aggiungi set di dati** selezionare **set di dati non tipizzato**e quindi fare clic su **OK**.

     **DataSet1** viene aggiunto alla barra dei componenti.

4. Nella finestra **Proprietà** impostare il **nome** e le <xref:System.Data.DataSet.DataSetName%2A> proprietà per `AuthorsDataSet` .

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Creare il gestore eventi per leggere il file XML nel set di dati

Il pulsante **Read XML** legge il file XML nel set di dati. Imposta quindi le proprietà del <xref:System.Windows.Forms.DataGridView> controllo che lo associano al set di dati.

1. In **Esplora soluzioni**selezionare **Form1**, quindi selezionare il pulsante **Progettazione viste** sulla barra degli strumenti **Esplora soluzioni** .

2. Selezionare il pulsante **lettura XML** .

     Viene aperto l' **editor di codice** nel `ReadXmlButton_Click` gestore eventi.

3. Digitare il codice seguente nel `ReadXmlButton_Click` gestore eventi:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4. Nel `ReadXMLButton_Click` codice del gestore eventi modificare la `filepath =` voce nel percorso corretto.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Creare il gestore eventi per visualizzare lo schema nella casella di testo

Il pulsante **Mostra schema** consente di creare un <xref:System.IO.StringWriter> oggetto compilato con lo schema e visualizzato nel <xref:System.Windows.Forms.TextBox> controllo.

1. In **Esplora soluzioni**selezionare **Form1**, quindi fare clic sul pulsante **Visualizza finestra di progettazione** .

2. Selezionare il pulsante **Mostra schema** .

     Viene aperto l' **editor di codice** nel `ShowSchemaButton_Click` gestore eventi.

3. Incollare il codice seguente nel gestore eventi `ShowSchemaButton_Click`.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>Testare il modulo

È ora possibile testare il form per assicurarsi che si comportano come previsto.

1. Selezionare **F5** per eseguire l'applicazione.

2. Selezionare il pulsante **lettura XML** .

     DataGridView Visualizza il contenuto del file XML.

3. Selezionare il pulsante **Mostra schema** .

     Nella casella di testo vengono visualizzati i XML Schema per il file XML.

## <a name="next-steps"></a>Passaggi successivi

In questa procedura dettagliata vengono illustrate le nozioni di base per la lettura di un file XML in un set di dati, nonché per la creazione di uno schema basato sul contenuto del file XML. Di seguito sono riportate alcune attività che è possibile eseguire successivamente:

- Modificare i dati nel set di dati e scriverli di nuovo come XML. Per altre informazioni, vedere <xref:System.Data.DataSet.WriteXml%2A>.

- Modificare i dati nel set di dati e scriverli in un database.

## <a name="see-also"></a>Vedere anche

- [Accedere ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Strumenti XML in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
