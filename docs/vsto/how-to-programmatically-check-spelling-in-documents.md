---
title: 'Procedura: eseguire il controllo ortografico nei documenti a livello di codice'
description: Informazioni su come controllare l'ortografia in un documento a livello di codice, è possibile usare il metodo CheckSpelling.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 85294b21e9fd1f52f5cc707fc6824a87530e3cda
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848313"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Procedura: eseguire il controllo ortografico nei documenti a livello di codice
  Per controllare l'ortografia in un documento, usare il <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> metodo. Questo metodo restituisce un valore booleano che indica se il parametro fornito è stato digitato correttamente.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Per controllare l'ortografia e visualizzare i risultati in una finestra di messaggio

1. Chiamare il <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> metodo e passargli un intervallo di testo per verificare la presenza di errori di ortografia. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]

## <a name="see-also"></a>Vedi anche
- [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
