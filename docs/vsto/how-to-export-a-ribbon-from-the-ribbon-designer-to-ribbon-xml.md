---
title: 'Procedura: Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione XML della barra multifunzione'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 6b9908b906a780839da335ce38af5b0d927632bc
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596516"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Procedura: Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione XML della barra multifunzione
  Il **sulla barra multifunzione (finestra di progettazione visiva)** elemento non supporta tutti i possibili tipi di personalizzazione della barra multifunzione. Per personalizzare la barra multifunzione in modi avanzati, è possibile esportare la barra multifunzione dalla finestra di progettazione XML della barra multifunzione e modificare direttamente il file XML.

> [!NOTE]
>  Non tutti i valori delle proprietà visualizzate nel file XML della barra multifunzione. Per altre informazioni, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Per esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione in XML della barra multifunzione

1.  Fare clic sul file di codice della barra multifunzione nel **Esplora soluzioni**, quindi fare clic su **Progettazione viste**.

2.  Fare doppio clic su finestra di progettazione della barra multifunzione e quindi fare clic su **Esporta barra multifunzione in XML**.

     Visual Studio aggiunge un file XML della barra multifunzione e un file di codice XML della barra multifunzione al progetto.

3.  Nella classe del codice della barra multifunzione, individuare i commenti che iniziano con `TODO:`.

4.  Copiare il blocco di codice in questi commenti per la **ThisAddin**, **ThisWorkbook**, o **ThisDocument** classe, a seconda di quale tipo di soluzione si sta sviluppando.

     Questo codice consente all'applicazione di Microsoft Office di individuare e caricare la barra multifunzione personalizzata. Per altre informazioni, vedere [Ribbon XML](../vsto/ribbon-xml.md).

5.  Nel **ThisAddin**, **ThisWorkbook**, o **ThisDocument** di classi, rimuovere il commento del blocco di codice.

     Dopo che è rimuovere il commento nel codice, dovrebbe essere simile al seguente. In questo esempio viene chiamata la classe Ribbon `MyRibbon`.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6.  Passare al file di codice XML della barra multifunzione e cercare il `Ribbon Callbacks` area.

     Si tratta in cui scrivere i metodi di callback per gestire le azioni utente, ad esempio la selezione di un pulsante.

7.  Creare un metodo di callback per ogni gestore eventi che è stata scritta nel codice di progettazione della barra multifunzione.

8.  Spostare tutto il codice del gestore eventi dai gestori eventi per i metodi di callback e modificare il codice per lavorare con il Ribbon extensibility (RibbonX) nel modello di programmazione.

     Per informazioni sulla scrittura di metodi di callback e utilizzando il modello di programmazione di RibbonX, vedere [XML della barra multifunzione](../vsto/ribbon-xml.md).

## <a name="see-also"></a>Vedere anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura dettagliata: Creare una scheda personalizzata utilizzando XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
