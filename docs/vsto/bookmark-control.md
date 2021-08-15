---
title: Bookmark (controllo)
description: Informazioni su come il controllo Bookmark è un segnalibro con un nome univoco, espone eventi e può essere associato ai dati.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: faaeae36f5c9e4ff658e79656cff0af6823d5be81673250f1b95452fdb117687
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121286175"
---
# <a name="bookmark-control"></a>Bookmark (controllo)
  Il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> è un segnalibro con un nome univoco che espone gli eventi e può essere associato ai dati. Può essere usato come segnaposto per contrassegnare un elemento o una posizione in un documento di Microsoft Office Word. Il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> è una combinazione degli oggetti <xref:Microsoft.Office.Interop.Word.Bookmark> e <xref:Microsoft.Office.Interop.Word.Range> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Nei progetti a livello di documento è possibile aggiungere i controlli <xref:Microsoft.Office.Tools.Word.Bookmark> al documento in fase di progettazione o di esecuzione. Nei progetti di componente aggiuntivo VSTO è possibile aggiungere i controlli <xref:Microsoft.Office.Tools.Word.Bookmark> a qualsiasi documento aperto in fase di esecuzione. Per altre informazioni, vedere [Procedura: Aggiungere controlli Segnalibro ai documenti di Word.](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

## <a name="bind-data-to-the-control"></a>Associare dati al controllo
 Un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> supporta un data binding semplice. Il segnalibro deve essere associato a un'origine dati usando la proprietà <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> . La proprietà di data binding predefinita del segnalibro è <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> .

 Se i dati nel set di dati associato vengono aggiornati, il <xref:Microsoft.Office.Tools.Word.Bookmark> controllo visualizza le modifiche.

 Nei progetti a livello di documento è anche possibile associare i dati ai segnalibri usando la finestra **Origini dati** . Per altre informazioni, vedere [Procedura: Popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md).

## <a name="formatting"></a>Formattazione
 La formattazione applicabile a <xref:Microsoft.Office.Interop.Word.Bookmark> può essere applicata anche a un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> . Questa formattazione include tipi di carattere, rientri, spaziatura, numerazione e stili.

## <a name="assign-text-to-the-bookmark"></a>Assegnare testo al segnalibro
 Un'altra differenza tra un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> e un controllo <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> riguarda il comportamento tenuto quando viene assegnato un testo al segnalibro. Se si assegna un testo a un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>di lunghezza zero, il testo viene aggiunto alla destra del segnalibro e il segnalibro resta di lunghezza zero. Tuttavia, se si assegna un testo a un controllo <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>di lunghezza zero, il testo viene inserito nel segnalibro e la lunghezza del segnalibro aumenta per il numero totale di caratteri inseriti.

 Il controllo <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> ha anche la proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType> , Questa proprietà è diversa dalla proprietà disponibile nella proprietà di un controllo o <xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType> nella proprietà di un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType> <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> <xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType> <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> .

|Proprietà Text|Descrizione|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|Usare questa proprietà per visualizzare un testo nel segnalibro e lasciare il segnalibro nel documento. L'assegnazione di un testo al segnalibro espande l'intervallo del segnalibro senza eliminarlo.<br /><br /> Ad esempio, `Bookmark1.Text = "Hello world"` inserisce il testo nel segnalibro e lascia intatto il segnalibro.|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|Usare questa proprietà per visualizzare il testo in corrispondenza del segnalibro ed eliminare automaticamente il segnalibro. Ad esempio, `Bookmark1.Range.Text = "Hello world"` inserisce il testo nel segnalibro ed elimina il segnalibro.|

## <a name="rename-the-control-at-design-time"></a>Rinominare il controllo in fase di progettazione
 Nei progetti a livello di documento, quando si trascina un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> dalla **casella degli strumenti** al documento, Visual Studio genera automaticamente un nome per il controllo, che può essere modificato nella finestra **Proprietà** .

## <a name="overlapping-controls"></a>Controlli sovrapposti
 I controlli segnalibro possono sovrapporsi tra loro. Lo stesso testo può essere condiviso da più segnalibri. Quando si assegna un nuovo testo a uno dei segnalibri sovrapposti, contiene solo il nuovo testo e i segnalibri non si sovrappongono più. L'altro segnalibro ora contiene solo il testo che non è stato condiviso tra i segnalibri sovrapposti originali.

 La tabella seguente mostra in che modo la frase "This is sample text." è condiviso da due segnalibri sovrapposti:

|Segnalibro|Testo|
|--------------|----------|
|Segnalibri sovrapposti|[this is {sample] text.}|
|Segnalibro1|This is sample|
|Segnalibro2|sample text.|

 Se si assegna il nuovo testo "This is replacement." in Bookmark1, i segnalibri non si sovrappongono e Bookmark2 mantiene solo il testo che non era originariamente parte di Bookmark1.

|Segnalibro|Testo|
|--------------|----------|
|Due segnalibri separati|[this is replacement]{ text.}|
|Segnalibro1|This is replacement|
|Segnalibro2|text.|

Se si modifica il testo di un segnalibro che contiene un altro segnalibro, il segnalibro interno non viene eliminato. Tuttavia, il segnalibro interno diventa un segnalibro vuoto e si sposta alla fine del segnalibro esterno.

La tabella seguente mostra in che modo la frase "This is sample text." è condiviso da un segnalibro contenuto in un altro segnalibro:

|Segnalibro|Testo|
|--------------|----------|
|Segnalibri sovrapposti|[this is {sample} text.]|
|Segnalibro1|This is sample text.|
|Segnalibro2|sample|

 Se si assegna il nuovo testo "This is replacement." al Segnalibro1, i segnalibri non sono più sovrapposti e il Segnalibro2 diventa un segnalibro vuoto posizionato alla fine del Segnalibro1.

|Segnalibro|Testo|
|--------------|----------|
|Due segnalibri separati|[questa è la sostituzione.]{}|
|Segnalibro1|This is replacement.|
|Segnalibro2|*\<empty>*|

## <a name="events"></a>Eventi

Gli eventi seguenti sono disponibili per il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> :

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>

- <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>

## <a name="see-also"></a>Vedi anche

- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Procedura: Aggiungere controlli Bookmark ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Procedura dettagliata: Creare menu di scelta rapida per i segnalibri](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Associare dati ai controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)