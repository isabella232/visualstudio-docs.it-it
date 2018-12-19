---
title: 'Procedura dettagliata: Associare controlli contenuto a parti XML personalizzate'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d48c0e1921c57923021e88a2a4a5bb5f89763ef1
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673303"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>Procedura dettagliata: Associare controlli contenuto a parti XML personalizzate
  Questa procedura dettagliata illustra come associare i controlli contenuto in una personalizzazione a livello di documento per Word a dati XML archiviati nel documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word consente di archiviare dati XML, denominati *parti XML personalizzate*, in un documento. È possibile controllare la visualizzazione di questi dati associando i controlli contenuto a elementi in una parte XML personalizzata. Il documento di esempio in questa procedura dettagliata visualizza informazioni sui dipendenti che vengono archiviate in una parte XML personalizzata. Quando si apre il documento, i controlli contenuto visualizzano i valori degli elementi XML. Nella parte XML personalizzata vengono salvate le eventuali modifiche apportate al testo nei controlli contenuto.  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Aggiunta di controlli contenuto al documento di Word presente in un progetto a livello di documento in fase di progettazione.  
  
-   Creazione di un file di dati XML e di uno schema XML che definisce gli elementi da associare ai controlli contenuto.  
  
-   Associazione dello schema XML al documento in fase di progettazione.  
  
-   Aggiunta del contenuto del file XML a una parte XML personalizzata nel documento in fase di esecuzione.  
  
-   Binding dei controlli contenuto a elementi nella parte XML personalizzata.  
  
-   Binding di <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a un set di valori definiti nello schema XML.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="create-a-new-word-document-project"></a>Creare un nuovo progetto di documento di Word  
 Creare un documento di Word che verrà usato nella procedura dettagliata.  
  
### <a name="to-create-a-new-word-document-project"></a>Per creare un progetto di documento di Word  
  
