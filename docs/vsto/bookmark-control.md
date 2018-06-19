---
title: Bookmark (controllo)
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 60ab9db37f3ed41de4afcdecbf2c9e83ffb5c2f6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264012"
---
# <a name="bookmark-control"></a>Bookmark (controllo)
  Il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> è un segnalibro con un nome univoco che espone gli eventi e può essere associato ai dati. Può essere usato come segnaposto per contrassegnare un elemento o una posizione in un documento di Microsoft Office Word. Il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> è una combinazione degli oggetti <xref:Microsoft.Office.Interop.Word.Bookmark> e <xref:Microsoft.Office.Interop.Word.Range> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Nei progetti a livello di documento, è possibile aggiungere <xref:Microsoft.Office.Tools.Word.Bookmark> controlli al documento in fase di progettazione o in fase di esecuzione. Nei progetti di componente aggiuntivo VSTO, è possibile aggiungere <xref:Microsoft.Office.Tools.Word.Bookmark> controlli a qualsiasi documento aperto in fase di esecuzione. Per altre informazioni, vedere [procedura: Aggiungi controllo Bookmark controlli ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

## <a name="bind-data-to-the-control"></a>Associare dati al controllo
 Un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> supporta un data binding semplice. Il segnalibro deve essere associato a un'origine dati usando la proprietà <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> . La proprietà di data binding predefinita del segnalibro è <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> .

 Se i dati in set di dati associato vengono aggiornati, il <xref:Microsoft.Office.Tools.Word.Bookmark> Mostra le modifiche del controllo.

 Nei progetti a livello di documento è anche possibile associare i dati ai segnalibri usando la finestra **Origini dati** . Per altre informazioni, vedere [procedura: popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md).

## <a name="formatting"></a>Formattazione
 La formattazione applicabile a <xref:Microsoft.Office.Interop.Word.Bookmark> può essere applicata anche a un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> . Questo include i tipi di carattere, rientri, spaziatura, numerazione e stili.

## <a name="assign-text-to-the-bookmark"></a>Assegna un testo al segnalibro
 Un'altra differenza tra un <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> oggetto e un <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> controllo riguarda il comportamento tenuto quando viene assegnato il testo al segnalibro. Se si assegna testo a lunghezza zero <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>, il testo viene aggiunto a destra del segnalibro e il segnalibro resta di lunghezza zero. Tuttavia, se si assegna testo a lunghezza zero <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>, il testo viene inserito nel segnalibro e la lunghezza del segnalibro aumenta per il numero totale di caratteri inseriti.

 Il <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> controllo dispone anche di <xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType> proprietà. Questa proprietà è diversa dal <xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType> proprietà che è disponibile nel <xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType> proprietà di un <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> (controllo), o il <xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType> proprietà di un <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> oggetto.

|Proprietà Text|Descrizione|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|Usare questa proprietà per visualizzare un testo nel segnalibro e lasciare il segnalibro nel documento. L'assegnazione di un testo al segnalibro espande l'intervallo del segnalibro senza eliminarlo.<br /><br /> Ad esempio, `Bookmark1.Text = "Hello world"` inserisce il testo nel segnalibro e lascia intatto il segnalibro.|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|Usare questa proprietà per visualizzare il testo in corrispondenza del segnalibro ed eliminare automaticamente il segnalibro. Ad esempio, `Bookmark1.Range.Text = "Hello world"` inserisce il testo nel segnalibro ed elimina il segnalibro.|

## <a name="rename-the-control-at-design-time"></a>Rinomina il controllo in fase di progettazione
 Nei progetti a livello di documento, quando si trascina un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> dalla **casella degli strumenti** al documento, Visual Studio genera automaticamente un nome per il controllo, che può essere modificato nella finestra **Proprietà** .

## <a name="overlapping-controls"></a>Sovrapposizione di controlli
 Controlli Bookmark possono sovrapporsi. Lo stesso testo può essere condiviso da più segnalibri. Quando si assegna il nuovo testo a uno dei segnalibri sovrapposti, contiene solo il nuovo testo e i segnalibri non si sovrappongono più. L'altro segnalibro conterrà solo il testo non è stato condiviso tra i segnalibri precedentemente sovrapposti.

 La tabella seguente mostra in che modo la frase "This is sample text." è condiviso da due segnalibri sovrapposti:

|Segnalibro|Testo|
|--------------|----------|
|Segnalibri sovrapposti|[this is {sample] text.}|
|Segnalibro1|This is sample|
|Segnalibro2|sample text.|

 Se si assegna il nuovo testo "This is replacement." al segnalibro1, i segnalibri non si sovrappongano e segnalibro2 visualizzerà solo il testo che originariamente non fa parte del segnalibro1.

|Segnalibro|Testo|
|--------------|----------|
|Due segnalibri separati|[this is replacement]{ text.}|
|Segnalibro1|This is replacement|
|Segnalibro2|text.|

Se si modifica il testo di un segnalibro che contiene un altro segnalibro, il segnalibro interno non verrà eliminato. Tuttavia, il segnalibro interno diventa un segnalibro vuoto e sposta alla fine del segnalibro esterno.

La tabella seguente mostra in che modo la frase "This is sample text." è condiviso da un segnalibro a cui è contenuto all'interno di un altro segnalibro:

|Segnalibro|Testo|
|--------------|----------|
|Segnalibri sovrapposti|[this is {sample} text.]|
|Segnalibro1|This is sample text.|
|Segnalibro2|esempio|

 Se si assegna il nuovo testo "This is replacement." al Segnalibro1, i segnalibri non sono più sovrapposti e il Segnalibro2 diventa un segnalibro vuoto posizionato alla fine del Segnalibro1.

|Segnalibro|Testo|
|--------------|----------|
|Due segnalibri separati|[è sostituzione].{}|
|Segnalibro1|This is replacement.|
|Segnalibro2|*\<vuota >*|

## <a name="events"></a>Eventi

Gli eventi seguenti sono disponibili per il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> :

-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>

-   <xref:System.ComponentModel.IComponent.Disposed>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>

## <a name="see-also"></a>Vedere anche

- [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Procedura: aggiungere controlli segnalibro ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Procedura dettagliata: Creare menu di scelta rapida per segnalibri](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Associare dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)