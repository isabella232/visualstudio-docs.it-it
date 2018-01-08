---
title: 'Procedura: aprire documenti esistenti | Documenti Microsoft'
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
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
ms.assetid: 08f7fe4b-d96d-4a0c-b32a-aa7fd7992316
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 991a282cb3fc8a34f3434c9cdb0a9be214c9e3bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-open-existing-documents"></a>Procedura: aprire documenti esistenti a livello di codice
  Il <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metodo apre il documento di Microsoft Office Word esistente specificato da un nome di file e percorso completo. Questo metodo restituisce un <xref:Microsoft.Office.Interop.Word.Document> che rappresenta il documento aperto.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-open-a-document"></a>Per aprire un documento  
  
-   Chiamare il <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metodo il <xref:Microsoft.Office.Interop.Word.Documents> raccolta e specificare un percorso del documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]  
  
### <a name="to-open-a-document-as-read-only"></a>Per aprire un documento in sola lettura  
  
-   Chiamare il <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metodo, fornire un percorso del documento e impostare il *ReadOnly* argomento **True** nella chiamata al metodo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio di codice presenta i requisiti seguenti:  
  
-   Un documento denominato NewDocument. doc deve essere presente in una directory denominata Test sull'unità C.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creazione di nuovi documenti a livello di codice](../vsto/how-to-programmatically-create-new-documents.md)   
 [Procedura: chiudere i documenti a livello di codice](../vsto/how-to-programmatically-close-documents.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  