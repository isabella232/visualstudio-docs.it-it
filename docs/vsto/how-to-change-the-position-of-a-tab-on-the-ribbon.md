---
title: 'Procedura: modificare la posizione di una scheda nella barra multifunzione'
description: È possibile modificare l'ordine delle schede personalizzate su una barra multifunzione e posizionare le schede personalizzate prima o dopo una scheda incorporata nella barra multifunzione usando l'editor della raccolta di schede.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 21fd7f17f7a990f95ce5c8b781e85807a10608c4
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846766"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Procedura: modificare la posizione di una scheda nella barra multifunzione
  È possibile modificare l'ordine delle schede personalizzate su una barra multifunzione usando l' **Editor della raccolta di schede**. È possibile posizionare le schede personalizzate prima o dopo una scheda incorporata nella barra multifunzione. Una scheda incorporata è una scheda già presente sulla barra multifunzione di un'applicazione Microsoft Office. Ad esempio, la scheda **dati** è una scheda incorporata in Excel.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Per modificare l'ordine delle schede sulla barra multifunzione

1. Selezionare il file di codice della barra multifunzione (file con *estensione VB* o *cs* ) in **Esplora soluzioni**.

2. Scegliere **finestra di progettazione** dal menu **Visualizza** .

3. Fare clic con il pulsante destro del mouse sulla finestra di progettazione Ribbon, quindi scegliere **Proprietà**.

4. Nella finestra **Proprietà** selezionare la proprietà **Tabs** , quindi fare clic sul pulsante con i puntini di sospensione (![ASP.NET Mobile Designer ellisse](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")).

     Viene visualizzato l' **Editor della raccolta di schede** .

5. Nell'elenco **membri** dell' **Editor della raccolta di schede** selezionare la scheda che si desidera spostare e fare clic sulle frecce su o giù per modificare l'ordine di tabulazione.

### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Per posizionare una scheda prima o dopo una scheda incorporata nella barra multifunzione

1. Nella finestra di progettazione della barra multifunzione selezionare una scheda personalizzata.

2. Nella finestra **Proprietà** espandere la proprietà **ControlID** , quindi verificare che il valore della proprietà **ControlIdType** sia impostato su **Custom**.

3. Nella finestra **Proprietà** espandere la proprietà **position** .

4. Impostare la proprietà **PositionType** sul valore appropriato:

    - **BeforeOfficeId** posiziona il gruppo prima di una scheda incorporata specificata.

    - **AfterOfficeId** posiziona il gruppo dopo una scheda incorporata specificata.

5. Impostare la proprietà **OfficeId** sull'ID del controllo di una scheda incorporata.

     Per un elenco di ID di controllo, vedere [file della Guida di office 2010: identificatori di controllo dell'interfaccia utente di Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

## <a name="see-also"></a>Vedi anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura dettagliata: creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura dettagliata: creare una scheda personalizzata usando il codice XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
