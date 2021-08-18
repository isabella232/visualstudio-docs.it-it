---
title: 'Procedura: Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione al codice XML della barra multifunzione'
description: Per personalizzare la barra multifunzione, è possibile esportare la barra multifunzione dalla finestra di progettazione al codice XML della barra multifunzione e modificare direttamente il codice XML.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 88c4e0be4ccab3d83c7dcd9ebe024493d2beab52
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046828"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Procedura: Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione al codice XML della barra multifunzione
  **L'elemento Barra multifunzione (finestra di progettazione visiva)** non supporta tutti i tipi possibili di personalizzazione della barra multifunzione. Per personalizzare la barra multifunzione in modi avanzati, è possibile esportare la barra multifunzione dalla finestra di progettazione al codice XML della barra multifunzione e modificare direttamente il codice XML.

> [!NOTE]
> Non tutti i valori delle proprietà vengono visualizzati nel file XML della barra multifunzione. Per altre informazioni, vedere Panoramica [della barra multifunzione.](../vsto/ribbon-overview.md)

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Per esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione al codice XML della barra multifunzione

1. Fare clic con il pulsante destro del mouse sul file di codice della barra **multifunzione in Esplora soluzioni** e quindi scegliere **Progettazione visualizzazioni**.

2. Fare clic con il pulsante destro del mouse sulla finestra di progettazione della barra multifunzione e quindi **scegliere Esporta barra multifunzione in XML**.

     Visual Studio aggiunge un file XML della barra multifunzione e un file di codice XML della barra multifunzione al progetto.

3. Nella classe di codice Ribbon individuare i commenti che iniziano con `TODO:` .

4. Copiare il blocco di codice in questi commenti nella **classe ThisAddin**, **ThisWorkbook** o **ThisDocument,** a seconda del tipo di soluzione che si sta sviluppando.

     Questo codice consente all'Microsoft Office di individuare e caricare la barra multifunzione personalizzata. Per altre informazioni, vedere [Ribbon XML](../vsto/ribbon-xml.md).

5. Nella classe **ThisAddin**, **ThisWorkbook** o **ThisDocument** rimuovere il commento dal blocco di codice.

     Dopo aver decommentato il codice, dovrebbe essere simile all'esempio seguente. In questo esempio la classe Ribbon è denominata `MyRibbon` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb" id="Snippet1":::

6. Passare al file di codice XML della barra multifunzione e trovare `Ribbon Callbacks` l'area.

     Qui si scrivono metodi di callback per gestire le azioni dell'utente, ad esempio facendo clic su un pulsante.

7. Creare un metodo di callback per ogni gestore eventi scritto nel codice della finestra di progettazione della barra multifunzione.

8. Spostare tutto il codice del gestore eventi dai gestori eventi ai metodi di callback e modificare il codice in modo che funzioni con il modello di programmazione Ribbon extensibility (RibbonX).

     Per informazioni sulla scrittura di metodi di callback e sull'uso del modello di programmazione RibbonX, vedere [XML della barra multifunzione.](../vsto/ribbon-xml.md)

## <a name="see-also"></a>Vedi anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando il codice XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
