---
title: 'Procedura: Popolare documenti con dati da un database'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 27dc08cc5d63368cecaa54ce59ed6831e7647240
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883999"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Procedura: Popolare documenti con dati da un database

È possibile accedere ai dati dei progetti a livello di documento per Microsoft Office con la stessa procedura usata per accedere ai dati dei progetti Windows Form. Per inserire dati da un database nella soluzione si usano infatti gli stessi strumenti e lo stesso codice e per visualizzare i dati è possibile usare i controlli Windows Form.

Inoltre, è possibile visualizzare i dati tramite i controlli host. I controlli host sono oggetti nativi di Microsoft Office Word che sono stati migliorati con eventi e funzionalità di data binding. Per altre informazioni, vedere [elementi Host e host Cenni preliminari sui controlli](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

Nell'esempio seguente viene mostrato come aggiungere controlli con associazione a dati in progetti a livello di documento mediante una finestra di progettazione. Per un esempio di come aggiungere controlli con associazione a dati nei progetti di componente aggiuntivo VSTO in fase di esecuzione, vedere [procedura dettagliata: Data binding semplice in progetto di componente aggiuntivo VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [associare dati al contenuto di Word 2007 consente di controllare utilizzando Visual Studio Tools per Office system (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785).

## <a name="add-a-control-to-a-document-at-design-time"></a>Aggiungere un controllo a un documento in fase di progettazione

### <a name="to-populate-a-document-with-data-from-a-database"></a>Per popolare un documento con dati da un database

1.  Aprire un progetto a livello di documento Word in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], con il documento aperto nella finestra di progettazione.

2.  Aprire il **Zdroje dat** finestra e creare un'origine dati da un database. Per altre informazioni, vedere [aggiungere le nuove connessioni](../data-tools/add-new-connections.md).

3.  Trascinare il campo desiderato dal **Zdroje dat** finestra al documento.

Al documento viene aggiunto un controllo contenuto. Il tipo di controllo contenuto dipende dal tipo di dati del campo selezionato. Per altre informazioni, vedere [dei controlli contenuto](../vsto/content-controls.md).

È possibile aggiungere un controllo diverso selezionando il campo dati nel **Zdroje dat** finestra e quindi scegliendo un controllo diverso dall'elenco a discesa.

## <a name="objects-in-the-project"></a>Oggetti del progetto

Oltre al controllo, gli oggetti relativi ai dati seguenti vengono aggiunti automaticamente al progetto:

-   Un set di dati tipizzato che incapsula le tabelle dati a cui ci si è connessi nel database. Per altre informazioni, vedere [strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

-   Un oggetto <xref:System.Windows.Forms.BindingSource> che connette il controllo al set di dati tipizzato. Per altre informazioni, vedere [Cenni preliminari sul componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

-   Un oggetto TableAdapter che si connette il set di dati tipizzato al database. Per altre informazioni, vedere [creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).

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
- [Procedura: Aggiornare un'origine dati con dati provenienti da un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Usare i file di database locale in panoramica di soluzioni Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Cenni preliminari sul componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)