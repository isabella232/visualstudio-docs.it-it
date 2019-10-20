---
title: Leggere dati XML in un set di dati
ms.date: 11/04/2016
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6dec7cad50d818d4b2418442d8196cb8b5ff046a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641372"
---
# <a name="read-xml-data-into-a-dataset"></a>Leggere dati XML in un set di dati

ADO.NET fornisce semplici metodi per l'utilizzo di dati XML. In questa procedura dettagliata viene creata un'applicazione Windows che carica i dati XML in un set di dati. Il set di dati viene quindi visualizzato in un controllo <xref:System.Windows.Forms.DataGridView>. Infine, un XML Schema in base al contenuto del file XML viene visualizzato in una casella di testo.

## <a name="create-a-new-project"></a>Creare un nuovo progetto

Creare un nuovo progetto di **App Windows Forms** per C# o Visual Basic. Denominare il progetto **ReadingXML**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Genera il file XML da leggere nel set di dati

Poiché questa procedura dettagliata è incentrata sulla lettura dei dati XML in un set di dati, viene fornito il contenuto di un file XML.

1. Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.

2. Selezionare **file XML**, denominare il file **authors. XML**e quindi selezionare **Aggiungi**.

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

4. Nel menu **file** selezionare **Salva authors. XML**.

## <a name="create-the-user-interface"></a>Creare l'interfaccia utente

L'interfaccia utente per questa applicazione è costituita dagli elementi seguenti:

- Controllo <xref:System.Windows.Forms.DataGridView> che Visualizza il contenuto del file XML come dati.

- Controllo <xref:System.Windows.Forms.TextBox> che visualizza la XML Schema per il file XML.

- Due controlli <xref:System.Windows.Forms.Button>.

  - Un pulsante legge il file XML nel set di dati e lo Visualizza nel controllo <xref:System.Windows.Forms.DataGridView>.

  - Un secondo pulsante estrae lo schema dal set di dati e tramite un <xref:System.IO.StringWriter> lo Visualizza nel controllo <xref:System.Windows.Forms.TextBox>.

### <a name="to-add-controls-to-the-form"></a>Per aggiungere controlli al form

1. Aprire `Form1` nella visualizzazione progettazione.

2. Dalla **casella degli strumenti**trascinare i controlli seguenti nel form:

    - Un controllo <xref:System.Windows.Forms.DataGridView>

    - Un controllo <xref:System.Windows.Forms.TextBox>

    - Due controlli <xref:System.Windows.Forms.Button>

3. Impostare le proprietà seguenti:

    |Control|proprietà|Impostazioni|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**ScrollBars**|**Verticale**|
    |`Button1`|**Nome**|`ReadXmlButton`|
    ||**Testo**|`Read XML`|
    |`Button2`|**Nome**|`ShowSchemaButton`|
    ||**Testo**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Creare il set di dati che riceve i dati XML

In questo passaggio viene creato un nuovo set di dati denominato `authors`. Per altre informazioni sui set di dati, vedere [DataSet Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

1. In **Esplora soluzioni**selezionare il file di origine per **Form1**, quindi selezionare il pulsante **Progettazione viste** sulla barra degli strumenti **Esplora soluzioni** .

2. Dalla [casella degli strumenti, scheda dati](../ide/reference/toolbox-data-tab.md), trascinare un **set** di dati in **Form1**.

3. Nella finestra di dialogo **Aggiungi set di dati** selezionare **set di dati non tipizzato**e quindi fare clic su **OK**.

     **DataSet1** viene aggiunto alla barra dei componenti.

4. Nella finestra **Proprietà** impostare il **nome** e le proprietà di <xref:System.Data.DataSet.DataSetName%2A> per `AuthorsDataSet`.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Creare il gestore eventi per leggere il file XML nel set di dati

Il pulsante **Read XML** legge il file XML nel set di dati. Imposta quindi le proprietà sul controllo <xref:System.Windows.Forms.DataGridView> che lo associano al set di dati.

1. In **Esplora soluzioni**selezionare **Form1**, quindi selezionare il pulsante **Progettazione viste** sulla barra degli strumenti **Esplora soluzioni** .

2. Selezionare il pulsante **lettura XML** .

     Viene aperto l' **editor di codice** nel gestore dell'evento `ReadXmlButton_Click`.

3. Digitare il codice seguente nel gestore dell'evento `ReadXmlButton_Click`:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4. Nel codice del gestore eventi `ReadXMLButton_Click` modificare la voce `filepath =` nel percorso corretto.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Creare il gestore eventi per visualizzare lo schema nella casella di testo

Il pulsante **Mostra schema** consente di creare un <xref:System.IO.StringWriter> oggetto compilato con lo schema e visualizzato nella <xref:System.Windows.Forms.TextBox>control.

1. In **Esplora soluzioni**selezionare **Form1**, quindi fare clic sul pulsante **Visualizza finestra di progettazione** .

2. Selezionare il pulsante **Mostra schema** .

     Viene aperto l' **editor di codice** nel gestore dell'evento `ShowSchemaButton_Click`.

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

- Modificare i dati nel set di dati e scriverli di nuovo come XML. Per ulteriori informazioni, vedere <xref:System.Data.DataSet.WriteXml%2A>.

- Modificare i dati nel set di dati e scriverli in un database.

## <a name="see-also"></a>Vedere anche

- [Accedere ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Strumenti XML in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
