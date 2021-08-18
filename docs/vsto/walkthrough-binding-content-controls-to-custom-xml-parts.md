---
title: 'Procedura dettagliata: Associare controlli contenuto a parti XML personalizzate'
description: Informazioni su come associare i controlli contenuto in una personalizzazione a livello di documento per Word ai dati XML archiviati nel documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PlainTextContentControl, binding to a custom XML part
- custom XML parts, binding to content controls
- content controls [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], content controls
- DropDownListContentControl, binding items to a custom XML part
- DatePickerContentControl, binding to a custom XML part
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 506b919be7a6e84bf6710166e09da4df7d1e7c2d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147713"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>Procedura dettagliata: Associare controlli contenuto a parti XML personalizzate
  Questa procedura dettagliata illustra come associare i controlli contenuto in una personalizzazione a livello di documento per Word a dati XML archiviati nel documento.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Word consente di archiviare dati XML, denominati *parti XML personalizzate,* in un documento. È possibile controllare la visualizzazione di questi dati associando i controlli contenuto a elementi in una parte XML personalizzata. Il documento di esempio in questa procedura dettagliata visualizza informazioni sui dipendenti che vengono archiviate in una parte XML personalizzata. Quando si apre il documento, i controlli contenuto visualizzano i valori degli elementi XML. Nella parte XML personalizzata vengono salvate le eventuali modifiche apportate al testo nei controlli contenuto.

 Vengono illustrate le attività seguenti:

- Aggiunta di controlli contenuto al documento di Word presente in un progetto a livello di documento in fase di progettazione.

- Creazione di un file di dati XML e di uno schema XML che definisce gli elementi da associare ai controlli contenuto.

- Associazione dello schema XML al documento in fase di progettazione.

- Aggiunta dei contenuti del file XML a una parte XML personalizzata nel documento in fase di progettazione.

- Binding dei controlli contenuto a elementi nella parte XML personalizzata.

- Associazione di <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a un set di valori definiti nello schema XML.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-document-project"></a>Creare un nuovo progetto di documento di Word
 Creare un documento di Word che verrà usato nella procedura dettagliata.

### <a name="to-create-a-new-word-document-project"></a>Per creare un progetto di documento di Word

1. Creare un progetto di documento di Word con il nome **EmployeeControls.** Creare un nuovo documento per la soluzione. Per altre informazioni, [vedere Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre il nuovo documento di Word nella finestra di progettazione e aggiunge il **progetto EmployeeControls** **Esplora soluzioni**.

## <a name="add-content-controls-to-the-document"></a>Aggiungere controlli contenuto al documento
 Creare una tabella che contiene tre tipi diversi di controlli contenuto in cui un utente può visualizzare o modificare informazioni su un dipendente.

### <a name="to-add-content-controls-to-the-document"></a>Per aggiungere controlli contenuto al documento

1. Nel documento di Word ospitato nella finestra di progettazione scegliere la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] scheda Inserisci sulla **barra** multifunzione.

2. Nel gruppo **Tabelle** scegliere **Tabella e** inserire una tabella con 2 colonne e 3 righe.

3. Digitare il testo nella prima colonna in modo che sia simile alla colonna seguente:

   ||
   |-|
   |**Nome dipendente**|
   |**Data assunzione**|
   |**Title**|

4. Nella seconda colonna della tabella scegliere la prima riga (accanto a **Employee Name**).

5. Sulla barra multifunzione scegliere la **scheda** Sviluppatore.

   > [!NOTE]
   > Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: Visualizzare la scheda Sviluppatore sulla barra multifunzione.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

6. Nel gruppo **Controlli** scegliere il pulsante **Testo** ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") per aggiungere <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> un oggetto alla prima cella.

7. Nella seconda colonna della tabella scegliere la seconda riga (accanto a **Hire Date**).

8. Nel gruppo **Controlli** scegliere il pulsante **Selezione data** ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> oggetto alla seconda cella.

9. Nella seconda colonna della tabella scegliere la terza riga (accanto a **Titolo**).

