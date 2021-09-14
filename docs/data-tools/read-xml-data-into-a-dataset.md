---
title: Leggere dati XML in un set di dati
description: Leggere i dati XML in un set di dati. In questa procedura dettagliata viene creata un'Windows che carica i dati XML in un set di dati.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9fe6058713abf66ab173f4ddf77e9ff71a03bb74
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631241"
---
# <a name="read-xml-data-into-a-dataset"></a>Leggere dati XML in un set di dati

ADO.NET fornisce metodi semplici per l'uso dei dati XML. In questa procedura dettagliata viene creata un'Windows che carica i dati XML in un set di dati. Il set di dati viene quindi visualizzato in un <xref:System.Windows.Forms.DataGridView> controllo . Infine, in una casella di testo viene visualizzato uno schema XML basato sul contenuto del file XML.

## <a name="create-a-new-project"></a>Creare un nuovo progetto

Creare un nuovo **progetto Windows'app Forms** per C# o Visual Basic. Assegnare al progetto il **nome ReadingXML**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Generare il file XML da leggere nel set di dati

Poiché questa procedura dettagliata è incentrata sulla lettura di dati XML in un set di dati, viene fornito il contenuto di un file XML.

1. Nel menu **Progetto** selezionare **Aggiungi nuovo elemento**.

2. Selezionare **File XML,** assegnare al file il **nomeauthors.xml** e quindi selezionare **Aggiungi**.

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

4. Scegliere **Salva** dal menu File **authors.xml**.

## <a name="create-the-user-interface"></a>Creare l'interfaccia utente

L'interfaccia utente per questa applicazione è costituita dai seguenti elementi:

- Controllo <xref:System.Windows.Forms.DataGridView> che visualizza il contenuto del file XML come dati.

- Controllo <xref:System.Windows.Forms.TextBox> che visualizza lo schema XML per il file XML.

- Due <xref:System.Windows.Forms.Button> controlli.

  - Un pulsante legge il file XML nel set di dati e lo visualizza nel <xref:System.Windows.Forms.DataGridView> controllo .

  - Un secondo pulsante estrae lo schema dal set di dati e tramite un oggetto <xref:System.IO.StringWriter> lo visualizza nel controllo <xref:System.Windows.Forms.TextBox> .

### <a name="to-add-controls-to-the-form"></a>Per aggiungere controlli al form

1. Aprire `Form1` nella visualizzazione Progettazione.

2. Dalla Casella **degli strumenti** trascinare i controlli seguenti nel form:

    - Un <xref:System.Windows.Forms.DataGridView> controllo

    - Un <xref:System.Windows.Forms.TextBox> controllo

    - Due <xref:System.Windows.Forms.Button> controlli

3. Impostare le proprietà seguenti:

    |Controllo|Proprietà|Impostazione|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**BarreScorrimento**|**Vertical**|
    |`Button1`|**Nome**|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**Nome**|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Creare il set di dati che riceve i dati XML

In questo passaggio viene creato un nuovo set di dati denominato `authors` . Per altre informazioni sui set di dati, vedere [Strumenti per set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

1. In **Esplora soluzioni** selezionare il file di origine per **Form1** e quindi selezionare il pulsante Progettazione visualizzazioni sulla barra **degli strumenti Esplora soluzioni.** 

2. Dalla casella [degli strumenti, scheda Dati](../ide/reference/toolbox-data-tab.md), trascinare un **DataSet** in **Form1.**

3. Nella finestra **di dialogo** Aggiungi set di dati selezionare **Untyped dataset (Set di dati non tipizzato)** e quindi **ok**.

     **DataSet1** viene aggiunto alla barra dei componenti.

4. Nella finestra **Proprietà** impostare il nome **e** <xref:System.Data.DataSet.DataSetName%2A> le proprietà per `AuthorsDataSet` .

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Creare il gestore eventi per leggere il file XML nel set di dati

Il **pulsante Leggi XML** legge il file XML nel set di dati. Imposta quindi le proprietà del <xref:System.Windows.Forms.DataGridView> controllo che lo associano al set di dati.

1. In **Esplora soluzioni** selezionare **Form1** e quindi selezionare il pulsante Progettazione visualizzazioni **sulla** barra Esplora soluzioni barra **degli strumenti.**

2. Selezionare il **pulsante Leggi XML.**

     **L'editor di** codice viene aperto in corrispondenza `ReadXmlButton_Click` del gestore eventi.

3. Digitare il codice seguente nel `ReadXmlButton_Click` gestore eventi:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb" id="Snippet2":::

4. Nel codice `ReadXMLButton_Click` del gestore eventi modificare la voce nel percorso `filepath =` corretto.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Creare il gestore eventi per visualizzare lo schema nella casella di testo

Il **pulsante Mostra** schema crea un oggetto che viene <xref:System.IO.StringWriter> riempito con lo schema e viene visualizzato nel <xref:System.Windows.Forms.TextBox> controllo .

1. In **Esplora soluzioni** selezionare **Form1** e quindi selezionare il pulsante **Progettazione visualizzazioni.**

2. Selezionare il **pulsante Mostra** schema.

     **L'editor di** codice viene aperto in corrispondenza `ShowSchemaButton_Click` del gestore eventi.

3. Incollare il codice seguente nel gestore eventi `ShowSchemaButton_Click`.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb" id="Snippet3":::

## <a name="test-the-form"></a>Testare il modulo

È ora possibile testare il modulo per assicurarsi che si comporti come previsto.

1. Selezionare **F5 per** eseguire l'applicazione.

2. Selezionare il **pulsante Leggi XML.**

     DataGridView visualizza il contenuto del file XML.

3. Selezionare il **pulsante Mostra** schema.

     Nella casella di testo viene visualizzato lo schema XML per il file XML.

## <a name="next-steps"></a>Passaggi successivi

Questa procedura dettagliata illustra le nozioni di base sulla lettura di un file XML in un set di dati, nonché sulla creazione di uno schema in base al contenuto del file XML. Ecco alcune attività che è possibile eseguire successivamente:

- Modificare i dati nel set di dati e scriverne di nuovo come XML. Per altre informazioni, vedere <xref:System.Data.DataSet.WriteXml%2A>.

- Modificare i dati nel set di dati e scriverlo in un database.

## <a name="see-also"></a>Vedi anche

- [Accedere ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Strumenti XML in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
