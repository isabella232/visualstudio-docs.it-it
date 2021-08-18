---
title: 'Procedura: Popolare documenti con dati da oggetti'
description: Informazioni su come usare i dati di un oggetto nella soluzione ed è possibile usare i Windows Form per visualizzare i dati in un documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: cba1869353071be287f244c7783964b010fff91d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046789"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Procedura: Popolare documenti con dati da oggetti

L'accesso ai dati di un oggetto dati è uguale sia nei progetti a livello di documento per Microsoft Office Word, sia nei progetti Windows Form. Per inserire i dati di un oggetto nella soluzione si possono usare gli stessi strumenti e lo stesso codice e per visualizzarli è possibile usare i controlli Windows Form. Inoltre, è possibile visualizzare i dati tramite i controlli host. I controlli host sono oggetti nativi di Microsoft Office Word che sono stati migliorati con eventi e funzionalità di data binding. Per altre informazioni, vedere [Panoramica di elementi host e controlli host](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

Per popolare il documento con i dati di un oggetto, è necessario completare tre passaggi di base:

- Aggiungere al documento un controllo che è possibile associare ai dati.

- Aggiungere un oggetto dati al documento.

- Connettere l'oggetto dati a BindingSource

## <a name="to-add-a-data-object"></a>Per aggiungere un oggetto dati

Per aggiungere un oggetto dati, aprire la **finestra Origini** dati e creare un'origine dati da un oggetto . Per altre informazioni, vedere [Add new data sources](../data-tools/add-new-data-sources.md) (Aggiungere nuove origini dati).

## <a name="connect-the-data-object-to-the-bindingsource"></a>Connessione'oggetto dati in BindingSource

Nei progetti a livello di documento i controlli vengono aggiunti al documento e associati ai dati in fase di progettazione.

Nei progetti di componente aggiuntivo VSTO è possibile creare controlli e associarli in fase di esecuzione.

### <a name="document-level-projects"></a>Progetti a livello di documento

Per connettere l'oggetto dati a BindingSource:

1. Trascinare il campo dati desiderato dalla finestra **Origini dati** al documento in modo da creare automaticamente un controllo.

2. Nel codice creare un'istanza del tipo di oggetto selezionato per l'origine dati.

3. Assegnare l'istanza alla proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> dell'oggetto <xref:System.Windows.Forms.BindingSource>.

### <a name="application-level-projects"></a>Progetti a livello di applicazione

Per connettere l'oggetto dati a BindingSource:

1. Nel codice creare un'istanza del tipo di oggetto associato all'origine dati.

2. Creare un'istanza di un <xref:System.Windows.Forms.BindingSource>.

3. Assegnare l'istanza dell'origine dati alla proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> dell'oggetto <xref:System.Windows.Forms.BindingSource>.

4. Aggiungere l'origine dati come data binding al controllo.

## <a name="see-also"></a>Vedi anche

- [Aggiungere nuove origini dati](../data-tools/add-new-data-sources.md)
- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Procedura: Popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Procedura: Aggiornare un'origine dati con i dati di un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Panoramica del componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)