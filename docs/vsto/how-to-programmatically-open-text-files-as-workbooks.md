---
title: 'Procedura: a livello di codice aprire i file di testo come cartelle di lavoro'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b7bc7caa5dbceb727394b8543b7659cc43e64a36
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257647"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Procedura: a livello di codice aprire i file di testo come cartelle di lavoro
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
 [Lavorare con le cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [Procedura: aprire cartelle di lavoro](../vsto/how-to-programmatically-open-workbooks.md)   
 [Procedura: creare nuove cartelle di lavoro](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Procedura: a livello di programmazione salvare cartelle di lavoro](../vsto/how-to-programmatically-save-workbooks.md)   
 [Procedura: chiudere a livello di codice le cartelle di lavoro](../vsto/how-to-programmatically-close-workbooks.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  