---
title: 'Procedura: aprire documenti esistenti a livello di codice'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eba4d110b06147db384a4d7aafe01c7d9f272ba3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85519899"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Procedura: aprire documenti esistenti a livello di codice
  Il <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metodo apre il documento Microsoft Office Word esistente specificato da un percorso completo e un nome file. Questo metodo restituisce un oggetto <xref:Microsoft.Office.Interop.Word.Document> che rappresenta il documento aperto.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>Per aprire un documento

- Chiamare il <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metodo della <xref:Microsoft.Office.Interop.Word.Documents> raccolta e fornire un percorso al documento.

     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]

## <a name="to-open-a-document-as-read-only"></a>Per aprire un documento come di sola lettura

- Chiamare il <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metodo, fornire un percorso al documento e impostare l'argomento *ReadOnly* su **true** nella chiamata al metodo.

     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presenta i requisiti seguenti:

- Un documento denominato *NewDocument.doc* deve esistere in una directory denominata *test* sull'unità C.

## <a name="see-also"></a>Vedere anche
- [Procedura: creare nuovi documenti a livello di codice](../vsto/how-to-programmatically-create-new-documents.md)
- [Procedura: chiudere documenti a livello di codice](../vsto/how-to-programmatically-close-documents.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