10. Nel gruppo **Controlli** scegliere il **pulsante Elenco a** discesa ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") per aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> all'ultima cella.

    È l'intera interfaccia utente per questo progetto. Se si esegue il progetto a questo punto, è possibile digitare un testo nella prima riga e selezionare una data nella seconda riga. Il passaggio successivo consiste nell'allegare i dati che si vogliano visualizzare al documento in un file XML.

## <a name="create-the-xml-data-file"></a>Creare il file di dati XML
 In genere, si ottengono dati XML da archiviare in una parte XML personalizzata da un'origine esterna, ad esempio un file o un database. In questa procedura dettagliata è possibile creare un file XML che contiene i dati del dipendente, contrassegnati da elementi che verranno associati ai controlli contenuto del documento. Per rendere disponibili i dati in fase di esecuzione, incorporare il file XML come risorsa nell'assembly di personalizzazione.

#### <a name="to-create-the-data-file"></a>Per creare il file di dati

1. Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento** .

2. Nel riquadro **Modelli** selezionare **File XML.**

3. Assegnare al file **employees.xml** e quindi scegliere **il pulsante** Aggiungi.

     Il **employees.xml** file viene aperto nell'editor di codice.

4. Sostituire il contenuto del file **employees.xml** con il testo seguente.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">
      <employee>
        <name>Karina Leal</name>
        <hireDate>1999-04-01</hireDate>
        <title>Manager</title>
      </employee>
    </employees>
    ```

5. In **Esplora soluzioni** scegliere il file **employees.xml.**

6. Nella finestra **Proprietà** selezionare la proprietà **Azione di** compilazione e quindi modificare il valore in **Risorsa incorporata.**

     Questo passaggio incorpora il file XML come risorsa nell'assembly quando si compila il progetto. e consente di accedere al contenuto del file XML in fase di esecuzione.

## <a name="create-an-xml-schema"></a>Creare uno schema XML
 Se si intende associare un controllo contenuto a un singolo elemento in una parte XML personalizzata, non è necessario usare uno schema XML. Tuttavia, per associare <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a un set di valori, è necessario creare uno schema XML che convalida il file di dati XML creato in precedenza. Lo schema XML definisce i valori possibili per l'elemento `title`. L'associazione di <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a questo elemento viene eseguita più avanti in questa procedura dettagliata.

#### <a name="to-create-an-xml-schema"></a>Per creare uno schema XML

1. Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento** .

2. Nel riquadro **Modelli** selezionare **XML Schema.**

3. Assegnare allo schema **il nome employees.xsd** e scegliere **il pulsante** Aggiungi.

     Viene aperta la progettazione schema.

4. In **Esplora soluzioni** aprire il menu di scelta rapida  **per employees.xsd** e quindi scegliere  **Visualizza codice**.

5. Sostituire il contenuto del file **employees.xsd** con lo schema seguente.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"
        targetNamespace="http://schemas.microsoft.com/vsto/samples"
        xmlns:xs="http://www.w3.org/2001/XMLSchema"
        elementFormDefault="qualified">
      <xs:element name="employees" type="EmployeesType"></xs:element>
      <xs:complexType name="EmployeesType">
        <xs:all>
          <xs:element name="employee" type="EmployeeType"/>
        </xs:all>
      </xs:complexType>
      <xs:complexType name="EmployeeType">
        <xs:sequence>
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>
        </xs:sequence>
      </xs:complexType>
      <xs:simpleType name="TitleType">
        <xs:restriction base="xs:string">
          <xs:enumeration value ="Engineer"/>
          <xs:enumeration value ="Designer"/>
          <xs:enumeration value ="Manager"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:schema>
    ```

6. Scegliere **Salva** tutto dal menu File **per** salvare le modifiche **apportate ai fileemployees.xml** e **employees.xsd.**

## <a name="attach-the-xml-schema-to-the-document"></a>Allegare l'XML Schema al documento
 È necessario allegare lo schema XML al documento per associare <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> ai valori validi dell'elemento `title`.

