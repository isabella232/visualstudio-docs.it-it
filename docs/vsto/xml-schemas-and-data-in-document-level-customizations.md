---
title: Xml Schema e dati nelle personalizzazioni a livello di documento
description: Microsoft Excel e Word offrono la possibilità di eseguire il mapping degli schemi ai documenti e possono semplificare l'importazione e l'esportazione di dati XML da e verso il documento.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3944655cd84f1034e2c3850514d45fdccf27a1ec
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710583"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>Xml Schema e dati nelle personalizzazioni a livello di documento
  **Importante** Le informazioni contenute in questo argomento relative a Microsoft Word vengono presentate esclusivamente a vantaggio e all'uso di singoli utenti e organizzazioni che si trovano all'esterno del Stati Uniti e dei relativi territori o che usano o sviluppano programmi eseguiti su prodotti Microsoft Word concessi in licenza da Microsoft prima del gennaio 2010, quando Microsoft ha rimosso un'implementazione di particolari funzionalità correlate al codice XML personalizzato da Microsoft Word. Queste informazioni relative Microsoft Word non possono essere lette o usate da singoli utenti o organizzazioni nel Stati Uniti o nei relativi territori che usano o sviluppano programmi eseguiti su prodotti Microsoft Word concessi in licenza da Microsoft dopo il 10 gennaio 2010; Tali prodotti non si comporteranno come i prodotti concessi in licenza prima di tale data o acquistati e concessi in licenza per l'uso al di fuori del Stati Uniti.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Microsoft Office Excel e Microsoft Office Word offrono la possibilità di eseguire il mapping degli schemi ai documenti. Questa funzionalità può semplificare l'importazione e l'esportazione di dati XML all'inizio e all'uscita dal documento.

 Visual Studio espone gli elementi dello schema mappato nelle personalizzazioni a livello di documento come controlli nel modello di programmazione. Ad Excel, Visual Studio il supporto per l'associazione dei controlli ai dati in database, servizi Web e oggetti. Per Word e Excel, Visual Studio aggiunge il supporto per i riquadri azioni, che possono essere usati con un documento mappato a schema per creare un'esperienza utente finale avanzata per le soluzioni. Per altre informazioni, vedere Panoramica [del riquadro Azioni.](../vsto/actions-pane-overview.md)

> [!NOTE]
> Non è possibile usare XML Schema multipart in Excel soluzioni.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Oggetti creati quando gli schemi vengono collegati a Excel cartelle di lavoro
 Quando si collega uno schema a una cartella di lavoro, Visual Studio automaticamente diversi oggetti e li aggiunge al progetto. Questi oggetti non devono essere eliminati usando Visual Studio, perché sono gestiti da Excel. Per eliminarli, rimuovere gli elementi mappati dal foglio di lavoro o scollegare lo schema usando gli Excel seguenti.

 Esistono due oggetti principali:

- XML Schema (file XSD). Per ogni schema nella cartella di lavoro, Visual Studio aggiunge uno schema al progetto. Viene visualizzato come elemento di progetto con un'estensione XSD in **Esplora soluzioni**.

- Una classe <xref:System.Data.DataSet> tipizzata. Questa classe viene creata in base allo schema. Questa classe del set di dati è **visibile in Visualizzazione classi**.

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Oggetti creati quando viene eseguito il mapping degli elementi dello schema Excel fogli di lavoro
 Quando si esegue il mapping di un elemento dello schema dal riquadro attività Origine **XML** a un foglio di lavoro, Visual Studio crea automaticamente diversi oggetti e li aggiunge al progetto:

- Controlli. Per ogni oggetto mappato nella cartella di lavoro, viene creato un controllo (per gli elementi dello schema non ripetuti) o un controllo (per gli elementi dello schema ripetuti) nel <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> modello di programmazione. Il <xref:Microsoft.Office.Tools.Excel.ListObject> controllo può essere eliminato solo eliminando i mapping e gli oggetti mappati dalla cartella di lavoro. Per altre informazioni sui controlli, vedere [Cenni preliminari sugli elementi host e sui controlli host.](../vsto/host-items-and-host-controls-overview.md)

