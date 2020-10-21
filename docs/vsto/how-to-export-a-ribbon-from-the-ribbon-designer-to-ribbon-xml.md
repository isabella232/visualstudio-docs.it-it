---
title: 'Procedura: esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione a XML della barra multifunzione'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- Ribbon [Office development in Visual Studio], exporting
- XML [Office development in Visual Studio], Ribbon
- Ribbon Designer [Office development in Visual Studio]
- exporting Ribbon
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf3101a062fa8b30ae821bf6a157319b6f37862a
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2020
ms.locfileid: "92298430"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Procedura: esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione a XML della barra multifunzione
  L'elemento **barra multifunzione (finestra di progettazione visiva)** non supporta tutti i possibili tipi di personalizzazione della barra multifunzione. Per personalizzare la barra multifunzione in modi avanzati, è possibile esportare la barra multifunzione dalla finestra di progettazione a XML della barra multifunzione e modificare direttamente il codice XML.

> [!NOTE]
> Non tutti i valori delle proprietà vengono visualizzati nel file XML della barra multifunzione. Per altre informazioni, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Per esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione a XML Ribbon

1. Fare clic con il pulsante destro del mouse sul file di codice della barra multifunzione in **Esplora soluzioni**, quindi scegliere **Progettazione visualizzazioni**.

2. Fare clic con il pulsante destro del mouse sulla finestra di progettazione Ribbon, quindi scegliere **Esporta barra multifunzione in XML**.

     Visual Studio aggiunge al progetto un file XML della barra multifunzione e un file di codice XML della barra multifunzione.

3. Nella classe di codice della barra multifunzione individuare i commenti che iniziano con `TODO:` .

4. Copiare il blocco di codice in questi commenti nella classe **ThisAddIn**, **ThisWorkbook**o **ThisDocument** , a seconda del tipo di soluzione che si sta sviluppando.

     Questo codice consente all'applicazione Microsoft Office di individuare e caricare la barra multifunzione personalizzata. Per altre informazioni, vedere [Ribbon XML](../vsto/ribbon-xml.md).

5. Nella classe **ThisAddIn**, **ThisWorkbook**o **ThisDocument** rimuovere il commento dal blocco di codice.

     Dopo aver annullato il commento del codice, il codice dovrebbe essere simile all'esempio seguente. In questo esempio viene chiamata la classe Ribbon `MyRibbon` .

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. Passare al file di codice XML della barra multifunzione e trovare l' `Ribbon Callbacks` area.

     Qui è possibile scrivere metodi di callback per gestire le azioni dell'utente, ad esempio facendo clic su un pulsante.

7. Creare un metodo di callback per ogni gestore eventi scritto nel codice della finestra di progettazione della barra multifunzione.

8. Spostare tutto il codice del gestore eventi dai gestori eventi ai metodi di callback e modificare il codice in modo che funzioni con il modello di programmazione di estendibilità della barra multifunzione (RibbonX).

     Per informazioni sulla scrittura di metodi di callback e sull'utilizzo del modello di programmazione RibbonX, vedere [Ribbon XML](../vsto/ribbon-xml.md).

## <a name="see-also"></a>Vedere anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura dettagliata: creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura dettagliata: creare una scheda personalizzata usando il codice XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
