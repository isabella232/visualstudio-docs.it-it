---
title: "Procedura: Eseguire il mapping degli schemi ai fogli di lavoro all'interno Visual Studio"
description: Informazioni su come eseguire il mapping di uno schema XML a un Microsoft Office Excel di lavoro mentre il foglio di lavoro è aperto in Visual Studio.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9fb7a8a2a3ae7a8b0f7f3898fdf5b13b105f58886f1d5586f98ad625cbaa5d0a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424124"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Procedura: Eseguire il mapping degli schemi ai fogli di lavoro all'interno Visual Studio
  È possibile eseguire il mapping di uno schema XML a un foglio di lavoro mentre il foglio di lavoro è aperto in Visual Studio. Usare gli stessi strumenti Microsoft Office Excel utilizzati quando la cartella di lavoro è aperta all'esterno Visual Studio. Il Office crea gli stessi oggetti, indipendentemente dal fatto che lo schema venga mappato al foglio di lavoro prima o dopo aver creato la Excel soluzione.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Non è possibile usare XML Schema multipart in Excel soluzioni.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Per eseguire il mapping di uno schema XML a un Excel di lavoro di Visual Studio

1. Aprire il progetto Excel cartella di lavoro o modello all'interno Visual Studio.

2. Fare clic nel foglio di lavoro per spostare lo stato attivo sulla finestra di progettazione.

3. Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .

    > [!NOTE]
    > Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: Visualizzare la scheda Sviluppatore sulla barra multifunzione.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

4. Nel gruppo **XML** fare clic su **Origine**.

     Verrà **visualizzata la finestra Origine XML.**

5. Nella finestra **Origine XML fare** clic su XML **Mappe**.

     Verrà **visualizzata la Mappe** xml .

6. Nella finestra **di dialogo Mappe** XML fare clic su **Aggiungi**.

7. Passare al file di schema, selezionarlo e quindi fare clic su **Apri.**

8. Fare clic su **OK**.

     Lo schema è rappresentato nella **finestra Origine XML.** Nel progetto viene generato un oggetto <xref:System.Data.DataSet> tipidato in base allo schema e viene <xref:System.Windows.Forms.BindingSource> creato un oggetto .

9. Trascinare elementi dalla **finestra Origine XML** nelle posizioni del foglio di lavoro in cui si desidera creare i controlli corrispondenti.

     Se si trascina un elemento dello schema non ripetuto, il Office genera un controllo associato <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> automaticamente a <xref:System.Windows.Forms.BindingSource> .

     Se si trascina un elemento dello schema ripetuto, il Office genera un controllo che non viene associato <xref:Microsoft.Office.Tools.Excel.ListObject> automaticamente a un'origine dati. Per altre informazioni, vedere [XML Schema e dati nelle personalizzazioni a livello di documento.](../vsto/xml-schemas-and-data-in-document-level-customizations.md)

## <a name="see-also"></a>Vedi anche
- [Procedura: Eseguire il mapping di schemi a documenti di Word all'interno Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Xml Schema e dati nelle personalizzazioni a livello di documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