### <a name="to-attach-the-xml-schema-to-the-document--word_15_short"></a>Per collegare l'XML Schema al documento ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] )

1. Attivare **EmployeeControls.docx** nella finestra di progettazione.

2. Sulla barra multifunzione scegliere la **scheda** Sviluppatore e quindi scegliere il **pulsante Componenti** aggiuntivi.

3. Nella finestra **di dialogo Modelli e componenti** aggiuntivi scegliere la scheda XML **Schema** e quindi scegliere il **pulsante Aggiungi** schema.

4. Passare allo schema **employees.xsd** creato in precedenza, che si trova nella directory del progetto, quindi scegliere il **pulsante** Apri.

5. Scegliere il **pulsante OK** nella finestra di **dialogo Impostazioni** schema .

6. Scegliere il **pulsante OK** per chiudere la finestra di dialogo Modelli **e componenti** aggiuntivi .

### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>Per allegare lo schema XML al documento (Word 2010)

1. Attivare **EmployeeControls.docx** nella finestra di progettazione.

2. Sulla barra multifunzione scegliere la **scheda** Sviluppatore.

3. Nel **gruppo XML** scegliere il **pulsante Schema.**

4. Nella finestra **di dialogo Modelli e componenti** aggiuntivi scegliere la scheda XML **Schema** e quindi scegliere il **pulsante Aggiungi** schema.

5. Passare allo schema **employees.xsd** creato in precedenza, che si trova nella directory del progetto, e scegliere il **pulsante** Apri.

6. Scegliere il **pulsante OK** nella finestra di **dialogo Impostazioni** schema .

7. Scegliere il **pulsante OK** per chiudere la finestra di dialogo Modelli **e componenti** aggiuntivi .

     Verrà **visualizzato il riquadro** attività Struttura XML .

8. Chiudere il **riquadro attività Struttura XML** .

## <a name="add-a-custom-xml-part-to-the-document"></a>Aggiungere una parte XML personalizzata al documento
 Prima di poter associare i controlli contenuto a elementi nel file XML, è necessario aggiungere il contenuto del file XML a una nuova parte XML personalizzata nel documento.

### <a name="to-add-a-custom-xml-part-to-the-document"></a>Per aggiungere una parte XML personalizzata al documento

1. In **Esplora soluzioni** aprire il menu di scelta rapida per **ThisDocument.cs** o **ThisDocument.vb** e quindi scegliere **Visualizza codice.**

2. Aggiungere le seguenti dichiarazioni alla classe `ThisDocument`. Questo codice dichiara diversi oggetti che verranno usati per aggiungere una parte XML personalizzata al documento.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet1":::

3. Aggiungi alla classe `ThisDocument` il metodo seguente. Questo metodo ottiene il contenuto del file di dati XML incorporato come risorsa nell'assembly e restituisce il contenuto come stringa XML.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet3":::

4. Aggiungi alla classe `ThisDocument` il metodo seguente. Il metodo crea `AddCustomXmlPart` una nuova parte XML personalizzata che contiene una stringa XML che viene passata al metodo.

     Per garantire che la parte XML personalizzata venga creata solo una volta, il metodo crea la parte XML personalizzata solo se non esiste già nel documento una parte XML personalizzata con GUID corrispondente. La prima volta che viene chiamato questo metodo, viene salvato il valore della proprietà <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> per la stringa `employeeXMLPartID`. Il valore della stringa `employeeXMLPartID` viene mantenuto nel documento perché è stato dichiarato mediante l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet4":::

## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Associare i controlli contenuto agli elementi nella parte XML personalizzata
 Associare ogni controllo contenuto a un elemento nella parte XML personalizzata usando la **proprietà XMLMapping** di ogni controllo contenuto.

### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Per associare i controlli contenuto a elementi nella parte XML personalizzata

1. Aggiungi alla classe `ThisDocument` il metodo seguente. Questo metodo associa ogni controllo del contenuto a un elemento nella parte XML personalizzata e imposta il formato di visualizzazione della data di <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet5":::

