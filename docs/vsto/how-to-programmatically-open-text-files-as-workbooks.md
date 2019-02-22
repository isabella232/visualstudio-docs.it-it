---
title: 'Procedura: A livello di codice aprire i file di testo come cartelle di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d53c21247e18f198fdac1c22a3b38c0bc5348b6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633915"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Procedura: A livello di codice aprire i file di testo come cartelle di lavoro
  È possibile aprire un file di testo come cartella di lavoro. È necessario passare il nome del file di testo che si desidera aprire. È possibile specificare diversi parametri facoltativi, ad esempio il numero di riga per iniziare l'analisi e il formato della colonna dei dati nel file.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Esempio
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]

## <a name="compile-the-code"></a>Compilare il codice
 In questo esempio richiede i componenti seguenti:

-   Un file di testo delimitato da virgole denominato `Test.txt` che contenga almeno tre righe di testo.

-   Il file di testo `Test.txt` da archiviare nell'unità C.

## <a name="see-also"></a>Vedere anche
- [Lavorare con le cartelle di lavoro](../vsto/working-with-workbooks.md)
- [Procedura: A livello di codice aprire cartelle di lavoro](../vsto/how-to-programmatically-open-workbooks.md)
- [Procedura: A livello di codice crea nuove cartelle di lavoro](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Procedura: A livello di programmazione salvare cartelle di lavoro](../vsto/how-to-programmatically-save-workbooks.md)
- [Procedura: A livello di programmazione chiudere cartelle di lavoro](../vsto/how-to-programmatically-close-workbooks.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
