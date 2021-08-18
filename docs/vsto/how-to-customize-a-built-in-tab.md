---
title: 'Procedura: Personalizzare una scheda incorporata'
description: Informazioni su come aggiungere gruppi e controlli a una scheda incorporata. Una scheda incorporata è una scheda già presente nella barra multifunzione di un'Microsoft Office applicazione.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ea01db137d7c1f6144f43e84f901e92702815fdf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046880"
---
# <a name="how-to-customize-a-built-in-tab"></a>Procedura: Personalizzare una scheda incorporata
  È possibile aggiungere gruppi e controlli a una scheda incorporata. Una scheda incorporata è una scheda già presente nella barra multifunzione di un'Microsoft Office applicazione. Ad esempio, la **scheda** Dati è una scheda predefinita in Excel. Quando si crea un gruppo personalizzato, esso viene visualizzato per ultimo nella scheda, ma è possibile spostarlo in un punto qualsiasi della scheda.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> È possibile aggiungere gruppi in una scheda incorporata, ma non è possibile rimuovere gruppi incorporati da una scheda incorporata.

### <a name="to-add-groups-to-a-built-in-tab"></a>Per aggiungere gruppi in una scheda incorporata

1. Fare clic con il pulsante destro del mouse sul file di codice della **barra multifunzione Esplora soluzioni** e quindi scegliere **Progettazione visualizzazioni**.

    > [!NOTE]
    > Se il file di codice della barra multifunzione non viene **visualizzato** Esplora soluzioni , è necessario aggiungere **un** elemento Barra multifunzione al progetto. Vedere [Procedura: Iniziare a personalizzare la barra multifunzione.](../vsto/how-to-get-started-customizing-the-ribbon.md)

2. Fare clic con il pulsante destro del mouse su una scheda qualsiasi nella finestra di progettazione della barra multifunzione e quindi scegliere **Proprietà**.

3. Nella finestra **Proprietà** espandere la **proprietà ControlId** e quindi impostare la **proprietà ControlIdType** **su Office**.

4. Impostare la **proprietà OfficeId** sull'ID controllo della scheda predefinita che si vuole personalizzare. 

     L'ID di controllo è il nome che identifica in modo univoco le schede, i gruppi e i controlli incorporati nelle applicazioni Microsoft Office.

     Per un elenco degli ID di controllo, vedere Office [2010 help files: Office fluent user interface control identifiers](https://www.microsoft.com/download/details.aspx?id=6627).

5. Dalla scheda **Office Controlli barra** multifunzione della Casella degli **strumenti** trascinare i gruppi nella scheda .

    > [!NOTE]
    > I gruppi incorporati non sono visualizzati nella finestra di progettazione. Pertanto, l'unico modo per determinare se si sta lavorando con una scheda predefinita è esaminare la **proprietà ControlId** della scheda.

### <a name="to-position-groups-on-a-built-in-tab"></a>Per posizionare gruppi in una scheda incorporata

1. Selezionare un gruppo personalizzato nella finestra di progettazione della barra multifunzione.

2. Nella finestra **Proprietà** espandere la **proprietà Posizione.**

3. Impostare la **proprietà PositionType** sul valore appropriato:

    - **BeforeOfficeId** posiziona il gruppo prima di un gruppo predefinito specificato.

    - **AfterOfficeId** posiziona il gruppo dopo un gruppo predefinito specificato.

4. Impostare la **proprietà OfficeId** sull'ID controllo di un gruppo predefinito.

     Per un elenco degli ID di controllo, vedere Office [2010 help files: Office fluent user interface control identifiers](https://www.microsoft.com/download/details.aspx?id=6627).

## <a name="see-also"></a>Vedi anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando il codice XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Procedura: Iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Procedura: Modificare la posizione di una scheda sulla barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Procedura: Aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Procedura: Visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)
