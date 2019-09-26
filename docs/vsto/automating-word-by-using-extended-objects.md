---
title: Automatizzare Word usando oggetti estesi
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], automating
- extended objects [Office development in Visual Studio], Word
- automation [Office development in Visual Studio], Word
- host items [Office development in Visual Studio], Word
- automating Word
- controls [Office development in Visual Studio], Word host controls
- host controls, Word
- host controls [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], host controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 083fe8cdd3bf9d0e4de4809aacfb78b537e4ed8e
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255540"
---
# <a name="automate-word-by-using-extended-objects"></a>Automatizzare Word usando oggetti estesi
  Quando si sviluppano soluzioni Word in Visual Studio, è possibile usare *elementi host* e *controlli host*nelle soluzioni. Si tratta di oggetti che estendono determinati oggetti usati comunemente nel modello a oggetti di Word (cioè, il modello a oggetti esposto dall'assembly di interoperabilità primario per Word), come ad esempio gli oggetti <xref:Microsoft.Office.Interop.Word.Document> e <xref:Microsoft.Office.Interop.Word.ContentControl> . Gli oggetti estesi si comportano come gli oggetti di Word su cui sono basati, ma aggiungono ulteriori eventi e funzionalità di data binding agli oggetti.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Gli elementi e i controlli host sono disponibili nelle personalizzazioni a livello di documento e dei componenti aggiuntivi VSTO, sebbene il contenuto in cui possono essere usati è diverso per ogni tipo di soluzione. Per altre informazioni, vedere [Cenni preliminari sugli elementi host e sui controlli host](../vsto/host-items-and-host-controls-overview.md).

## <a name="document-host-item"></a>Elemento host Document
 I progetti Word consentono l'accesso all'elemento host <xref:Microsoft.Office.Tools.Word.Document> . L'elemento host <xref:Microsoft.Office.Tools.Word.Document> viene usato come contenitore per altri controlli, inclusi i controlli host e quelli Windows Form, e gestisce informazioni relative ai controlli della relativa area. L'elemento host <xref:Microsoft.Office.Tools.Word.Document> fornisce anche la maggior parte dei membri della classe <xref:Microsoft.Office.Interop.Word.Document> , ovvero la classe corrispondente nel modello a oggetti di Word.

 Per ulteriori informazioni, vedere [Document host Item](../vsto/document-host-item.md).

## <a name="word-host-controls"></a>controlli host di Word
 Vi sono vari controlli host per Word che consentono di creare, organizzare e automatizzare i documenti. La maggior parte delle funzionalità offerte include l'importazione, la presentazione e la protezione dei dati. Si tratta di controlli host che forniscono funzionalità di data binding ed eventi che non sono disponibili nelle rispettive controparti del modello a oggetti di Word nativo.

 Nei progetti a livello di documento è possibile aggiungere al documento qualsiasi controllo host in fase di progettazione oppure controlli contenuto e controlli segnalibro in fase di esecuzione. Nei progetti di componente aggiuntivo VSTO è possibile aggiungere controlli contenuto e segnalibro a qualsiasi documento aperto in fase di esecuzione.

 Per altre informazioni sui controlli host da poter usare in progetti Word, vedere i seguenti argomenti:

- [Controlli contenuto](../vsto/content-controls.md)

- [Segnalibro (controllo)](../vsto/bookmark-control.md)

- [XMLNode (controllo)](../vsto/xmlnode-control.md)

- [Controllo XMLNodes](../vsto/xmlnodes-control.md)

## <a name="see-also"></a>Vedere anche
- [Procedura: Aggiungere controlli contenuto a documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Procedura: Aggiungere controlli Bookmark ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Procedura: Aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Procedura: Aggiungere controlli XMLNodes ai documenti di Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Procedura: Ridimensionare i controlli Bookmark](../vsto/how-to-resize-bookmark-controls.md)
- [Procedura dettagliata: Creare un modello usando i controlli contenuto](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)
- [Procedura dettagliata: Associare controlli contenuto a parti XML personalizzate](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)
- [Procedura dettagliata: Creare menu di scelta rapida per i segnalibri](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Soluzioni Word](../vsto/word-solutions.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Estendi i documenti di Word e le cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
