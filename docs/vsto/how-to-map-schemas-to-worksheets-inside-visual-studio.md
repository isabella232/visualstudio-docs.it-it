---
title: 'Procedura: eseguire il mapping di schemi a fogli di fogli di Visual Studio'
titleSuffix: ''
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c8a0437b940953e89e24969314f63df34d223496
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538138"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Procedura: eseguire il mapping di schemi a fogli di fogli di Visual Studio
  È possibile eseguire il mapping di un XML Schema a un foglio di un foglio di tempo mentre il foglio di foglio è aperto in Visual Studio Si usa lo stesso Microsoft Office strumenti di Excel usati quando la cartella di lavoro è aperta all'esterno di Visual Studio. Il progetto di Office crea gli stessi oggetti se lo schema viene mappato al foglio di lavoro prima o dopo la creazione della soluzione Excel.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Non è possibile utilizzare schemi XML multipart in soluzioni Excel.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Per eseguire il mapping di un XML Schema a un foglio di lavoro di Excel in Visual Studio

1. Aprire la cartella di lavoro di Excel o il progetto di modello all'interno di Visual Studio.

2. Fare clic nel foglio di foglio per spostare lo stato attivo sulla finestra di progettazione.

3. Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .

    > [!NOTE]
    > Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per ulteriori informazioni, vedere [procedura: visualizzare la scheda Developer sulla barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Nel gruppo **XML** fare clic su **origine**.

     Verrà visualizzata la finestra **origine XML** .

5. Nella finestra **origine XML** fare clic su **mappe XML**.

     Verrà visualizzata la finestra di dialogo **mapping XML** .

6. Nella finestra di dialogo **mappe XML** fare clic su **Aggiungi**.

7. Individuare il file di schema, selezionarlo e quindi fare clic su **Apri**.

8. Fare clic su **OK**.

     Lo schema è rappresentato nella finestra di **origine XML** . Nel progetto, un oggetto tipizzato <xref:System.Data.DataSet> viene generato in base allo schema e <xref:System.Windows.Forms.BindingSource> viene creato un oggetto.

9. Trascinare gli elementi dalla finestra di **origine XML** ai punti del foglio di lavoro in cui si desidera creare i controlli corrispondenti.

     Se si trascina un elemento dello schema non ripetuto, il progetto di Office genera un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo che viene associato automaticamente a <xref:System.Windows.Forms.BindingSource> .

     Se si trascina un elemento dello schema ripetuto, il progetto di Office genera un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo che non viene associato automaticamente a un'origine dati. Per ulteriori informazioni, vedere [XML Schema e dati nelle personalizzazioni a livello di documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: eseguire il mapping degli schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [XML Schema e dati nelle personalizzazioni a livello di documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
