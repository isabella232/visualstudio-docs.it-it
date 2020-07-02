---
title: Aggiungere testo & formattazione alle celle della tabella di Word a livello di codice
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: acd43c82c6dae32ef6595b2f63c06fe61f3c6168
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538047"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Procedura: aggiungere testo e formattazione alle celle delle tabelle di Word a livello di codice
  Ogni tabella è costituita da una raccolta di celle. Ogni singolo oggetto <xref:Microsoft.Office.Interop.Word.Cell> rappresenta una cella della tabella. Le singole celle vengono individuate tramite la relativa posizione nella tabella. Questo esempio si riferisce alla cella che si trova nella prima riga e nella prima colonna della tabella. Viene aggiunto un testo alla cella e viene applicata la formattazione.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-add-text-and-formatting-to-cells"></a>Per aggiungere testo e formattazione alle celle

1. Fare riferimento alla cella tramite la relativa posizione nella tabella, aggiungere testo alla cella e applicare la formattazione.

     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento. Per usare questo esempio, eseguirlo dalla classe `ThisDocument` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]

     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo. Per usare l'esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]

## <a name="see-also"></a>Vedere anche
- [Procedura: creare tabelle di Word a livello di codice](../vsto/how-to-programmatically-create-word-tables.md)
- [Procedura: aggiungere righe e colonne alle tabelle di Word a livello di codice](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Procedura: popolare tabelle di Word con proprietà dei documenti a livello di codice](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
