---
title: 'Procedura: Popolare i fogli di lavoro con i dati di un database'
description: Informazioni su come usare i dati di un oggetto nella soluzione e su come usare i controlli form Windows per visualizzare i dati in un foglio di lavoro.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: cd48feecfd100fc54748511107094bf1351c8c4d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046776"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Procedura: Popolare i fogli di lavoro con i dati di un database

È possibile accedere ai dati nei progetti Office a livello di documento nello stesso modo in cui si accede ai dati nei Windows Form. Per inserire i dati nella soluzione si possono usare gli stessi strumenti e lo stesso codice e per visualizzarli è possibile persino usare i controlli Windows Form. È anche possibile sfruttare i controlli denominati controlli host, ovvero oggetti nativi in Microsoft Office Excel che sono stati migliorati con eventi e funzionalità di data binding. Per altre informazioni, vedere [Panoramica degli elementi host e dei controlli host.](../vsto/host-items-and-host-controls-overview.md)

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

Nell'esempio seguente viene mostrato come aggiungere controlli con associazione a dati in progetti a livello di documento mediante una finestra di progettazione. Per un esempio di come aggiungere controlli associati a dati in progetti a livello di applicazione in fase di esecuzione, vedere [Procedura dettagliata:](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)data binding complessa nel progetto VSTO componente aggiuntivo .

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Aggiungere un controllo con associazione a dati a un foglio di lavoro in fase di progettazione

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Per popolare un foglio di lavoro con i dati di un database

1. Aprire un Excel a livello di documento in Visual Studio, con il foglio di lavoro aperto nella finestra di progettazione.

2. Aprire la finestra **Origini dati** e creare un'origine dati per il progetto. Per altre informazioni, vedere [Aggiungere nuove connessioni.](../data-tools/add-new-connections.md)

3. Trascinare il campo o la tabella desiderata dalla **finestra Origini** dati al foglio di lavoro.

Nel foglio di lavoro viene creato uno dei controlli seguenti:

- Se si trascina un campo, viene <xref:Microsoft.Office.Tools.Excel.NamedRange> creato un controllo nel foglio di lavoro. Per altre informazioni, vedere [Controllo NamedRange.](../vsto/namedrange-control.md)

- Se si trascina una tabella, viene <xref:Microsoft.Office.Tools.Excel.ListObject> creato un controllo nel foglio di lavoro. Per altre informazioni, vedere [Controllo ListObject.](../vsto/listobject-control.md)

È possibile aggiungere un controllo diverso selezionando  la tabella o il campo nella finestra Origini dati e quindi scegliendo un controllo diverso dall'elenco a discesa.

## <a name="objects-in-the-project"></a>Oggetti nel progetto

Oltre al controllo, gli oggetti relativi ai dati seguenti vengono aggiunti automaticamente al progetto:

- Un set di dati tipizzato che incapsula le tabelle dati a cui ci si è connessi nel database. Per altre informazioni, vedere [Strumenti del set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Un oggetto <xref:System.Windows.Forms.BindingSource> che connette il controllo al set di dati tipizzato. Per altre informazioni, vedere [Panoramica del componente BindingSource.](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- TableAdapter che connette il set di dati tipizzato al database. Per altre informazioni, vedere [Cenni preliminari sugli oggetti TableAdapter.](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)

- TableAdapterManager, usato per coordinare gli adattatori di tabella nel set di dati per abilitare gli aggiornamenti gerarchici. Per altre informazioni, vedere [Aggiornamento gerarchico e](../data-tools/hierarchical-update.md) [Informazioni di riferimento su TableAdapterManager.](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference)

Quando si esegue il progetto, il controllo visualizza il primo record dell'origine dati. È possibile usare <xref:System.Windows.Forms.BindingSource> per consentire agli utenti di scorrere i record.

### <a name="to-scroll-through-the-records"></a>Per scorrere i record

- Usare i metodi <xref:System.Windows.Forms.BindingSource> quali <xref:System.Windows.Forms.BindingSource.MoveNext%2A> e <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Per informazioni su come inviare aggiornamenti al set di dati tipizzato e al database, vedere Procedura: Aggiornare un'origine dati con dati [da un controllo host.](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)

## <a name="see-also"></a>Vedi anche

- [Associare dati a controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Aggiungere nuove origini dati](../data-tools/add-new-data-sources.md)
- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Procedura: Popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Procedura: Popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Procedura: Popolare documenti con i dati dei servizi](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Procedura: Aggiornare un'origine dati con i dati di un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)