---
title: 'Procedura: popolare fogli di dati da un database'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0a1e01f5c9fc1372cda4d7d31f8ba56b90e166e7
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985852"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Procedura: popolare fogli di dati da un database

È possibile accedere ai dati nei progetti di Office a livello di documento nello stesso modo in cui si accede ai dati nei progetti Windows Forms. Per inserire i dati nella soluzione si possono usare gli stessi strumenti e lo stesso codice e per visualizzarli è possibile persino usare i controlli Windows Form. Inoltre, è possibile sfruttare i controlli denominati controlli host, ovvero oggetti nativi in Microsoft Office Excel che sono stati migliorati con eventi e funzionalità di data binding. Per altre informazioni, vedere [Cenni preliminari sugli elementi host e sui controlli host](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

Nell'esempio seguente viene mostrato come aggiungere controlli con associazione a dati in progetti a livello di documento mediante una finestra di progettazione. Per un esempio di come aggiungere controlli con associazione a dati nei progetti a livello di applicazione in fase di esecuzione, vedere [procedura dettagliata: data binding complessi in un progetto di componente aggiuntivo VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Aggiungere un controllo con associazione a dati a un foglio di esecuzione in fase di progettazione

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Per popolare un foglio di dati con i dati di un database

1. Aprire un progetto a livello di documento di Excel in Visual Studio, con il foglio di lavoro aperto nella finestra di progettazione.

2. Aprire la finestra **Origini dati** e creare un'origine dati per il progetto. Per altre informazioni, vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).

3. Trascinare il campo o la tabella desiderato dalla finestra **origini dati** al foglio di lavoro.

Uno dei seguenti controlli viene creato nel foglio di controllo:

- Se si trascina un campo, nel foglio di <xref:Microsoft.Office.Tools.Excel.NamedRange> viene creato un controllo. Per ulteriori informazioni, vedere [controllo NamedRange](../vsto/namedrange-control.md).

- Se si trascina una tabella, nel foglio di <xref:Microsoft.Office.Tools.Excel.ListObject> viene creato un controllo. Per ulteriori informazioni, vedere [controllo ListObject](../vsto/listobject-control.md).

È possibile aggiungere un controllo diverso selezionando la tabella o il campo nella finestra **origini dati** e scegliendo un controllo diverso dall'elenco a discesa.

## <a name="objects-in-the-project"></a>Oggetti nel progetto

Oltre al controllo, gli oggetti relativi ai dati seguenti vengono aggiunti automaticamente al progetto:

- Un set di dati tipizzato che incapsula le tabelle dati a cui ci si è connessi nel database. Per altre informazioni, vedere [DataSet Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Un oggetto <xref:System.Windows.Forms.BindingSource> che connette il controllo al set di dati tipizzato. Per altre informazioni, vedere [Cenni preliminari sul componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- Oggetto TableAdapter che connette il set di dati tipizzato al database. Per altre informazioni, vedere [Panoramica di TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

- TableAdapterManager, utilizzato per coordinare gli adattatori di tabella nel set di dati per consentire gli aggiornamenti gerarchici. Per ulteriori informazioni, vedere l' [aggiornamento gerarchico](../data-tools/hierarchical-update.md) e [riferimento a TableAdapterManager](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Quando si esegue il progetto, il controllo visualizza il primo record dell'origine dati. È possibile usare <xref:System.Windows.Forms.BindingSource> per consentire agli utenti di scorrere i record.

### <a name="to-scroll-through-the-records"></a>Per scorrere i record

- Usare i metodi <xref:System.Windows.Forms.BindingSource> quali <xref:System.Windows.Forms.BindingSource.MoveNext%2A> e <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Per informazioni su come inviare aggiornamenti al DataSet tipizzato e al database, vedere [procedura: aggiornare un'origine dati con dati da un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Vedere anche

- [Associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Aggiungi nuova origine dati](../data-tools/add-new-data-sources.md)
- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Procedura: popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Procedura: popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Procedura: popolare documenti con dati da servizi](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Procedura: aggiornare un'origine dati con i dati di un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)