1.  Creare un progetto documento di Word con il nome **EmployeeControls**. Creare un nuovo documento per la soluzione. Per altre informazioni, vedere [procedura: progetti di Office di creare in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Apre il nuovo documento di Word nella finestra di progettazione e aggiunge il **EmployeeControls** progetto al **Esplora soluzioni**.  
  
## <a name="add-content-controls-to-the-document"></a>Aggiungere controlli contenuto al documento  
 Creare una tabella che contiene tre tipi diversi di controlli contenuto in cui un utente può visualizzare o modificare informazioni su un dipendente.  
  
### <a name="to-add-content-controls-to-the-document"></a>Per aggiungere controlli contenuto al documento  
  
1.  Nel documento di Word ospitato nella [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer, sulla barra multifunzione, scegliere il **Inserisci** scheda.  
  
2.  Nel **tabelle** gruppo, scegliere **tabella**e inserire una tabella con 2 colonne e 3 righe.  
  
3.  Digitare il testo nella prima colonna in modo che sia simile alla colonna seguente:  
  
    ||  
    |-|  
    |**Nome del dipendente**|  
    |**Data di assunzione**|  
    |**Titolo**|  
  
4.  Nella seconda colonna della tabella, scegliere la prima riga (accanto a **Employee Name**).  
  
5.  Sulla barra multifunzione scegliere la **sviluppatore** scheda.  
  
    > [!NOTE]  
    >  Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [procedura: visualizzare la scheda sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  Nel **controlli** gruppo, scegliere il **testo** pulsante ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>alla prima cella.  
  
7.  Nella seconda colonna della tabella, scegliere la seconda riga (accanto a **Data assunzione**).  
  
8.  Nel **controlli** gruppo, scegliere il **Date Picker** pulsante ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> alla seconda cella.  
  
9. Nella seconda colonna della tabella, selezionare la terza riga (accanto a **titolo**).  
  
10. Nel **controlli** gruppo, scegliere il **elenco a discesa** pulsante ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") da aggiungere un <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> all'ultima cella.  
  
 È l'intera interfaccia utente per questo progetto. Se si esegue il progetto a questo punto, è possibile digitare un testo nella prima riga e selezionare una data nella seconda riga. Il passaggio successivo consiste nell'allegare i dati che si vogliano visualizzare al documento in un file XML.  
  
## <a name="create-the-xml-data-file"></a>Creare il file di dati XML  
 In genere, si ottengono dati XML da archiviare in una parte XML personalizzata da un'origine esterna, ad esempio un file o un database. In questa procedura dettagliata è possibile creare un file XML che contiene i dati del dipendente, contrassegnati da elementi che verranno associati ai controlli contenuto del documento. Per rendere disponibili i dati in fase di esecuzione, incorporare il file XML come risorsa nell'assembly di personalizzazione.  
  
#### <a name="to-create-the-data-file"></a>Per creare il file di dati  
  
1.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.  
  
2.  Nel **modelli** riquadro, selezionare **File XML**.  
  
3.  Denominare il file **Employees**, quindi scegliere il **Add** pulsante.  
  
     Il **Employees** file viene aperto nell'Editor del codice.  
  
4.  Sostituire il contenuto del **Employees** file con il testo seguente.  
  
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
  
5.  Nelle **Esplora soluzioni**, scegliere il **Employees** file.  
  
6.  Nel **delle proprietà** finestra, seleziona la **azione di compilazione** proprietà e quindi modificare il valore in **risorsa incorporata**.  
  
     Questo passaggio incorpora il file XML come risorsa nell'assembly quando si compila il progetto. In questo modo è possibile accedere al contenuto del file XML in fase di esecuzione.  
  
## <a name="create-an-xml-schema"></a>Creare uno Schema XML  
 Se si intende associare un controllo contenuto a un singolo elemento in una parte XML personalizzata, non è necessario usare uno schema XML. Tuttavia, per associare <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a un set di valori, è necessario creare uno schema XML che convalida il file di dati XML creato in precedenza. Lo schema XML definisce i valori possibili per l'elemento `title`. L'associazione di <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a questo elemento viene eseguita più avanti in questa procedura dettagliata.  
  
#### <a name="to-create-an-xml-schema"></a>Per creare uno schema XML  
  
1.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.  
  
2.  Nel **modelli** riquadro, selezionare **XML Schema**.  
  
3.  Assegnare un nome schema **Employees. xsd** e scegliere il **Add** pulsante.  
  
     Viene aperta la progettazione schema.  
  
4.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida **Employees. xsd**, quindi scegliere **Visualizza codice**.  
  
5.  Sostituire il contenuto del **Employees. xsd** file con lo schema seguente.  
  
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
  
6.  Nel **File** dal menu fare clic su **Salva tutto** per salvare le modifiche per il **Employees. XML** e il **Employees. xsd** file.  
  
## <a name="attach-the-xml-schema-to-the-document"></a>Allegare lo schema XML al documento  
 È necessario allegare lo schema XML al documento per associare <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> ai valori validi dell'elemento `title`.  
  
### <a name="to-attach-the-xml-schema-to-the-document-includeword15shortvstoincludesword-15-short-mdmd"></a>Per allegare lo schema XML al documento ([!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)])  
  
1.  Attivare **EmployeeControls. docx** nella finestra di progettazione.  
  
2.  Sulla barra multifunzione scegliere la **sviluppatore** scheda e quindi scegliere il **Add-Ins** pulsante.  
  
3.  Nel **modelli e componenti aggiuntivi** finestra di dialogo scegliere la **XML Schema** scheda e quindi scegliere il **Aggiungi Schema** pulsante.  
  
4.  Selezionare il **Employees. xsd** schema creato in precedenza, che si trova nella directory del progetto e quindi scegliere il **Open** pulsante.  
  
5.  Scegliere il **OK** pulsante il **le impostazioni dello Schema** nella finestra di dialogo.  
  
6.  Scegliere il **OK** per chiudere la **modelli e componenti aggiuntivi** nella finestra di dialogo.  
  
### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>Per allegare lo schema XML al documento (Word 2010)  
  
1.  Attivare **EmployeeControls. docx** nella finestra di progettazione.  
  
2.  Sulla barra multifunzione scegliere la **sviluppatore** scheda.  
  
3.  Nel **XML** gruppo, scegliere il **Schema** pulsante.  
  
4.  Nel **modelli e componenti aggiuntivi** finestra di dialogo scegliere la **XML Schema** scheda e quindi scegliere il **Aggiungi Schema** pulsante.  
  
5.  Selezionare il **Employees. xsd** schema creato in precedenza, a cui si trova nella directory del progetto e scelga il **Open** pulsante.  
  
6.  Scegliere il **OK** pulsante il **le impostazioni dello Schema** nella finestra di dialogo.  
  
7.  Scegliere il **OK** per chiudere la **modelli e componenti aggiuntivi** nella finestra di dialogo.  
  
     Il **struttura XML** Visualizza il riquadro attività.  
  
8.  Chiudi il **struttura XML** riquadro attività.  
  
## <a name="add-a-custom-xml-part-to-the-document"></a>Aggiungere una parte XML personalizzata al documento  
 Prima di poter associare i controlli contenuto a elementi nel file XML, è necessario aggiungere il contenuto del file XML a una nuova parte XML personalizzata nel documento.  
  
### <a name="to-add-a-custom-xml-part-to-the-document"></a>Per aggiungere una parte XML personalizzata al documento  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida **ThisDocument.cs** oppure **ThisDocument. vb**, quindi scegliere **Visualizza codice**.  
  
2.  Aggiungere le seguenti dichiarazioni alla classe `ThisDocument`. Questo codice dichiara diversi oggetti che verranno usati per aggiungere una parte XML personalizzata al documento.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#1)]  
  
3.  Aggiungere il metodo seguente alla classe `ThisDocument` . Questo metodo ottiene il contenuto del file di dati XML incorporato come risorsa nell'assembly e restituisce il contenuto come stringa XML.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#3)]  
  
4.  Aggiungere il metodo seguente alla classe `ThisDocument` . Il metodo crea `AddCustomXmlPart` una nuova parte XML personalizzata che contiene una stringa XML che viene passata al metodo.  
  
     Per garantire che la parte XML personalizzata venga creata solo una volta, il metodo crea la parte XML personalizzata solo se non esiste già nel documento una parte XML personalizzata con GUID corrispondente. La prima volta che viene chiamato questo metodo, viene salvato il valore della proprietà <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> per la stringa `employeeXMLPartID`. Il valore della stringa `employeeXMLPartID` viene mantenuto nel documento perché è stato dichiarato mediante l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#4)]  
  
## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Associare controlli contenuto a elementi nella parte XML personalizzata  
 Associare ogni controllo contenuto a un elemento nella parte XML personalizzata usando il **XMLMapping** proprietà di ogni controllo contenuto.  
  
### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Per associare i controlli contenuto a elementi nella parte XML personalizzata  
  
1.  Aggiungere il metodo seguente alla classe `ThisDocument` . Questo metodo associa ogni controllo del contenuto a un elemento nella parte XML personalizzata e imposta il formato di visualizzazione della data di <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#5)]  
  
## <a name="run-your-code-when-the-document-is-opened"></a>Eseguire il codice quando il documento viene aperto  
 Creare la parte XML personalizzata e associare i controlli personalizzati ai dati quando il documento viene aperto.  
  
### <a name="to-run-your-code-when-the-document-is-opened"></a>Per eseguire il codice quando il documento è aperto  
  
1.  Aggiungere il seguente codice al metodo `ThisDocument_Startup` della classe `ThisDocument`. Questo codice ottiene la stringa XML dal **Employees** file, aggiunge la stringa XML a una nuova parte XML personalizzata nel documento e associa i controlli contenuto agli elementi nella parte XML personalizzata.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#2)]  
  
## <a name="test-the-project"></a>Il progetto di test  
 Quando si apre il documento, i controlli contenuto consentono di visualizzare dati dagli elementi nella parte XML personalizzata. È possibile fare clic il <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> per selezionare uno dei tre valori validi per il `title` elemento, che sono definiti nel **Employees. xsd** file. Se si modificano i dati in uno dei controlli contenuto, i nuovi valori vengono salvati nella parte XML personalizzata del documento.  
  
### <a name="to-test-the-content-controls"></a>Per testare i controlli contenuto  
  
1.  Premere **F5** per eseguire il progetto.  
  
2.  Verificare che la tabella nel documento sia simile alla tabella seguente. Tutte le stringhe della seconda colonna sono ottenute da un elemento nella parte XML personalizzata del documento.  
  
    |||  
    |-|-|  
    |**Nome del dipendente**|**Karina Leal**|  
    |**Data di assunzione**|**1 aprile 1999**|  
    |**Titolo**|**Manager**|  
  
3.  Scegliere la cella a destra del **Employee Name** di cella e digitare un nome diverso.  
  
4.  Scegliere la cella a destra del **Data assunzione** di cella e selezionare una data diversa nella selezione data.  
  
5.  Scegliere la cella a destra del **titolo** di cella e selezionare un nuovo elemento nell'elenco a discesa.  
  
6.  Salvare e chiudere il documento.  
  
7.  In Esplora File, aprire il *\bin\Debug* cartella nel percorso del progetto.  
  
8.  Aprire il menu di scelta rapida **EmployeeControls. docx** e quindi scegliere **rinominare**.  
  
9. Denominare il file **EmployeeControls**.  
  
     Il **EmployeeControls. docx** documento viene salvato in formato Open XML. Rinominando questo documento con il *zip* estensione, è possibile esaminare il contenuto del documento. Per altre informazioni sul formato Open XML, vedere l'articolo tecnico [formati di presentazione di Office (2007) Open XML file](http://msdn.microsoft.com/96018532-f62c-4da7-bbff-16b96a483fbf).  
  
10. Aprire il **EmployeeControls** file.  
  
11. Aprire il **customXml** cartella.  
  
12. Aprire il menu di scelta rapida **item2.xml** e quindi scegliere **Open**.  
  
     Il file contiene la parte XML personalizzata che è stata aggiunta al documento.  
  
13. Verificare che gli elementi `name`, `hireDate` e `title` contengano i nuovi valori immessi nei controlli contenuto nel documento.  
  
14. Chiudi il **item2.xml** file.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Per altre informazioni sull'utilizzo dei controlli contenuto, vedere gli argomenti seguenti:  
  
-   Usare tutti i controlli contenuto disponibili per creare un modello. Per altre informazioni, vedere [procedura dettagliata: creare un modello mediante controlli contenuto](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
-   Modificare i dati nella parte XML personalizzata mentre il documento è chiuso. Alla successiva apertura del documento, i controlli contenuto associati agli elementi XML visualizzeranno i nuovi dati.  
  
-   Usare i controlli contenuto per proteggere parti di un documento. Per altre informazioni, vedere [procedura: proteggere parti di documenti mediante controlli contenuto](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Controlli del contenuto](../vsto/content-controls.md)   
 [Procedura: aggiungere controlli contenuto a documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Procedura: proteggere parti di documenti mediante controlli contenuto](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  