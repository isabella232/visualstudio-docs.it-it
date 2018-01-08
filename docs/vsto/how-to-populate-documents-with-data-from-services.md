---
title: 'Procedura: popolare documenti con dati da servizi | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
ms.assetid: 4c42653c-627f-445e-9024-8482eaf5562e
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5cdcfc080251d62bf0f7dbede2016b4821383c5a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Procedura: Compilare documenti con dati forniti da servizi
  L'accesso ai dati funziona in modo identico per i progetti a livello di documento per Microsoft Office e per i progetti Windows Form. Per inserire i dati nella soluzione si possono usare gli stessi strumenti e lo stesso codice e per visualizzarli è possibile persino usare i controlli Windows Form. Inoltre, è possibile usare i controlli chiamati controlli host, ossia oggetti nativi in Microsoft Office Excel e Microsoft Office Word migliorati con funzionalità di associazione di dati ed eventi. Per altre informazioni, vedere [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 L'esempio seguente mostra come aggiungere controlli con associazione ai dati ai documenti in fase di progettazione. Per un esempio di come aggiungere controlli associati a dati nei componenti aggiuntivi VSTO in fase di esecuzione, vedere [procedura dettagliata: associazione ai dati di un servizio in un VSTO aggiungere nel progetto](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).  
  
 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [procedura di interazione con i servizi Web di Microsoft Excel?](http://go.microsoft.com/fwlink/?LinkID=130284).  
  
### <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Per popolare un progetto a livello di documento con i dati da un servizio Web  
  
1.  Aprire la finestra **Origini dati** e creare un'origine dati del servizio per il progetto. Per altre informazioni, vedere [Add new data sources](/visualstudio/data-tools/add-new-data-sources) (Aggiungere nuove origini dati).  
  
2.  Trascinare la tabella o il campo desiderato dalla finestra **Origini dati** al documento.  
  
     Viene creato un controllo nel documento, un oggetto <xref:System.Windows.Forms.BindingSource> associato alla classe di oggetti nel progetto e classi per il servizio.  
  
3.  Nel codice creare un'istanza della classe del servizio Web a cui è stata eseguita la connessione nel passaggio 1.  
  
4.  Se alcune proprietà sono necessarie per la comunicazione con il servizio Web, creare istanze di queste proprietà.  
  
5.  Creare e inviare una richiesta di dati usando i metodi esposti dal servizio Web e le eventuali istanze delle proprietà create nel passaggio 4.  
  
     I metodi usati dipendono dall'offerta del servizio Web.  
  
6.  Assegnare la risposta di dati dal servizio Web alla proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> di <xref:System.Windows.Forms.BindingSource>.  
  
 Quando si esegue il progetto, i controlli visualizzano il primo record nell'origine dati. È possibile abilitare lo scorrimento dei record gestendo gli eventi di valuta tramite gli oggetti in <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="see-also"></a>Vedere anche  
 [Associazione dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Aggiungere nuove origini dati](/visualstudio/data-tools/add-new-data-sources)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Procedura: popolare fogli di lavoro con dati da un Database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Procedura: popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Procedura: popolare documenti con dati da un Database](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Procedura: Aggiornare un'origine dati con i dati di un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)  
  
  