---
title: XML Schema e dati nelle personalizzazioni a livello di documento
description: Microsoft Excel e Word offrono la possibilità di eseguire il mapping degli schemi ai documenti e possono semplificare l'importazione e l'esportazione di dati XML all'interno e all'esterno del documento.
ms.custom: SEO-VS-2020
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ece2c06e9432ca24b4a5773c9938aeec61df0270
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894413"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>XML Schema e dati nelle personalizzazioni a livello di documento
  **Importante** Le informazioni contenute in questo argomento riguardanti Microsoft Word sono presentate esclusivamente per il vantaggio e l'utilizzo di singoli utenti e organizzazioni che si trovano al di fuori del Stati Uniti e dei suoi territori o che utilizzano o sviluppano programmi eseguiti in Microsoft Word, che sono stati concessi in licenza da Microsoft prima del gennaio 2010, quando Microsoft ha rimosso un'implementazione di particolari funzionalità correlate a XML personalizzato da Microsoft Word. Queste informazioni relative a Microsoft Word non possono essere lette o usate da singoli utenti o organizzazioni nel Stati Uniti o nei suoi territori che usano o sviluppano programmi eseguiti in Microsoft Word prodotti concessi in licenza da Microsoft dopo il 10 gennaio 2010; tali prodotti non si comporteranno come prodotti concessi in licenza prima di tale data o acquistati e concessi in licenza per l'utilizzo al di fuori del Stati Uniti.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Microsoft Office Excel e Microsoft Office Word offrono la possibilità di eseguire il mapping degli schemi ai documenti. Questa funzionalità consente di semplificare l'importazione e l'esportazione di dati XML all'interno e all'esterno del documento.

 Visual Studio espone gli elementi dello schema mappati nelle personalizzazioni a livello di documento come controlli nel modello di programmazione. Per Excel, Visual Studio aggiunge il supporto per l'associazione dei controlli ai dati in database, servizi Web e oggetti. Per Word ed Excel, Visual Studio aggiunge il supporto per i riquadri azioni, che possono essere utilizzati con un documento mappato allo schema per creare un'esperienza utente finale avanzata per le soluzioni. Per altre informazioni, vedere [Cenni preliminari sul riquadro azioni](../vsto/actions-pane-overview.md).

> [!NOTE]
> Non è possibile utilizzare schemi XML multipart in soluzioni Excel.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Oggetti creati quando gli schemi sono collegati a cartelle di lavoro di Excel
 Quando si collega uno schema a una cartella di lavoro, Visual Studio crea automaticamente diversi oggetti e li aggiunge al progetto. Questi oggetti non devono essere eliminati utilizzando gli strumenti di Visual Studio, perché sono gestiti da Excel. Per eliminarle, rimuovere gli elementi mappati dal foglio di lavoro o scollegarlo tramite strumenti di Excel.

 Sono presenti due oggetti principali:

- XML Schema (file XSD). Per ogni schema nella cartella di lavoro, Visual Studio aggiunge uno schema al progetto. Viene visualizzato come elemento di progetto con un'estensione XSD in **Esplora soluzioni**.

- Una classe <xref:System.Data.DataSet> tipizzata. Questa classe viene creata in base allo schema. Questa classe DataSet è visibile in **Visualizzazione classi**.

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Oggetti creati quando viene eseguito il mapping degli elementi dello schema ai fogli di lavoro di Excel
 Quando si esegue il mapping di un elemento dello schema dal riquadro attività **origine XML** a un foglio di lavoro, Visual Studio crea automaticamente diversi oggetti e li aggiunge al progetto:

- Controlli. Per ogni oggetto mappato nella cartella di lavoro, <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> nel modello di programmazione viene creato un controllo (per gli elementi dello schema non ripetuti) o un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo (per gli elementi dello schema ripetuti). Il <xref:Microsoft.Office.Tools.Excel.ListObject> controllo può essere eliminato solo eliminando i mapping e gli oggetti di cui è stato eseguito il mapping dalla cartella di lavoro. Per ulteriori informazioni sui controlli, vedere [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md).