- Bindingsource. Quando si crea un oggetto tramite il mapping di un elemento dello schema non ripetuto al foglio di lavoro, viene creato un oggetto e il controllo viene <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:System.Windows.Forms.BindingSource> associato a <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:System.Windows.Forms.BindingSource> . È necessario associare a un'istanza dell'origine dati che corrisponde allo schema mappato al documento, ad esempio un'istanza della classe <xref:System.Windows.Forms.BindingSource> tipiata <xref:System.Data.DataSet> creata. Creare l'associazione impostando <xref:System.Windows.Forms.BindingSource.DataSource%2A> le <xref:System.Windows.Forms.BindingSource.DataMember%2A> proprietà e esposte nella **finestra** Proprietà.

    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource>L'oggetto non viene creato per gli oggetti <xref:Microsoft.Office.Tools.Excel.ListObject> . È necessario associare manualmente <xref:Microsoft.Office.Tools.Excel.ListObject> all'origine dati impostando le <xref:System.Windows.Forms.BindingSource.DataSource%2A> proprietà e nella <xref:System.Windows.Forms.BindingSource.DataMember%2A> **finestra** Proprietà.

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office gli schemi mappati e la Visual Studio origini dati
 Sia la funzionalità dello schema mappato di Office  che la finestra Origini dati Visual Studio consentono di presentare i dati in un foglio di lavoro di Excel per la creazione di report o la modifica. In entrambi i casi è possibile trascinare gli elementi dati nel foglio Excel foglio di lavoro. Entrambi i metodi creano controlli associati a dati tramite a <xref:System.Windows.Forms.BindingSource> un'origine dati, ad esempio <xref:System.Data.DataSet> o un servizio Web.

> [!NOTE]
> Quando si esegue il mapping di un elemento dello schema ripetuto a un foglio di lavoro, Visual Studio crea un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> . <xref:Microsoft.Office.Tools.Excel.ListObject>L'oggetto non viene associato automaticamente ai dati tramite <xref:System.Windows.Forms.BindingSource> . È necessario associare manualmente <xref:Microsoft.Office.Tools.Excel.ListObject> all'origine dati impostando le <xref:System.Windows.Forms.BindingSource.DataSource%2A> proprietà e nella <xref:System.Windows.Forms.BindingSource.DataMember%2A> **finestra** Proprietà.

 La tabella seguente illustra alcune delle differenze tra i due metodi.

|XML Schema|Finestra Origini dati|
|----------------|-------------------------|
|Usa Office inter interface.|Usa **la finestra Origini** dati in Visual Studio.|
|Abilita le funzionalità Office per l'importazione e l'esportazione di dati da file XML.|È necessario fornire funzionalità di importazione ed esportazione a livello di codice.|
|È necessario scrivere codice per riempire i controlli generati con dati.|I controlli aggiunti dalla **finestra Origini dati generano** automaticamente codice per riempirli, insieme alle stringhe di connessione necessarie quando si usano i server di database.|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Comportamento quando gli schemi sono collegati a documenti di Word
 Gli oggetti dati non vengono creati quando si collega uno schema a un documento di Word utilizzato in un progetto Office documento. Tuttavia, quando si esegue il mapping di un elemento dello schema al documento, i controlli vengono creati. Il tipo di controllo dipende dal tipo di elemento di cui si esegue il mapping. Gli elementi ripetuti <xref:Microsoft.Office.Tools.Word.XMLNodes> generano controlli e gli elementi non ripetuti <xref:Microsoft.Office.Tools.Word.XMLNode> generano controlli. Per altre informazioni, vedere [Controllo XMLNodes e](../vsto/xmlnodes-control.md) [Controllo XMLNode.](../vsto/xmlnode-control.md)

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Distribuzione di soluzioni che includono XML Schema
 È necessario creare un programma di installazione per distribuire una soluzione che utilizza uno schema XML mappato a un documento. Il programma di installazione deve registrare lo schema nella libreria di schemi nel computer dell'utente. Se non si registra lo schema, la soluzione continuerà a funzionare perché Word genera uno schema temporaneo basato sugli elementi presenti nel documento quando l'utente lo apre. Tuttavia, l'utente non sarà in grado di eseguire la convalida o salvare lo schema usato per creare il progetto. Per altre informazioni sui programmi di installazione, vedere [Distribuire applicazioni, servizi e componenti.](../deployment/deploying-applications-services-and-components.md)

 È anche possibile aggiungere codice al progetto per verificare se lo schema è nella libreria e registrato. In caso contrario, è possibile avvisare l'utente.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs" id="Snippet1":::

## <a name="see-also"></a>Vedi anche

- [Procedura: Eseguire il mapping di schemi a documenti di Word all'interno Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Procedura: Eseguire il mapping degli schemi ai fogli di lavoro all'interno Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
