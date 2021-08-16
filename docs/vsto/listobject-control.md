---
title: ListObject (controllo)
description: Il controllo ListObject è un elenco che espone eventi e può essere associato ai dati. È anche possibile aggiungere controlli ListObject a un foglio di lavoro in fase di progettazione o di esecuzione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.List
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- lists, events
- ListObject control
- ListObject control, events
- ListObject control, data binding
- ListObject control, improving performance when bound to data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 555cb96deb97b08068ca1b9634ee1770d0f340f021e3e9e29f09ec8150a09eaf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408149"
---
# <a name="listobject-control"></a>ListObject (controllo)
  Il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> è un elenco che espone gli eventi e può essere associato a dati. Quando si aggiunge un elenco a un foglio di lavoro, Visual Studio crea un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> su cui è possibile programmare direttamente senza dover passare attraverso il modello a oggetti di Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Creare il controllo
 Nei progetti a livello di documento è possibile aggiungere i controlli <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di lavoro in fase di progettazione o di esecuzione. Nei progetti di componente aggiuntivo VSTO è possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.ListObject> ai fogli di lavoro aperti solo in fase di esecuzione. Per altre informazioni, vedere [Procedura: Aggiungere controlli ListObject ai fogli di lavoro.](../vsto/how-to-add-listobject-controls-to-worksheets.md)

> [!NOTE]
> Per impostazione predefinita, gli oggetti elenco creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host quando il foglio di lavoro è chiuso. Per altre informazioni, vedere [Aggiungere controlli a Office documenti in fase di esecuzione.](../vsto/adding-controls-to-office-documents-at-run-time.md)

## <a name="bind-data-to-the-control"></a>Associare dati al controllo
 Un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> supporta un data binding semplice e complesso. Il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> può essere associato a un'origine dati usando le proprietà <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> e <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> in fase di progettazione o il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> in fase di esecuzione.

> [!NOTE]
> L'oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> viene aggiornato automaticamente quando è associato a un'origine dati, ad esempio un <xref:System.Data.DataTable>, che genera eventi quando i dati vengono modificati. Se si associa l'oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> a un'origine dati che non genera eventi quando i dati vengono modificati, è necessario chiamare il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> o <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> per aggiornare l'oggetto <xref:Microsoft.Office.Tools.Excel.ListObject>.

 Quando si aggiunge un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> a una cella di un foglio di lavoro mappando un elemento ripetuto dello schema a tale cella, Visual Studio mappa automaticamente l'oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> al set di dati generato. L'oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> , invece, non viene associato automaticamente ai dati. L'oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> può essere associato al set di dati in fase di programmazione o in fase di esecuzione in un progetto a livello di documento. È possibile associare a livello di codice al set di dati <xref:Microsoft.Office.Tools.Excel.ListObject> in fase di esecuzione in VSTO componente aggiuntivo.

 Poiché i dati sono separati rispetto all'oggetto <xref:Microsoft.Office.Tools.Excel.ListObject>, è necessario aggiungere e rimuovere dati tramite il set di dati associato e non direttamente tramite <xref:Microsoft.Office.Tools.Excel.ListObject>. Se i dati nel set di dati associato vengono aggiornati con qualsiasi meccanismo, il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> rispecchia automaticamente le modifiche. Per altre informazioni, vedere [Associare dati ai controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md).

 È possibile riempire rapidamente un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> associando <xref:Microsoft.Office.Tools.Excel.ListObject> a un'origine dati. Se si modificano i dati in un controllo <xref:Microsoft.Office.Tools.Excel.ListObject>associato a dati, le modifiche vengono apportate automaticamente anche all'origine dati. Se si vuole riempire un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> e quindi consentire all'utente di modificare i dati in <xref:Microsoft.Office.Tools.Excel.ListObject> senza modificare l'origine dati, è possibile usare il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> per scollegare <xref:Microsoft.Office.Tools.Excel.ListObject> dall'origine dati. Per altre informazioni, vedere [Procedura: Compilare controlli ListObject con dati.](../vsto/how-to-fill-listobject-controls-with-data.md)

> [!NOTE]
> Il data binding non è supportato nei controlli <xref:Microsoft.Office.Tools.Excel.ListObject> sovrapposti.

### <a name="improve-performance-in-listobject-controls"></a>Migliorare le prestazioni nei controlli ListObject
 La lettura di un file XML in un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> associato a dati tende a essere lenta se si associa prima il controllo e quindi si chiama <xref:System.Data.DataSet.ReadXml%2A> per riempire il set di dati. Per migliorare le prestazioni, chiamare <xref:System.Data.DataSet.ReadXml%2A> prima di associare il controllo.

### <a name="disconnect-listobject-controls-from-the-data-source"></a>Disconnettere i controlli ListObject dall'origine dati
 Dopo aver riempito un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> con dati associandolo a un'origine dati, è possibile disconnetterlo affinché le modifiche apportate ai dati nell'oggetto elenco non influiscano sull'origine dati. Per altre informazioni, vedere [Procedura: Compilare controlli ListObject con dati.](../vsto/how-to-fill-listobject-controls-with-data.md)

