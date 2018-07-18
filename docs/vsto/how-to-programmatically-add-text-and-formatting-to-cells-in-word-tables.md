---
title: 'Procedura: aggiungere a livello di codice di testo e formattazione alle celle delle tabelle di Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a7fff8451c469e58d7c23ab6bd3366db2fa10d59
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256344"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Procedura: aggiungere a livello di codice di testo e formattazione alle celle delle tabelle di Word
  Ogni tabella è costituita da una raccolta di celle. Ogni singolo oggetto <xref:Microsoft.Office.Interop.Word.Cell> rappresenta una cella della tabella. Le singole celle vengono individuate tramite la relativa posizione nella tabella. Questo esempio si riferisce alla cella che si trova nella prima riga e nella prima colonna della tabella. Viene aggiunto un testo alla cella e viene applicata la formattazione.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-add-text-and-formatting-to-cells"></a>Per aggiungere testo e formattazione alle celle  
  
1.  Fare riferimento alla cella tramite la relativa posizione nella tabella, aggiungere testo alla cella e applicare la formattazione.  
  
     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento. Per usare questo esempio, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]  
  
     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo. Per usare l'esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creazione di tabelle di Word a livello di codice](../vsto/how-to-programmatically-create-word-tables.md)   
 [Procedura: a livello di codice aggiungere righe e colonne alle tabelle di Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Procedura: a livello di codice compilare tabelle di Word con le proprietà documento](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  