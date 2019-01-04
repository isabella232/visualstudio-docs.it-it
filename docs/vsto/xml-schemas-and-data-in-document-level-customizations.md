---
title: XML schema e dati nelle personalizzazioni a livello di documento
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dd9f91b8b0fbf786bc06687df14dfe29d579610a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966758"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>XML schema e dati nelle personalizzazioni a livello di documento
  **Importante** le informazioni definite in questo argomento relative a Microsoft Word sono presentati in modo esclusivo per il vantaggio e uso di singoli utenti e le organizzazioni che si trovano di fuori degli Stati Uniti e dei relativi territori o che usano o lo sviluppo i programmi eseguiti su, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft prima di gennaio del 2010 quando Microsoft ha rimosso un'implementazione di una funzionalità specifica correlato a XML personalizzata da Microsoft Word. Queste informazioni relative a Microsoft Word non possono essere lette o utilizzate dagli singoli individui o organizzazioni negli Stati Uniti o relativo territori che usano o lo sviluppo di programmi in esecuzione in, i prodotti di Microsoft Word che sono stati concessi in licenza da Microsoft dopo il 10 gennaio 2010 ; tali prodotti non si comporterà come prodotti concessi in licenza prima di tale data o acquistati e concesso in licenza per l'utilizzo di fuori degli Stati Uniti.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Microsoft Office Excel e Microsoft Office Word offrono la possibilità di eseguire il mapping di schemi ai documenti. Questa funzionalità può semplificare l'importazione ed esportazione dei dati XML da e verso il documento.

 Visual Studio vengono esposti eseguito il mapping di elementi dello schema nelle personalizzazioni a livello di documento come controlli nel modello di programmazione. Per Excel, Visual Studio aggiunge il supporto per l'associazione di controlli ai dati nel database, servizi Web e oggetti. Per Word ed Excel, Visual Studio aggiunge il supporto per i riquadri azioni, che consente a un documento il mapping dello schema per creare un'esperienza avanzata agli utenti finali per le soluzioni. Per altre informazioni, vedere [Cenni preliminari sul riquadro azioni](../vsto/actions-pane-overview.md).

> [!NOTE]
>  È possibile usare gli schemi XML in più parti nelle soluzioni Excel.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Oggetti creati quando gli schemi collegati a cartelle di lavoro di Excel
 Quando si allega uno schema in una cartella di lavoro, Visual Studio automaticamente crea diversi oggetti e li aggiunge al progetto. Questi oggetti non devono essere eliminati usando strumenti di Visual Studio, perché vengono gestite da Excel. Per eliminarle, rimuovere gli elementi mappati dal foglio di lavoro o scollegare dello schema utilizzando gli strumenti di Excel.

 Sono presenti due oggetti principali:

-   Schema XML (file XSD). Per ogni schema nella cartella di lavoro, Visual Studio aggiunge uno schema al progetto. Questa opzione corrisponde a un elemento del progetto con estensione XSD nella **Esplora soluzioni**.

-   Una classe <xref:System.Data.DataSet> tipizzata. Questa classe viene creata sulla base dello schema. Questa classe di set di dati è visibile nella **Visualizzazione classi**.

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Oggetti creati quando vengono eseguito il mapping di elementi dello schema a fogli di lavoro di Excel
 Quando si esegue il mapping di un elemento dello schema dal **origine XML** riquadro attività a un foglio di lavoro, Visual Studio automaticamente crea diversi oggetti e le aggiunge al progetto:

-   Controlli. Per ogni oggetto con mapping nella cartella di lavoro, un' <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo (per gli elementi dello schema non ripetuto) o un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo (per la ripetizione di elementi dello schema) viene creata nel modello di programmazione. Il <xref:Microsoft.Office.Tools.Excel.ListObject> controllo può essere eliminato solo eliminando i mapping e gli oggetti con mapping dalla cartella di lavoro. Per altre informazioni sui controlli, vedere [elementi Host e host Cenni preliminari sui controlli](../vsto/host-items-and-host-controls-overview.md).

