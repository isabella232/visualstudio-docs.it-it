---
title: 'Procedura: Popolare documenti con dati dai servizi'
description: Informazioni su come usare i dati dei servizi nella soluzione e su come usare i Windows Form per visualizzare i dati in un documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e68795d79b3cbd0bc190bc174200b90b3676779b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155980"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Procedura: Popolare documenti con dati dai servizi

L'accesso ai dati funziona in modo identico per i progetti a livello di documento per Microsoft Office e per i progetti Windows Form. Per inserire i dati nella soluzione si possono usare gli stessi strumenti e lo stesso codice e per visualizzarli è possibile persino usare i controlli Windows Form. Inoltre, è possibile usare i controlli chiamati controlli host, ossia oggetti nativi in Microsoft Office Excel e Microsoft Office Word migliorati con funzionalità di associazione di dati ed eventi. Per altre informazioni, vedere [Panoramica di elementi host e controlli host](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

L'esempio seguente mostra come aggiungere controlli con associazione ai dati ai documenti in fase di progettazione. Per un esempio di come aggiungere controlli associati a dati nei componenti aggiuntivi VSTO in fase di esecuzione, vedere [Procedura dettagliata:](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md)Associare dati da un servizio in un progetto di componente aggiuntivo VSTO .

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Per popolare un progetto a livello di documento con i dati di un servizio Web

1. Aprire la finestra **Origini dati** e creare un'origine dati del servizio per il progetto. Per altre informazioni, vedere [Add new data sources](../data-tools/add-new-data-sources.md) (Aggiungere nuove origini dati).

2. Trascinare la tabella o il campo desiderato dalla finestra **Origini dati** al documento.

     Viene creato un controllo nel documento, un oggetto <xref:System.Windows.Forms.BindingSource> associato alla classe di oggetti nel progetto e classi per il servizio.

3. Nel codice creare un'istanza della classe del servizio Web a cui si è connessi nel passaggio 1.

4. Se sono presenti proprietà necessarie per la comunicazione con il servizio Web, creare istanze di tali proprietà.

5. Creare e inviare una richiesta di dati usando i metodi esposti dal servizio Web e le eventuali istanze delle proprietà create nel passaggio 4.

     I metodi utilizzati dipendono dalle offerte del servizio Web.

6. Assegnare la risposta ai dati dal servizio Web alla <xref:System.Windows.Forms.BindingSource.DataSource%2A> proprietà dell'oggetto <xref:System.Windows.Forms.BindingSource> .

Quando si esegue il progetto, i controlli visualizzano il primo record nell'origine dati. È possibile abilitare lo scorrimento dei record gestendo gli eventi di valuta tramite gli oggetti in <xref:System.Windows.Forms.BindingSource>.

## <a name="see-also"></a>Vedi anche

- [Associare dati ai controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Aggiungere nuove origini dati](../data-tools/add-new-data-sources.md)
- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Procedura: Popolare fogli di lavoro con dati da un database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Procedura: Popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Procedura: Popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Procedura: Aggiornare un'origine dati con i dati di un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)