---
title: 'Procedura: creazione di nuovi documenti di Visio a livello di codice'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4142ebe86ea69fbb0a74f25c2a7053a60c527cdb
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671560"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Procedura: creazione di nuovi documenti di Visio a livello di codice
  Quando si crea un nuovo disegno di Microsoft Office Visio, viene aggiunto alla raccolta `Microsoft.Office.Interop.Visio.Documents` di documenti di Visio aperti. Il metodo `Microsoft.Office.Interop.Visio.Documents.Add` crea quindi un nuovo documento di disegno di Visio. Per altre informazioni, vedere la documentazione di riferimento di VBA relativa al metodo [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) .  
  
## <a name="create-new-blank-documents"></a>Creare nuovi documenti vuoti  
  
### <a name="to-create-a-new-document"></a>Per creare un nuovo documento  
  
-   Usare il metodo `Microsoft.Office.Interop.Visio.Documents.Add` per creare un nuovo documento vuoto che non si basa su un modello.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="create-documents-copied-from-existing-documents"></a>Creazione di documenti copiati da documenti esistenti  
 Il metodo `Microsoft.Office.Interop.Visio.Documents.Add` può creare un nuovo documento che è una copia di un documento di Visio esistente. È necessario specificare il nome file e il percorso completo del diagramma.  
  
### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Per creare un nuovo documento copiato da un documento esistente  
  
-   Chiamare il metodo `Microsoft.Office.Interop.Visio.Documents.Add` e specificare il percorso del diagramma di Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="create-stencils-copied-from-existing-stencils"></a>Creazione di stencil copiati da stencil esistenti  
 Il metodo [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) può creare un nuovo stencil che è una copia di uno stencil di Visio esistente. È necessario specificare il nome file e il percorso completo dello stencil.  
  
### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Per creare un nuovo stencil copiato da uno stencil esistente  
  
-   Chiamare il metodo `Microsoft.Office.Interop.Visio.Documents.Add` e specificare il percorso dello stencil.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="create-documents-based-on-existing-templates"></a>Creazione di documenti basati su modelli esistenti  
 Il `Microsoft.Office.Interop.Visio.Documents.Add` metodo consente di creare un nuovo documento (un *vsd* file) che si basa su un modello di Visio esistente (un *VST* file). Questo metodo copia gli stencil, gli stili e le impostazioni che fanno parte dell'area di lavoro modello. È necessario specificare il nome file e il percorso completo del modello.  
  
### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Per creare un nuovo documento basato su un modello esistente  
  
-   Chiamare il metodo `Microsoft.Office.Interop.Visio.Documents.Add` e specificare il percorso del modello.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
 Questo esempio di codice presenta i requisiti seguenti:  
  
-   Un documento di Visio denominato `myDrawing.vsd` deve trovarsi in una directory denominata `Test` nel *documenti* cartella (per Windows XP e versioni precedenti) o nella *documenti* cartella (per Windows Vista).  
  
-   Un documento di Visio denominato `myStencil.vss` deve trovarsi in una directory denominata `Test` nel *documenti* cartella (per Windows XP e versioni precedenti) o nella *documenti* cartella (per Windows Vista).  
  
-   Un documento di Visio denominato `myTemplate.vst` deve trovarsi in una directory denominata `Test` nel *documenti* cartella (per Windows XP e versioni precedenti) o nella *documenti* cartella (per Windows Vista).  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti Visio](../vsto/visio-object-model-overview.md)   
 [Procedura: aprire documenti di Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Procedura: chiudere a livello di programmazione di documenti di Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Procedura: a livello di programmazione salvare documenti di Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Procedura: stampa di documenti di Visio a livello di codice](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  