-   BindingSource. Quando si crea un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> eseguendo il mapping di un elemento dello schema non ripetuto nel foglio di lavoro, un <xref:System.Windows.Forms.BindingSource> viene creato e il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> è associato ai <xref:System.Windows.Forms.BindingSource>. È necessario associare il <xref:System.Windows.Forms.BindingSource> a un'istanza dell'origine dati che corrispondono allo schema mappato al documento, ad esempio un'istanza dell'oggetto tipizzato <xref:System.Data.DataSet> classe creata. Creare il binding impostando il <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> le proprietà, che vengono esposte nel **proprietà** finestra.

    > [!NOTE]
    >  Il <xref:System.Windows.Forms.BindingSource> non viene creato per <xref:Microsoft.Office.Tools.Excel.ListObject> oggetti. È necessario associare manualmente il <xref:Microsoft.Office.Tools.Excel.ListObject> all'origine dei dati impostando il <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> delle proprietà nel **proprietà** finestra.

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office eseguito il mapping degli schemi e nella finestra Origini dati di Visual Studio
 Entrambe le funzionalità con mapping dello schema di Office e Visual Studio **Zdroje dat** finestra può aiutarti a presentare i dati in un foglio di lavoro di Excel per la creazione di report o la modifica. In entrambi i casi è possibile trascinare gli elementi di dati del foglio di lavoro di Excel. Entrambi i metodi di creano controlli che sono associati a dati mediante un <xref:System.Windows.Forms.BindingSource> a un'origine dati, ad esempio un <xref:System.Data.DataSet> o un servizio web.

> [!NOTE]
>  Quando si esegue il mapping di un elemento ripetuto dello schema a un foglio di lavoro, Visual Studio crea un <xref:Microsoft.Office.Tools.Excel.ListObject>. Il <xref:Microsoft.Office.Tools.Excel.ListObject> non viene automaticamente associato ai dati tramite il <xref:System.Windows.Forms.BindingSource>. È necessario associare manualmente il <xref:Microsoft.Office.Tools.Excel.ListObject> all'origine dei dati impostando il <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> delle proprietà nel **proprietà** finestra.

 Nella tabella seguente vengono illustrate alcune delle differenze tra i due metodi.

|Schema XML|Finestra Origini dati|
|----------------|-------------------------|
|Usa l'interfaccia di Office.|Viene utilizzato **Zdroje dat** finestra in Visual Studio.|
|Abilita le funzionalità di Office predefinite per l'importazione ed esportazione dei dati dai file XML.|È necessario consentire l'importazione e la funzionalità di esportazione a livello di codice.|
|È necessario scrivere codice per inserire i controlli generati con i dati.|I controlli aggiunti dal **Zdroje dat** finestra dispone di codice generato automaticamente per il riempimento, insieme a stringhe di connessione necessarie quando si usano server di database.|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Comportamento quando gli schemi sono collegati ai documenti di Word
 Gli oggetti dati non vengono creati quando si allega uno schema a un documento di Word che viene usato in un progetto di Office a livello di documento. Tuttavia, quando si esegue il mapping di un elemento dello schema al documento, vengono creati i controlli. Il tipo di controllo varia in base al tipo di elemento di cui si esegue il mapping; gli elementi ripetitivi generano <xref:Microsoft.Office.Tools.Word.XMLNodes> controlli e gli elementi non ripetuto generare <xref:Microsoft.Office.Tools.Word.XMLNode> controlli. Per altre informazioni, vedere [controllo XMLNodes](../vsto/xmlnodes-control.md) e [controllo XMLNode](../vsto/xmlnode-control.md).

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Distribuzione di soluzioni che includono gli schemi XML
 È consigliabile creare un programma di installazione per distribuire una soluzione che usa uno schema XML che viene eseguito il mapping a un documento. Il programma di installazione deve registrare lo schema nella raccolta dello schema nel computer dell'utente. Se non si registrano lo schema, la soluzione continuerà a funzionare poiché Word consente di generare uno schema temporaneo basato sugli elementi presenti nel documento quando l'utente apre. Tuttavia, l'utente non sarà in grado di eseguire la convalida o salvare lo schema utilizzato per creare il progetto. Per altre informazioni sui programmi di installazione, vedere [distribuire applicazioni, servizi e componenti](../deployment/deploying-applications-services-and-components.md).

 È anche possibile aggiungere codice al progetto per verificare se lo schema nella raccolta e registrato. In caso contrario, è possibile avvisare l'utente.

 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]

## <a name="see-also"></a>Vedere anche

- [Procedura: Mappare schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Procedura: Mappare schemi a fogli di lavoro in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
