---
title: 'Procedura: personalizzare una scheda incorporata'
description: Informazioni su come aggiungere gruppi e controlli a una scheda incorporata. Una scheda incorporata è una scheda già presente sulla barra multifunzione di un'applicazione Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 94cf4d256cafa03ee4604138f7233ff9fd3cf6c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953994"
---
# <a name="how-to-customize-a-built-in-tab"></a>Procedura: personalizzare una scheda incorporata
  È possibile aggiungere gruppi e controlli a una scheda incorporata. Una scheda incorporata è una scheda già presente sulla barra multifunzione di un'applicazione Microsoft Office. Ad esempio, la scheda **dati** è una scheda incorporata in Excel. Quando si crea un gruppo personalizzato, esso viene visualizzato per ultimo nella scheda, ma è possibile spostarlo in un punto qualsiasi della scheda.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> È possibile aggiungere gruppi in una scheda incorporata, ma non è possibile rimuovere gruppi incorporati da una scheda incorporata.

### <a name="to-add-groups-to-a-built-in-tab"></a>Per aggiungere gruppi in una scheda incorporata

1. Fare clic con il pulsante destro del mouse sul file di codice della barra multifunzione in **Esplora soluzioni**, quindi scegliere **Progettazione visualizzazioni**.

    > [!NOTE]
    > Se il file di codice della barra multifunzione non viene visualizzato in **Esplora soluzioni**, è necessario aggiungere un **elemento della barra multifunzione** al progetto. Vedere [procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. Fare clic con il pulsante destro del mouse su una scheda nella finestra di progettazione della barra multifunzione e quindi scegliere **Proprietà**

3. Nella finestra **Proprietà** espandere la proprietà **ControlID** , quindi impostare la proprietà **ControlIdType** su **Office**.

4. Impostare la proprietà **OfficeId** sull' *ID del controllo* della scheda incorporata che si desidera personalizzare.

     L'ID di controllo è il nome che identifica in modo univoco le schede, i gruppi e i controlli incorporati nelle applicazioni Microsoft Office.

     Per un elenco di ID di controllo, vedere [file della Guida di office 2010: identificatori di controllo dell'interfaccia utente di Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

5. Dalla scheda **controlli barra multifunzione di Office** della **casella degli strumenti** trascinare i gruppi nella scheda.

    > [!NOTE]
    > I gruppi incorporati non sono visualizzati nella finestra di progettazione. Pertanto, l'unico modo per determinare se si sta utilizzando una scheda incorporata consiste nell'esaminare la proprietà **ControlID** della scheda.

### <a name="to-position-groups-on-a-built-in-tab"></a>Per posizionare gruppi in una scheda incorporata

1. Selezionare un gruppo personalizzato nella finestra di progettazione della barra multifunzione.

2. Nella finestra **Proprietà** espandere la proprietà **position** .

3. Impostare la proprietà **PositionType** sul valore appropriato:

    - **BeforeOfficeId** posiziona il gruppo prima di un gruppo predefinito specificato.

    - **AfterOfficeId** posiziona il gruppo dopo un gruppo predefinito specificato.

4. Impostare la proprietà **OfficeId** sull'ID del controllo di un gruppo incorporato.

     Per un elenco di ID di controllo, vedere [file della Guida di office 2010: identificatori di controllo dell'interfaccia utente di Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

## <a name="see-also"></a>Vedi anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura dettagliata: creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura dettagliata: creare una scheda personalizzata usando il codice XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Procedura: modificare la posizione di una scheda nella barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Procedura: visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)