## <a name="run-your-code-when-the-document-is-opened"></a>Eseguire il codice all'apertura del documento
 Creare la parte XML personalizzata e associare i controlli personalizzati ai dati quando il documento viene aperto.

### <a name="to-run-your-code-when-the-document-is-opened"></a>Per eseguire il codice quando il documento è aperto

1. Aggiungere il seguente codice al metodo `ThisDocument_Startup` della classe `ThisDocument`. Questo codice ottiene la stringa XML dal file **employees.xml,** aggiunge la stringa XML a una nuova parte XML personalizzata nel documento e associa i controlli contenuto agli elementi nella parte XML personalizzata.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet2":::

## <a name="test-the-project"></a>Testare il progetto
 Quando si apre il documento, i controlli contenuto consentono di visualizzare dati dagli elementi nella parte XML personalizzata. È possibile fare clic su per selezionare uno dei tre valori validi per l'elemento <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> , definiti nel file `title` **employees.xsd.** Se si modificano i dati in uno dei controlli contenuto, i nuovi valori vengono salvati nella parte XML personalizzata del documento.

### <a name="to-test-the-content-controls"></a>Per testare i controlli contenuto

1. Premere **F5** per eseguire il progetto.

2. Verificare che la tabella nel documento sia simile alla tabella seguente. Tutte le stringhe della seconda colonna sono ottenute da un elemento nella parte XML personalizzata del documento.

    |Colonna|valore|
    |-|-|
    |**Nome dipendente**|**Karina Leal**|
    |**Data assunzione**|**1 aprile 1999**|
    |**Title**|**Responsabile**|

3. Scegliere la cella a destra della cella **Nome** dipendente e digitare un nome diverso.

4. Scegliere la cella a destra della cella **Hire Date (Data** assunzione) e selezionare una data diversa nella selezione data.

5. Scegliere la cella a destra della cella **Titolo** e selezionare un nuovo elemento dall'elenco a discesa.

6. Salvare e chiudere il documento.

7. In Esplora file aprire la *cartella \bin\Debug* nel percorso del progetto.

8. Aprire il menu di scelta rapida **EmployeeControls.docx** e quindi scegliere **Rinomina.**

9. Assegnare al file **ilEmployeeControls.docx.zip**.

     Il **EmployeeControls.docx** viene salvato in formato Open XML. Rinominando questo documento con *l'.zip* di file, è possibile esaminare il contenuto del documento. Per altre informazioni su Open XML, vedere l'articolo tecnico [Introducing the Office (2007) Open XML file formats (Introduzione](/previous-versions/office/developer/office-2007/aa338205(v=office.12))ai formati di file Open XML del 2007).

10. Aprire il file **EmployeeControls.docx.zip.**

11. Aprire la **cartella customXml.**

12. Aprire il menu di scelta rapida **item2.xml** e quindi scegliere **Apri.**

     Il file contiene la parte XML personalizzata che è stata aggiunta al documento.

13. Verificare che gli elementi `name`, `hireDate` e `title` contengano i nuovi valori immessi nei controlli contenuto nel documento.

14. Chiudere il file **item2.xml.**

## <a name="next-steps"></a>Passaggi successivi
 Per altre informazioni sull'utilizzo dei controlli contenuto, vedere gli argomenti seguenti:

- Usare tutti i controlli contenuto disponibili per creare un modello. Per altre informazioni, vedere [Procedura dettagliata: Creare un modello usando i controlli contenuto.](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)

- Modificare i dati nella parte XML personalizzata mentre il documento è chiuso. Alla successiva apertura del documento, i controlli contenuto associati agli elementi XML visualizzeranno i nuovi dati.

- Usare i controlli contenuto per proteggere parti di un documento. Per altre informazioni, vedere [Procedura: Proteggere parti di documenti usando i controlli contenuto.](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)

## <a name="see-also"></a>Vedi anche
- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Controlli contenuto](../vsto/content-controls.md)
- [Procedura: Aggiungere controlli contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Procedura: Proteggere parti di documenti usando i controlli contenuto](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Aggiungere controlli ai Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
