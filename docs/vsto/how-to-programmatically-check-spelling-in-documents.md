---
title: "Procedura: Controllare l'ortografia nei documenti a livello di codice"
description: Per controllare l'ortografia in un documento a livello di codice, è possibile usare il metodo CheckSpelling.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a2f03c61a1d35e9c66e1e660a3d2fdb56c2bac9ba6f25cd41cd795d2f172ee51
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121268079"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Procedura: Controllare l'ortografia nei documenti a livello di codice
  Per controllare l'ortografia in un documento, usare il <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> metodo . Questo metodo restituisce un valore booleano che indica se il parametro fornito è stato digitato correttamente.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Per controllare l'ortografia e visualizzare i risultati in una finestra di messaggio

1. Chiamare il <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> metodo e passarlo a un intervallo di testo per verificare la presenza di errori di ortografia. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet113":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet113":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
