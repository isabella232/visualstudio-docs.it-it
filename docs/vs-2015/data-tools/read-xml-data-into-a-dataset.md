---
title: Leggere dati XML in un set di dati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c34fb87c02ff60d9b28c43130d6fbf3a12e70349
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652899"
---
# <a name="read-xml-data-into-a-dataset"></a>Leggere dati XML in un set di dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ADO.NET fornisce semplici metodi per l'utilizzo di dati XML. In questa procedura dettagliata viene creata un'applicazione Windows che carica i dati XML in un set di dati. Il set di dati viene quindi visualizzato in un controllo <xref:System.Windows.Forms.DataGridView>. Infine, un XML Schema in base al contenuto del file XML viene visualizzato in una casella di testo.

 Questa procedura dettagliata è costituita da cinque passaggi principali:

1. Creazione di un nuovo progetto

2. Creazione di un file XML da leggere nel set di dati

3. Creazione dell'interfaccia utente

4. Creazione del set di dati, lettura del file XML e visualizzazione in un controllo <xref:System.Windows.Forms.DataGridView>

5. Aggiunta di codice per visualizzare il XML Schema in base al file XML in un controllo <xref:System.Windows.Forms.TextBox>

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione in uso. Per modificare le impostazioni, scegliere**Importa/Esporta impostazioni**dal menu **strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-new-project"></a>Creare un nuovo progetto
 In questo passaggio viene creato un Visual Basic o un progetto C# visuale che contiene questa procedura dettagliata.

#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows

1. Scegliere Crea nuovo progetto dal menu **file** .

2. Denominare il progetto `ReadingXML`.

3. Selezionare **applicazione Windows**e quindi fare clic su **OK**. Per ulteriori informazioni, vedere [applicazioni client](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Il progetto **ReadingXML** viene creato e aggiunto a **Esplora soluzioni**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Genera il file XML da leggere nel set di dati
 Poiché questa procedura dettagliata è incentrata sulla lettura dei dati XML in un set di dati, viene fornito il contenuto di un file XML.

#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Per creare il file XML che verrà letto nel set di dati

1. Scegliere**Aggiungi nuovo elemento**dal menu **progetto** .

2. Selezionare **file XML**, denominare il file `authors.xml` e quindi selezionare **Aggiungi**.

     Il file XML viene caricato nella finestra di progettazione ed è pronto per la modifica.

3. Incollare il codice seguente nell'editor sotto la dichiarazione XML:

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

4. Nel menu **file** selezionare**Salva authors. XML**.

## <a name="create-the-user-interface"></a>Creare l'interfaccia utente
 L'interfaccia utente per questa applicazione è costituita dagli elementi seguenti:

- Controllo <xref:System.Windows.Forms.DataGridView> che Visualizza il contenuto del file XML come dati.

- Controllo <xref:System.Windows.Forms.TextBox> che visualizza la XML Schema per il file XML.

- Due controlli <xref:System.Windows.Forms.Button>.

  - Un pulsante legge il file XML nel set di dati e lo Visualizza nel controllo <xref:System.Windows.Forms.DataGridView>.

  - Un secondo pulsante estrae lo schema dal set di dati e tramite un <xref:System.IO.StringWriter> lo Visualizza nel controllo <xref:System.Windows.Forms.TextBox>.

#### <a name="to-add-controls-to-the-form"></a>Per aggiungere controlli al form

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

## <a name="create-the-dataset-thatreceives-the-xml-data"></a>Creare il set di dati thatreceives i dati XML
 In questo passaggio viene creato un nuovo set di dati denominato `authors`. Per altre informazioni sui set di dati, vedere [DataSet Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>Per creare un nuovo set di dati che riceve i dati XML

1. In **Esplora soluzioni**selezionare il file di origine per **Form1**, quindi selezionare il pulsante **Progettazione viste** sulla barra degli strumenti **Esplora soluzioni** .

2. Dalla [casella degli strumenti, scheda dati](../ide/reference/toolbox-data-tab.md), trascinare un **set** di dati in **Form1**.

3. Nella finestra di dialogo **Aggiungi set di dati** selezionare **set di dati non tipizzato**e quindi fare clic su **OK**.

     **DataSet1** viene aggiunto alla barra dei componenti.

4. Nella finestra **Proprietà** impostare il **nome** e le proprietà di <xref:System.Data.DataSet.DataSetName%2A> per `AuthorsDataSet`.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Creare il gestore eventi per leggere il file XML nel set di dati
 Il pulsante **Read XML** legge il file XML nel set di dati. Imposta quindi le proprietà sul controllo <xref:System.Windows.Forms.DataGridView> che lo associano al set di dati.

#### <a name="to-add-code-to-the-readxmlbutton_click-event-handler"></a>Per aggiungere codice al gestore eventi ReadXmlButton_Click

1. In **Esplora soluzioni**selezionare **Form1**, quindi selezionare il pulsante **Progettazione viste** sulla barra degli strumenti **Esplora soluzioni** .

2. Selezionare il pulsante **lettura XML** .

     Viene aperto l' **editor di codice** nel gestore dell'evento `ReadXmlButton_Click`.

3. Digitare il codice seguente nel gestore dell'evento `ReadXmlButton_Click`:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]

4. Nel codice del gestore eventi `ReadXMLButton_Click` modificare la voce `filepath =` nel percorso corretto.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Creare il gestore eventi per visualizzare lo schema nella casella di testo
 Il pulsante **Mostra schema** consente di creare un <xref:System.IO.StringWriter> oggetto compilato con lo schema e visualizzato nella <xref:System.Windows.Forms.TextBox>control.

#### <a name="to-add-code-to-the-showschemabutton_click-event-handler"></a>Per aggiungere codice al gestore eventi ShowSchemaButton_Click

1. In **Esplora soluzioni**selezionare **Form1**, quindi fare clic sul pulsante **Visualizza finestra di progettazione** .

2. Selezionare il pulsante **Mostra schema** .

     Viene aperto l' **editor di codice** nel gestore dell'evento `ShowSchemaButton_Click`.

3. Digitare il codice seguente nel gestore dell'evento `ShowSchemaButton_Click`.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]

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
 [Procedure dettagliate relative ai dati](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) [accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [preparazione dell'applicazione per la ricezione di](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [strumenti XML di dati in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
