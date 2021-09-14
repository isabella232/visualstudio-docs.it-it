---
title: 'Procedura: Aprire documenti esistenti a livello di codice'
description: Informazioni su come usare il metodo Open per aprire un documento Microsoft Word specificato da un percorso completo e da un nome file.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e1785053c4342144e56cb67e1f75adbef484058b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710062"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Procedura: Aprire documenti esistenti a livello di codice
  Il <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metodo apre l'Microsoft Office documento di Word specificato da un percorso completo e da un nome file. Questo metodo restituisce un <xref:Microsoft.Office.Interop.Word.Document> oggetto che rappresenta il documento aperto.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>Per aprire un documento

- Chiamare il <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metodo della raccolta e fornire un percorso al <xref:Microsoft.Office.Interop.Word.Documents> documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet5":::

## <a name="to-open-a-document-as-read-only"></a>Per aprire un documento in sola lettura

- Chiamare il <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metodo , fornire un percorso al documento e impostare l'argomento *ReadOnly* su **True** nella chiamata al metodo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet6":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presenta i requisiti seguenti:

- Un documento denominato *NewDocument.doc* deve esistere in una directory denominata *Test* nell'unità C.

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare nuovi documenti a livello di codice](../vsto/how-to-programmatically-create-new-documents.md)
- [Procedura: Chiudere documenti a livello di codice](../vsto/how-to-programmatically-close-documents.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