### <a name="restore-column-and-row-order"></a>Ripristinare l'ordine di colonne e righe
 Quando si associano dati a un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> che è stato aggiunto a un documento in fase di progettazione, Visual Studio tiene traccia dell'ordine delle righe e delle colonne ogni volta che la cartella di lavoro viene salvata. Se un utente sposta le righe o le colonne di <xref:Microsoft.Office.Tools.Excel.ListObject> in fase di esecuzione, il nuovo ordine verrà conservato alla successiva apertura della cartella di lavoro e il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> verrà associato nuovamente all'origine dati.

 Se si vuole ripristinare l'ordine delle righe e colonne originale per l'oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> , è possibile chiamare il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> . Questo metodo rimuove le proprietà personalizzate dei documenti correlate all'ordine delle righe e colonne dell'oggetto <xref:Microsoft.Office.Tools.Excel.ListObject>specificato. Chiamare questo metodo dall'evento <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> della cartella di lavoro se non si vuole mantenere l'ordine delle righe e colonne di <xref:Microsoft.Office.Tools.Excel.ListObject>.

## <a name="format"></a>Formato
 La formattazione applicabile a <xref:Microsoft.Office.Interop.Excel.ListObject> può essere applicata anche a un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> . Questo include i bordi, i tipi di carattere, il formato numero e gli stili. Gli utenti finali possono ridisporre le colonne in un oggetto associato a dati e queste modifiche verranno rese persistenti con il documento, a condizione che sia stato aggiunto al documento <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject> in fase di progettazione. Alla successiva che apertura del documento, l'oggetto elenco verrà associato alla stessa origine dati, ma l'ordine delle colonne rifletterà le modifiche apportate dagli utenti.

## <a name="add-and-remove-columns-at-run-time"></a>Aggiungere e rimuovere colonne in fase di esecuzione
 Non è possibile aggiungere o rimuovere colonne manualmente in un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> associato a dati in fase di esecuzione. Se un utente finale tenta di eliminare una colonna, verrà ripristinata immediatamente e tutte le colonne aggiunte verranno rimosse. È quindi importante scrivere codice per spiegare agli utenti perché non possono eseguire queste azioni su un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> associato a dati. Visual Studio fornisce diversi eventi su un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> correlati al data binding. Ad esempio, si può usare l'evento <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> per avvertire gli utenti che i dati che hanno tentato di eliminare non possono essere eliminati e sono stati ripristinati.

## <a name="add-and-remove-rows-at-run-time"></a>Aggiungere e rimuovere righe in fase di esecuzione
 È possibile aggiungere e rimuovere righe manualmente in un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> associato a dati, purché l'origine dati consenta di aggiungere nuove righe e non sia di sola lettura. È possibile scrivere codice per eventi come <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> per convalidare i dati. Per altre informazioni, vedere [Procedura: Convalidare i dati quando viene aggiunta](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)una nuova riga a un controllo ListObject.

 In alcuni casi la relazione tra l'oggetto elenco e l'origine dati provoca errori di routine. Ad esempio, è possibile mappare le colonne da visualizzare in <xref:Microsoft.Office.Tools.Excel.ListObject>, quindi se si omettono le colonne con restrizioni, ad esempio un campo che non accetta valori null, vengono generati errori ogni volta che viene creata una riga. È possibile scrivere codice per aggiungere i valori mancanti in un gestore eventi per l'evento <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> .

## <a name="rename-listobject-controls-in-excel"></a>Rinominare i controlli ListObject in Excel
 Excel consente agli utenti di modificare il nome Excel tabelle in fase di esecuzione usando la **scheda** Progettazione . Tuttavia, il <xref:Microsoft.Office.Tools.Excel.ListObject> controllo non supporta questa funzionalità. Se un utente tenta di rinominare una tabella di Excel che corrisponde a un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject>, quando viene salvata la cartella di lavoro viene ripristinato automaticamente il nome originale della tabella di Excel.

## <a name="events"></a>Eventi
 Gli eventi seguenti sono disponibili per il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> :

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Change>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>

- <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>

- <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>

- <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>

## <a name="see-also"></a>Vedi anche
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Procedura: Aggiungere controlli ListObject ai fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Procedura: Ridimensionare i controlli ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Procedura: Convalidare i dati quando viene aggiunta una nuova riga a un controllo ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Procedura: Eseguire il mapping di colonne ListObject ai dati](../vsto/how-to-map-listobject-columns-to-data.md)
- [Procedura: Compilare controlli ListObject con dati](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Office e procedure dettagliate per lo sviluppo di applicazioni](../vsto/office-development-samples-and-walkthroughs.md)
- [Associare dati a controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Estendere documenti di Word Excel cartelle di lavoro VSTO componenti aggiuntivi in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli su Office documenti](../vsto/controls-on-office-documents.md)
- [Aggiungere controlli ai Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Procedura: Popolare i fogli di lavoro con i dati di un database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
