---
title: 'Procedura: Popolare documenti con dati da un database'
description: Informazioni su come usare i dati di un database nella soluzione e su come usare i controlli form Windows per visualizzare i dati in un documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a2c49f7f40d7b73ed0db14e227ac97f8aacc7fca
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148207"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Procedura: Popolare documenti con dati da un database

È possibile accedere ai dati dei progetti a livello di documento per Microsoft Office con la stessa procedura usata per accedere ai dati dei progetti Windows Form. Per inserire dati da un database nella soluzione si usano infatti gli stessi strumenti e lo stesso codice e per visualizzare i dati è possibile usare i controlli Windows Form.

Inoltre, è possibile visualizzare i dati tramite i controlli host. I controlli host sono oggetti nativi di Microsoft Office Word che sono stati migliorati con eventi e funzionalità di data binding. Per altre informazioni, vedere [Panoramica di elementi host e controlli host](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

Nell'esempio seguente viene mostrato come aggiungere controlli con associazione a dati in progetti a livello di documento mediante una finestra di progettazione. Per un esempio di come aggiungere controlli associati VSTO dati VSTO progetti di componente aggiuntivo in fase di esecuzione, vedere [Procedura dettagliata:](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)data binding semplice nel VSTO progetto di componente aggiuntivo .

![collegamento al video](../vsto/media/playvideo.gif "Collegamento a video") Per una dimostrazione video correlata, vedere Associare dati ai controlli contenuto di [Word 2007 usando Strumenti di Visual Studio per il sistema Office (3.0).](/previous-versions/office/developer/office-2007/bb967663(v=office.12))

## <a name="add-a-control-to-a-document-at-design-time"></a>Aggiungere un controllo a un documento in fase di progettazione

### <a name="to-populate-a-document-with-data-from-a-database"></a>Per popolare un documento con dati da un database

1. Aprire un progetto a livello di documento Word in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], con il documento aperto nella finestra di progettazione.

2. Aprire la **finestra Origini dati** e creare un'origine dati da un database. Per altre informazioni, vedere [Aggiungere nuove connessioni.](../data-tools/add-new-connections.md)

3. Trascinare il campo desiderato dalla **finestra Origini** dati al documento.

Al documento viene aggiunto un controllo contenuto. Il tipo di controllo contenuto dipende dal tipo di dati del campo selezionato. Per altre informazioni, vedere [Controlli contenuto](../vsto/content-controls.md).

È possibile aggiungere un controllo diverso selezionando  il campo dati nella finestra Origini dati e quindi scegliendo un controllo diverso dall'elenco a discesa.

## <a name="objects-in-the-project"></a>Oggetti nel progetto

Oltre al controllo, gli oggetti relativi ai dati seguenti vengono aggiunti automaticamente al progetto:

- Un set di dati tipizzato che incapsula le tabelle dati a cui ci si è connessi nel database. Per altre informazioni, vedere [Strumenti del set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Un oggetto <xref:System.Windows.Forms.BindingSource> che connette il controllo al set di dati tipizzato. Per altre informazioni, vedere [Panoramica del componente BindingSource.](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- TableAdapter che connette il set di dati tipizzato al database. Per altre informazioni, vedere [Creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).

- TableAdapterManager, usato per coordinare gli adattatori di tabella nel set di dati per abilitare gli aggiornamenti gerarchici. Per altre informazioni, vedere [Aggiornamento gerarchico e](../data-tools/hierarchical-update.md) [Riferimento a TableAdapterManager](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Quando si esegue il progetto, il controllo visualizza il primo record dell'origine dati. È possibile usare <xref:System.Windows.Forms.BindingSource> per consentire agli utenti di scorrere i record.

### <a name="to-scroll-through-the-records"></a>Per scorrere i record

- Usare i metodi <xref:System.Windows.Forms.BindingSource> quali <xref:System.Windows.Forms.BindingSource.MoveNext%2A> e <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Per informazioni su come inviare aggiornamenti al set di dati tipizzato e al database, vedere [Procedura:](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)Aggiornare un'origine dati con dati da un controllo host .

## <a name="see-also"></a>Vedi anche

- [Associare dati ai controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Aggiungere nuove origini dati](../data-tools/add-new-data-sources.md)
- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Procedura: Popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Procedura: Aggiornare un'origine dati con i dati di un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Usare i file di database locali nella Office delle soluzioni](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Panoramica del componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)