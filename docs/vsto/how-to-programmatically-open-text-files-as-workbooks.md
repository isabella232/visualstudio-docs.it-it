---
title: 'Procedura: Aprire file di testo come cartelle di lavoro a livello di codice'
description: Informazioni su come usare Visual Studio per aprire a livello di codice un file di testo come Microsoft Excel cartella di lavoro.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 68ee509eca06d6785f47fc776ad42c9f010b5219
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710061"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Procedura: Aprire file di testo come cartelle di lavoro a livello di codice
  È possibile aprire un file di testo come cartella di lavoro. È necessario passare il nome del file di testo che si vuole aprire. È possibile specificare diversi parametri facoltativi, ad esempio il numero di riga su cui iniziare l'analisi e il formato della colonna dei dati nel file.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Esempio
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet80":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet80":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede i componenti seguenti:

- File di testo delimitato da virgole denominato `Test.txt` che contiene almeno tre righe di testo.

- File di testo `Test.txt` da archiviare nell'unità C.

## <a name="see-also"></a>Vedi anche
- [Usare le cartelle di lavoro](../vsto/working-with-workbooks.md)
- [Procedura: Aprire cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-open-workbooks.md)
- [Procedura: Creare nuove cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Procedura: Salvare cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-save-workbooks.md)
- [Procedura: Chiudere cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-close-workbooks.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
