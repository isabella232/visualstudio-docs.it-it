---
title: 'Procedura: aggiungere righe e colonne alle tabelle di Word a livello di codice'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cc8fbc80a58afcb6f2256c56b1071276c50f319b
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985850"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Procedura: aggiungere righe e colonne alle tabelle di Word a livello di codice
  In una tabella di Microsoft Office Word le celle sono organizzate in righe e colonne. È possibile usare il metodo <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Rows> per aggiungere righe alla tabella e il metodo <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Columns> per aggiungere colonne.

 [!INCLUDE[appliesto_wdalldocapp](includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customization-examples"></a>Esempi di personalizzazione a livello di documento
 Gli esempi di codice seguenti possono essere usati in una personalizzazione a livello di documento. Per usare questi esempi, eseguirli dalla classe `ThisDocument` nel progetto. Gli esempi presuppongono che il documento associato alla personalizzazione contenga già almeno una tabella.

> [!IMPORTANT]
> Questo codice viene eseguito solo in progetti creati usando uno dei modelli di progetto seguenti:
>
> - Documento di Word 2013
> - Modello di Word 2013
> - Documento di Word 2010
> - Modello di Word 2010
>
>   Se si vuole eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento all'assembly **Microsoft. Office. Interop. Word** , quindi è necessario usare le classi di tale assembly per aggiungere righe e colonne alle tabelle. Per altre informazioni, vedere [procedura: destinare applicazioni di Office tramite assembly di interoperabilità primari](how-to-target-office-applications-through-primary-interop-assemblies.md) e [riferimento all'assembly di interoperabilità primario di Word 2010](office-primary-interop-assemblies.md).

### <a name="to-add-a-row-to-a-table"></a>Per aggiungere una riga a una tabella

1. Usare il metodo <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> per aggiungere una riga alla tabella.

     [!code-vb[Trin_VstcoreWordAutomation#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>Per aggiungere una colonna a una tabella

1. Usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> e quindi usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> per applicare la stessa larghezza a tutte le colonne.

     [!code-vb[Trin_VstcoreWordAutomation#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]

## <a name="vsto-add-in-examples"></a>Esempi di componenti aggiuntivi VSTO
 Gli esempi di codice seguenti possono essere usati in un componente aggiuntivo VSTO. Per usare gli esempi, eseguirli dalla classe `ThisAddIn` nel progetto. Gli esempi presuppongono che il documento attivo contenga già almeno una tabella.

> [!IMPORTANT]
> Questo codice viene eseguito solo in progetti creati usando modelli di componente aggiuntivo VSTO per Word.
>
> Se si vuole eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento all'assembly **Microsoft. Office. Interop. Word** , quindi è necessario usare le classi di tale assembly per aggiungere righe e colonne alle tabelle. Per altre informazioni, vedere [procedura: destinare applicazioni di Office tramite assembly di interoperabilità primari](how-to-target-office-applications-through-primary-interop-assemblies.md) e [riferimento all'assembly di interoperabilità primario di Word 2010](office-primary-interop-assemblies.md).

### <a name="to-add-a-row-to-a-table"></a>Per aggiungere una riga a una tabella

1. Usare il metodo <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> per aggiungere una riga alla tabella.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>Per aggiungere una colonna a una tabella

1. Usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> e quindi usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> per applicare la stessa larghezza a tutte le colonne.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]

## <a name="see-also"></a>Vedere anche
- [Procedura: creare tabelle di Word a livello di codice](how-to-programmatically-create-word-tables.md)
- [Procedura: aggiungere testo e formattazione alle celle delle tabelle di Word a livello di codice](how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Procedura: popolare tabelle di Word con proprietà dei documenti a livello di codice](how-to-programmatically-populate-word-tables-with-document-properties.md)