- BindingSource. Quando si crea un oggetto <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> eseguendo il mapping di un elemento dello schema non ripetuto al foglio di <xref:System.Windows.Forms.BindingSource> controllo, viene creato un oggetto e il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo viene associato a <xref:System.Windows.Forms.BindingSource> . È necessario associare <xref:System.Windows.Forms.BindingSource> a un'istanza dell'origine dati corrispondente allo schema mappato al documento, ad esempio un'istanza della classe tipizzata <xref:System.Data.DataSet> creata. Per creare l'associazione, impostare <xref:System.Windows.Forms.BindingSource.DataSource%2A> le <xref:System.Windows.Forms.BindingSource.DataMember%2A> proprietà e, che vengono esposte nella finestra **proprietà** .

    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource>Non viene creato per <xref:Microsoft.Office.Tools.Excel.ListObject> gli oggetti. È necessario associare manualmente l'oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> all'origine dati impostando le <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> proprietà e nella finestra **Proprietà** .

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Schemi con mapping di Office e finestra Origini dati di Visual Studio
 Sia la funzionalità dello schema mappata di Office che la finestra **origini dati** di Visual Studio consentono di presentare i dati in un foglio di lavoro di Excel per la creazione di report o la modifica. In entrambi i casi è possibile trascinare gli elementi dati nel foglio di lavoro di Excel. Entrambi i metodi consentono di creare controlli associati a dati tramite un oggetto <xref:System.Windows.Forms.BindingSource> a un'origine dati, ad esempio <xref:System.Data.DataSet> o un servizio Web.

> [!NOTE]
> Quando si esegue il mapping di un elemento dello schema ripetuto a un foglio di foglio, Visual Studio crea un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> . <xref:Microsoft.Office.Tools.Excel.ListObject>Non viene associato automaticamente ai dati tramite <xref:System.Windows.Forms.BindingSource> . È necessario associare manualmente l'oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> all'origine dati impostando le <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> proprietà e nella finestra **Proprietà** .

 Nella tabella seguente vengono illustrate alcune delle differenze tra i due metodi.

|XML Schema|Finestra Origini dati|
|----------------|-------------------------|
|Usa l'interfaccia di Office.|Usa la finestra **origini dati** in Visual Studio.|
|Abilita le funzionalità predefinite di Office per l'importazione e l'esportazione di dati da file XML.|È necessario fornire la funzionalità di importazione ed esportazione a livello di codice.|
|È necessario scrivere il codice per riempire i controlli generati con i dati.|I controlli aggiunti dalla finestra **origini dati** hanno codice generato automaticamente per riempirli, insieme alle stringhe di connessione necessarie quando si usano i server di database.|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Comportamento quando gli schemi sono allegati ai documenti di Word
 Gli oggetti dati non vengono creati quando si connette uno schema a un documento di Word utilizzato in un progetto di Office a livello di documento. Tuttavia, quando si esegue il mapping di un elemento dello schema al documento, vengono creati i controlli. Il tipo di controllo dipende dal tipo di elemento mappato; gli elementi ripetuti generano <xref:Microsoft.Office.Tools.Word.XMLNodes> controlli e gli elementi non ripetuti generano <xref:Microsoft.Office.Tools.Word.XMLNode> controlli. Per altre informazioni, vedere [controllo XMLNodes](../vsto/xmlnodes-control.md) e [controllo XMLNode](../vsto/xmlnode-control.md).

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Distribuzione di soluzioni che includono XML Schema
 È necessario creare un programma di installazione per distribuire una soluzione che utilizza un XML Schema mappato a un documento. Il programma di installazione deve registrare lo schema nella libreria dello schema nel computer dell'utente. Se lo schema non viene registrato, la soluzione continuerà a funzionare perché Word genera uno schema temporaneo basato sugli elementi presenti nel documento quando viene aperto dall'utente. Tuttavia, l'utente non sarà in grado di eseguire la convalida o di salvare lo schema utilizzato per creare il progetto. Per ulteriori informazioni sui programmi di installazione, vedere la pagina relativa alla [distribuzione di applicazioni, servizi e componenti](../deployment/deploying-applications-services-and-components.md).

 È anche possibile aggiungere codice al progetto per verificare se lo schema si trova nella libreria e registrato. In caso contrario, è possibile avvisare l'utente.

 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]

## <a name="see-also"></a>Vedi anche

- [Procedura: eseguire il mapping degli schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Procedura: eseguire il mapping di schemi a fogli di fogli di Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
