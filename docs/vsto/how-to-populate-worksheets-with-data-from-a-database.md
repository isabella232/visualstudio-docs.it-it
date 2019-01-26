---
title: 'Procedura: Popolare fogli di lavoro con i dati da un database'
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
ms.openlocfilehash: 1169ea54ffbc0d0437204ed4491e2b8cc68a4a04
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865619"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Procedura: Popolare fogli di lavoro con i dati da un database

È possibile accedere ai dati nei progetti di Office a livello di documento nello stesso modo che si accedere ai dati nei progetti Windows Form. Per inserire i dati nella soluzione si possono usare gli stessi strumenti e lo stesso codice e per visualizzarli è possibile persino usare i controlli Windows Form. Inoltre, possono sfruttare i controlli chiamati controlli host, ossia oggetti nativi di Microsoft Office Excel che sono stati migliorati con eventi e funzionalità di associazione dati. Per altre informazioni, vedere [elementi Host e host Cenni preliminari sui controlli](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

Nell'esempio seguente viene mostrato come aggiungere controlli con associazione a dati in progetti a livello di documento mediante una finestra di progettazione. Per un esempio di come aggiungere controlli con associazione a dati nei progetti a livello di applicazione in fase di esecuzione, vedere [procedura dettagliata: Data binding complesso in progetto di componente aggiuntivo VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).

![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [ricerca per categorie Trasferire i dati in un foglio di lavoro di Excel? ](http://go.microsoft.com/fwlink/?LinkID=130277), e [ricerca per categorie Usare i dati di database in Excel? ](http://go.microsoft.com/fwlink/?LinkID=130287).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Aggiungere un controllo con associazione a dati a un foglio di lavoro in fase di progettazione

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Per popolare un foglio di lavoro con i dati da un database

1.  Aprire un progetto a livello di documento di Excel in Visual Studio, aprire il foglio di lavoro nella finestra di progettazione.

2.  Aprire la finestra **Origini dati** e creare un'origine dati per il progetto. Per altre informazioni, vedere [aggiungere le nuove connessioni](../data-tools/add-new-connections.md).

3.  Trascinare il campo o la tabella desiderata dal **Zdroje dat** finestra al foglio di lavoro.

Uno dei seguenti controlli viene creato nel foglio di lavoro:

-   Se si trascina un campo, un <xref:Microsoft.Office.Tools.Excel.NamedRange> nel foglio di lavoro viene creato. Per altre informazioni, vedere [NamedRange control](../vsto/namedrange-control.md).

-   Se si trascina una tabella, una <xref:Microsoft.Office.Tools.Excel.ListObject> nel foglio di lavoro viene creato. Per altre informazioni, vedere [ListObject control](../vsto/listobject-control.md).

È possibile aggiungere un controllo diverso selezionando la tabella o il campo nella **Zdroje dat** finestra e quindi scegliendo un controllo diverso dall'elenco a discesa.

## <a name="objects-in-the-project"></a>Oggetti del progetto

Oltre al controllo, gli oggetti relativi ai dati seguenti vengono aggiunti automaticamente al progetto:

-   Un set di dati tipizzato che incapsula le tabelle dati a cui ci si è connessi nel database. Per altre informazioni, vedere [strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

-   Un oggetto <xref:System.Windows.Forms.BindingSource> che connette il controllo al set di dati tipizzato. Per altre informazioni, vedere [Cenni preliminari sul componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

-   Un oggetto TableAdapter che si connette il set di dati tipizzato al database. Per altre informazioni, vedere [panoramica degli oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

-   Un componente TableAdapterManager, che consente di coordinare gli adattatori di tabella nel set di dati per abilitare gli aggiornamenti gerarchici. Per altre informazioni, vedere [aggiornamento gerarchico](../data-tools/hierarchical-update.md) e [TableAdapterManager riferimento](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Quando si esegue il progetto, il controllo visualizza il primo record dell'origine dati. È possibile usare <xref:System.Windows.Forms.BindingSource> per consentire agli utenti di scorrere i record.

### <a name="to-scroll-through-the-records"></a>Per scorrere i record

-   Usare i metodi <xref:System.Windows.Forms.BindingSource> quali <xref:System.Windows.Forms.BindingSource.MoveNext%2A> e <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Per informazioni su come inviare aggiornamenti al set di dati tipizzato e al database, vedere [come: Aggiornare un'origine dati con dati provenienti da un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Vedere anche

- [Associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Aggiungi nuova origine dati](../data-tools/add-new-data-sources.md)
- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Procedura: Popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Procedura: Popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Procedura: Popolare documenti con dati provenienti da servizi](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Procedura: Aggiornare un'origine dati con dati provenienti da un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Procedura: Trasferire i dati in un foglio di lavoro di Excel](http://go.microsoft.com/fwlink/?LinkID=130277)
- [Procedura: Usare i dati di database in Excel?](http://go.microsoft.com/fwlink/?LinkID=130287)