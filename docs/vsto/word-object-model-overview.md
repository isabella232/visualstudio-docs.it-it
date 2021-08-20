---
title: Panoramica del modello a oggetti di Word
description: Il modello a oggetti di Word è costituito da classi e interfacce fornite nell'assembly di interoperabilità primario per Word e definite nello spazio dei nomi di Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word object model
- Word [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Word
- objects [Office development in Visual Studio], Office object models
- Office object models
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 919253f271da3c8f7d486ea9bfd8706c2bd66c71
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068465"
---
# <a name="word-object-model-overview"></a>Panoramica del modello a oggetti di Word
  Quando si sviluppano soluzioni Word in Visual Studio, si interagisce con il modello a oggetti di Word. Questo modello a oggetti è costituito da classi e interfacce fornite nell'assembly di interoperabilità primario per Word ed è definito nello spazio dei nomi <xref:Microsoft.Office.Interop.Word> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 In questo argomento viene fornita una breve panoramica del modello a oggetti di Word. Per le risorse in cui è possibile ottenere altre informazioni sull'intero modello a oggetti di Word, vedere la documentazione relativa all'uso del [modello a oggetti di Word.](#WordOMDocumentation)

 Per informazioni sull'uso del modello a oggetti di Word per eseguire attività specifiche, vedere gli argomenti seguenti:

- [Usare i documenti](../vsto/working-with-documents.md)

- [Usare il testo nei documenti](../vsto/working-with-text-in-documents.md)

- [Utilizzare le tabelle](../vsto/working-with-tables.md)

## <a name="understand-the-word-object-model"></a><a name="understanding"></a> Informazioni sul modello a oggetti di Word
 In Word sono disponibili centinaia di oggetti con cui interagire. Questi oggetti sono organizzati in una gerarchia che corrisponde strettamente all'interfaccia utente. All'inizio della gerarchia vi è l'oggetto <xref:Microsoft.Office.Interop.Word.Application> . Questo oggetto rappresenta l'istanza corrente di Word. L'oggetto <xref:Microsoft.Office.Interop.Word.Application> contiene gli oggetti <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, <xref:Microsoft.Office.Interop.Word.Bookmark>e <xref:Microsoft.Office.Interop.Word.Range> . Ciascuno di questi oggetti dispone di numerosi metodi e proprietà che è possibile modificare e usare con l'oggetto.

 La figura seguente mostra una visualizzazione di questi oggetti nella gerarchia del modello a oggetti di Word.

 ![Rappresentazione grafica del modello a oggetti di Word](../vsto/media/wrwordobjectmodel.gif "Rappresentazione grafica del modello a oggetti di Word")

 A prima vista, gli oggetti sembrano essere sovrapposti. Ad esempio, gli oggetti <xref:Microsoft.Office.Interop.Word.Document> e <xref:Microsoft.Office.Interop.Word.Selection> sono entrambi membri dell'oggetto <xref:Microsoft.Office.Interop.Word.Application> , ma l'oggetto <xref:Microsoft.Office.Interop.Word.Document> è anche membro dell'oggetto <xref:Microsoft.Office.Interop.Word.Selection> . Entrambi gli oggetti <xref:Microsoft.Office.Interop.Word.Document> e <xref:Microsoft.Office.Interop.Word.Selection> contengono oggetti <xref:Microsoft.Office.Interop.Word.Bookmark> e <xref:Microsoft.Office.Interop.Word.Range> . La sovrapposizione esiste in quanto sono disponibili diversi modi per accedere allo stesso tipo di oggetto. Ad esempio, si applica la formattazione a un oggetto <xref:Microsoft.Office.Interop.Word.Range> , ma è possibile accedere all'intervallo della selezione corrente, di un particolare paragrafo, di una sezione o dell'intero documento.

 Le sezioni riportate di seguito forniscono una breve descrizione degli oggetti di livello superiore e della loro reciproca interazione. Tali oggetti comprendono i cinque seguenti:

- Oggetto applicazione

- Oggetto Document

- Oggetto Selection

- Oggetto Range

- Oggetto Bookmark

  Oltre al modello a oggetti di Word, i progetti di Office in Visual Studio forniscono *elementi host* e *controlli host* che estendono alcuni oggetti nel modello a oggetti di Word. Gli elementi e i controlli host si comportano come gli oggetti di Word che vengono estesi, ma dispongono anche di funzionalità aggiuntive, ad esempio funzionalità di data binding ed eventi aggiuntivi. Per altre informazioni, vedere [Automatizzare Word usando oggetti](../vsto/automating-word-by-using-extended-objects.md) estesi ed [Elementi host e cenni preliminari sui controlli host](../vsto/host-items-and-host-controls-overview.md).

### <a name="application-object"></a>Oggetto applicazione
 L'oggetto <xref:Microsoft.Office.Interop.Word.Application> rappresenta l'applicazione Word e costituisce l'elemento padre di tutti gli altri oggetti. I membri vengono in genere applicati a Word nel suo complesso. È possibile usare le proprietà e i metodi di questo oggetto per controllare l'ambiente Word.

 Nei progetti di componente aggiuntivo VSTO è possibile accedere all'oggetto <xref:Microsoft.Office.Interop.Word.Application> usando il campo `Application` della classe `ThisAddIn` . Per altre informazioni, vedere [Programmi VSTO componenti aggiuntivi](../vsto/programming-vsto-add-ins.md).

 Nei progetti a livello di documento è possibile accedere all'oggetto <xref:Microsoft.Office.Interop.Word.Application> usando la proprietà <xref:Microsoft.Office.Tools.Word.Document.Application%2A> della classe `ThisDocument` .

### <a name="document-object"></a>Oggetto Document
 L'oggetto <xref:Microsoft.Office.Interop.Word.Document> svolge un ruolo centrale nell'ambito della programmazione di Word. Rappresenta un documento e tutto il relativo contenuto. Quando si apre un documento o se ne crea uno nuovo, viene creato un nuovo oggetto <xref:Microsoft.Office.Interop.Word.Document> , che viene aggiunto alla raccolta <xref:Microsoft.Office.Interop.Word.Documents> dell'oggetto <xref:Microsoft.Office.Interop.Word.Application> . Il documento con lo stato attivo è definito documento attivo. È rappresentato dalla proprietà <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Application> .

 Gli strumenti di sviluppo di Office in Visual Studio estendono l'oggetto <xref:Microsoft.Office.Interop.Word.Document> fornendo il tipo <xref:Microsoft.Office.Tools.Word.Document> . Questo tipo è un *elemento host* che consente di accedere a tutte le funzionalità di un oggetto <xref:Microsoft.Office.Interop.Word.Document> , che aggiunge eventi aggiuntivi e che offre la possibilità di aggiungere controlli gestiti.

 Quando si crea un progetto a livello di documento, è possibile accedere ai membri <xref:Microsoft.Office.Tools.Word.Document> tramite la classe `ThisDocument` generata nel progetto. È possibile accedere ai membri dell'elemento host <xref:Microsoft.Office.Tools.Word.Document> usando le parole chiave **Me** o **this** del codice della classe `ThisDocument` oppure usando l'oggetto `Globals.ThisDocument` del codice esterno alla classe `ThisDocument` . Per altre informazioni, vedere [Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md). Ad esempio, per selezionare il primo paragrafo del documento, usare il codice seguente.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet120":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet120":::

 Nei progetti di componente aggiuntivo VSTO è possibile generare elementi host <xref:Microsoft.Office.Tools.Word.Document> in fase di esecuzione. È possibile usare l'elemento host generato per aggiungere controlli al documento associato. Per altre informazioni, vedere Estendere documenti di Word Excel cartelle di lavoro in VSTO [componenti aggiuntivi in fase di esecuzione.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

### <a name="selection-object"></a>Oggetto Selection
 L'oggetto <xref:Microsoft.Office.Interop.Word.Selection> rappresenta l'area attualmente selezionata. Quando si esegue un'operazione nell'interfaccia utente di Word, ad esempio l'applicazione di grassetto a un testo, si seleziona o si evidenzia il testo e quindi si applica la formattazione. L'oggetto <xref:Microsoft.Office.Interop.Word.Selection> è sempre presente in un documento. Se non è selezionato alcun elemento, rappresenta il punto di inserimento. Inoltre, una selezione può includere più blocchi di testo non contigui.

### <a name="range-object"></a>Oggetto Range
 L'oggetto <xref:Microsoft.Office.Interop.Word.Range> rappresenta un'area contigua in un documento e viene definito mediante una posizione di carattere iniziale e una posizione di carattere finale. Non sono presenti limiti che impongono l'uso di un singolo oggetto <xref:Microsoft.Office.Interop.Word.Range> . È possibile definire più oggetti <xref:Microsoft.Office.Interop.Word.Range> nello stesso documento. Un oggetto <xref:Microsoft.Office.Interop.Word.Range> presenta le caratteristiche seguenti:

- Può essere costituito dal solo punto di inserimento, da un intervallo di testo o dall'intero documento.

- Comprende caratteri non stampabili come spazi, caratteri di tabulazione e segni di paragrafo.

- Può essere l'area rappresentata dalla selezione corrente o può rappresentare un'area diversa dalla selezione corrente.

- Non è visibile in un documento, a differenza di una selezione, che è sempre visibile.

- Non viene salvato con un documento ed è disponibile solo durante l'esecuzione del codice.

  In caso di inserimento di testo alla fine dell'intervallo, in Word l'intervallo viene automaticamente espanso in modo da includere il testo inserito.

### <a name="content-control-objects"></a>Oggetti controllo contenuto
 Un oggetto <xref:Microsoft.Office.Interop.Word.ContentControl> rappresenta un modo per controllare l'input e la presentazione del testo nonché di altri tipi di contenuto nei documenti di Word. Un oggetto <xref:Microsoft.Office.Interop.Word.ContentControl> può visualizzare vari tipi diversi di interfaccia utente ottimizzati per l'uso nei documenti di Word, ad esempio un controllo RTF, una selezione data o una casella combinata. Inoltre è possibile usare un oggetto <xref:Microsoft.Office.Interop.Word.ContentControl> per impedire agli utenti di modificare le sezioni del documento o del modello.

 Visual Studio estende l'oggetto <xref:Microsoft.Office.Interop.Word.ContentControl> in numerosi controlli host diversi. Mentre l'oggetto <xref:Microsoft.Office.Interop.Word.ContentControl> è in grado di visualizzare uno qualsiasi dei vari tipi di interfaccia utente disponibili per i controlli del contenuto, in Visual Studio è disponibile un tipo diverso per ogni controllo del contenuto. È ad esempio possibile usare un oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> per creare un controllo RTF o un oggetto <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> per creare una selezione data. Questi controlli host funzionano come oggetti <xref:Microsoft.Office.Interop.Word.ContentControl>nativi, ma sono dotati di eventi e funzionalità di data binding aggiuntive. Per altre informazioni, vedere [Controlli contenuto](../vsto/content-controls.md).

### <a name="bookmark-object"></a>Oggetto Bookmark
 L'oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> rappresenta un'area contigua in un documento, con una posizione di carattere iniziale e una posizione di carattere finale. I segnalibri possono essere usati per contrassegnare una posizione in un documento o come contenitori di testo in un documento. Un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> può essere costituito dal punto di inserimento o avere le stesse dimensioni dell'intero documento. Un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> presenta le seguenti caratteristiche distintive rispetto all'oggetto <xref:Microsoft.Office.Interop.Word.Range> :

- È possibile assegnare un nome al segnalibro in fase di progettazione.

- Gli oggetti<xref:Microsoft.Office.Interop.Word.Bookmark> vengono salvati con il documento, pertanto non vengono eliminati al termine dell'esecuzione del codice o dopo la chiusura del documento.

- È possibile nascondere o rendere visibili i segnalibri impostando la proprietà <xref:Microsoft.Office.Interop.Word.View.ShowBookmarks%2A> della classe <xref:Microsoft.Office.Interop.Word.View> su **false** o **true**.

  In Visual Studio l'oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> viene esteso fornendo il controllo host <xref:Microsoft.Office.Tools.Word.Bookmark> . Il controllo host <xref:Microsoft.Office.Tools.Word.Bookmark> si comporta come un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark>nativo, ma dispone di ulteriori eventi e funzionalità di data binding. È possibile associare dati a un controllo Bookmark contenuto in un documento nello stesso modo in cui si associano dati a un controllo casella di testo di un Windows Form. Per altre informazioni, vedere [Controllo Bookmark](../vsto/bookmark-control.md).

## <a name="use-the-word-object-model-documentation"></a><a name="WordOMDocumentation"></a> Usare la documentazione del modello a oggetti di Word
 Per informazioni complete sul modello a oggetti di Word, è possibile usare il riferimento dell'assembly di interoperabilità primario (PIA) di Word e il riferimento del modello a oggetti Visual Basic, Applications Edition (VBA).

### <a name="primary-interop-assembly-reference"></a>Informazioni di riferimento sull'assembly di interoperabilità primario
 Nella documentazione di riferimento dell'assembly di interoperabilità primario dell'assembly di interoperabilità primario (PIA) di Word vengono descritti i tipi dell'assembly di interoperabilità primario per Word. Questa documentazione è disponibile nel percorso seguente: Riferimento all'assembly di interoperabilità primario di [Word 2010.](../vsto/office-primary-interop-assemblies.md)

 [Per altre](/previous-versions/office/office-12/ms247299(v=office.12))informazioni sulla progettazione dell'assembly di interoperabilità primario di Word, ad esempio sulle differenze tra classi e interfacce nell'assembly di interoperabilità primario e sulla modalità di implementazione degli eventi nell'assembly di interoperabilità primario, vedere Panoramica delle classi e delle interfacce negli assembly di interoperabilità primari di Office .

### <a name="vba-object-model-reference"></a>Informazioni di riferimento sul modello a oggetti VBA
 Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di Word esposto al codice VBA. Per altre informazioni, vedere Riferimento al modello a oggetti di [Word 2010.](/office/vba/api/overview/Word/object-model)

 Tutti gli oggetti e i membri nel riferimento del modello a oggetti VBA corrispondono a tipi e membri nell'assembly di interoperabilità primario (PIA) di Word. Ad esempio, l'oggetto Document nel riferimento al modello a oggetti VBA corrisponde <xref:Microsoft.Office.Interop.Word.Document> all'oggetto nell'assembly di interoperabilità principale di Word. Sebbene il riferimento del modello a oggetti VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA di questo riferimento per Visual Basic o Visual C# se si vuole usarlo in un progetto di Word che è possibile creare tramite Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Office assembly di interoperabilità primari](../vsto/office-primary-interop-assemblies.md)
- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Usare i documenti](../vsto/working-with-documents.md)
- [Usare il testo nei documenti](../vsto/working-with-text-in-documents.md)
- [Utilizzare le tabelle](../vsto/working-with-tables.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
