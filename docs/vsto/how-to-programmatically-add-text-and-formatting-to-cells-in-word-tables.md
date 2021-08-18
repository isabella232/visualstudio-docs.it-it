---
title: Aggiungere la formattazione & testo alle celle della tabella di Word a livello di codice
description: Informazioni su come aggiungere testo e formattazione a livello di codice alle celle Microsoft Office tabelle di Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 6cdb47e1db9893c128850407022eb95a358eb15e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046711"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Procedura: Aggiungere testo e formattazione alle celle nelle tabelle di Word a livello di codice
  Ogni tabella è costituita da una raccolta di celle. Ogni singolo oggetto <xref:Microsoft.Office.Interop.Word.Cell> rappresenta una cella della tabella. Le singole celle vengono individuate tramite la relativa posizione nella tabella. Questo esempio si riferisce alla cella che si trova nella prima riga e nella prima colonna della tabella. Viene aggiunto un testo alla cella e viene applicata la formattazione.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-add-text-and-formatting-to-cells"></a>Per aggiungere testo e formattazione alle celle

1. Fare riferimento alla cella tramite la relativa posizione nella tabella, aggiungere testo alla cella e applicare la formattazione.

     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento. Per usare questo esempio, eseguirlo dalla classe `ThisDocument` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet97":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet97":::

     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo. Per usare l'esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet97":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet97":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare tabelle di Word a livello di codice](../vsto/how-to-programmatically-create-word-tables.md)
- [Procedura: Aggiungere righe e colonne alle tabelle di Word a livello di codice](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Procedura: Popolare a livello di codice le tabelle di Word con le proprietà del documento](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
