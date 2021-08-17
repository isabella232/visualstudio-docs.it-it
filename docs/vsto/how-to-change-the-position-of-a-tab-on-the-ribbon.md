---
title: 'Procedura: Modificare la posizione di una scheda sulla barra multifunzione'
description: È possibile modificare l'ordine delle schede personalizzate in una barra multifunzione e posizionare le schede personalizzate prima o dopo una scheda incorporata nella barra multifunzione usando l'editor della raccolta schede.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 93ce719b8db2280029ad4302adb2afc1e08140de
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106341"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Procedura: Modificare la posizione di una scheda sulla barra multifunzione
  È possibile modificare l'ordine delle schede personalizzate in una barra multifunzione usando **l'Editor raccolta schede**. È possibile posizionare schede personalizzate prima o dopo una scheda incorporata sulla barra multifunzione. Una scheda incorporata è una scheda già presente nella barra multifunzione di un Microsoft Office app. Ad esempio, la **scheda** Dati è una scheda predefinita in Excel.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Per modificare l'ordine delle schede sulla barra multifunzione

1. Selezionare il file di codice della barra multifunzione (file *con estensione vb* o *cs)* in **Esplora soluzioni**.

2. Scegliere **Progettazione** dal menu **Visualizza**.

3. Fare clic con il pulsante destro del mouse sulla finestra di progettazione della barra multifunzione e quindi **scegliere Proprietà**.

4. Nella finestra **Proprietà** selezionare la proprietà **Schede** e quindi fare clic sul pulsante con i puntini di sospensione ( ASP.NET ![dei puntini di sospensione della finestra di progettazione per dispositivi mobili](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")).

     Verrà **visualizzato l'editor della raccolta** Schede.

5. Nell'elenco Membri dell'editor raccolta schede selezionare la scheda da spostare e fare clic sulle frecce su o giù per modificare l'ordine di tabulazione.  

### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Per posizionare una scheda prima o dopo una scheda incorporata sulla barra multifunzione

1. Nella finestra di progettazione della barra multifunzione selezionare una scheda personalizzata.

2. Nella finestra **Proprietà** espandere la **proprietà ControlId** e quindi assicurarsi che il valore della proprietà **ControlIdType** sia impostato su **Personalizzato.**

3. Nella finestra **Proprietà** espandere la **proprietà Posizione.**

4. Impostare la **proprietà PositionType** sul valore appropriato:

    - **BeforeOfficeId** posiziona il gruppo prima di una scheda incorporata specificata.

    - **AfterOfficeId** posiziona il gruppo dopo una scheda incorporata specificata.

5. Impostare la **proprietà OfficeId** sull'ID di controllo di una scheda predefinita.

     Per un elenco degli ID di controllo, vedere Office [2010 help files: Office fluent user interface control identifiers](https://www.microsoft.com/download/details.aspx?id=6627).

## <a name="see-also"></a>Vedi anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando il codice XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
