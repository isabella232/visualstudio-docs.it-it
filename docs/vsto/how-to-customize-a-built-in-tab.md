---
title: 'Procedura: personalizzare una scheda incorporata'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 30b4af116df218f3f778b9efa1e295fbadbad86a
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257267"
---
# <a name="how-to-customize-a-built-in-tab"></a>Procedura: personalizzare una scheda incorporata
  È possibile aggiungere gruppi e controlli in una scheda incorporata, cioè una scheda già presente sulla barra multifunzione di un'applicazione di Microsoft Office. Ad esempio, il **dati** scheda è una scheda incorporata in Excel. Quando si crea un gruppo personalizzato, esso viene visualizzato per ultimo nella scheda, ma è possibile spostarlo in un punto qualsiasi della scheda.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  È possibile aggiungere gruppi in una scheda incorporata, ma non è possibile rimuovere gruppi incorporati da una scheda incorporata.  
  
### <a name="to-add-groups-to-a-built-in-tab"></a>Per aggiungere gruppi in una scheda incorporata  
  
1.  Fare clic sul file di codice della barra multifunzione nel **Esplora soluzioni**, quindi fare clic su **Progettazione viste**.  
  
    > [!NOTE]  
    >  Se il file di codice della barra multifunzione non compare nel **Esplora soluzioni**, è necessario aggiungere un **elemento barra multifunzione** al progetto. Visualizzare [procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Fare doppio clic su qualsiasi scheda nella finestra di progettazione della barra multifunzione e quindi fare clic su **proprietà**.  
  
3.  Nel **delle proprietà** finestra, espandere il **ControlId** proprietà e quindi impostare il **ControlIdType** proprietà **Office**.  
  
4.  Impostare il **OfficeId** proprietà per il *ID controllo* della scheda incorporata che si desidera personalizzare.  
  
     L'ID di controllo è il nome che identifica in modo univoco le schede, i gruppi e i controlli incorporati nelle applicazioni Microsoft Office.  
  
     Per un elenco ID di controllo, vedere [i file della Guida di Office 2010: identificatori del controllo dell'interfaccia utente Office fluent Office](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
5.  Dal **controlli della barra multifunzione di Office** scheda della finestra di **della casella degli strumenti**, trascinare i gruppi della scheda.  
  
    > [!NOTE]  
    >  I gruppi incorporati non sono visualizzati nella finestra di progettazione. Pertanto, l'unico modo per determinare se si lavora con una scheda incorporata consiste nell'esaminare i **ControlId** proprietà della scheda.  
  
### <a name="to-position-groups-on-a-built-in-tab"></a>Per posizionare gruppi in una scheda incorporata  
  
1.  Selezionare un gruppo personalizzato nella finestra di progettazione della barra multifunzione.  
  
2.  Nel **delle proprietà** finestra, espandere il **posizione** proprietà.  
  
3.  Impostare il **PositionType** proprietà sul valore appropriato:  
  
    -   **BeforeOfficeId** posiziona il gruppo prima di un determinato gruppo incorporato.  
  
    -   **AfterOfficeId** posiziona il gruppo dopo un determinato gruppo incorporato.  
  
4.  Impostare il **OfficeId** proprietà ID di controllo di un gruppo incorporato.  
  
     Per un elenco ID di controllo, vedere [i file della Guida di Office 2010: identificatori del controllo dell'interfaccia utente Office fluent Office](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [XML della barra multifunzione](../vsto/ribbon-xml.md)   
 [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura dettagliata: Creare una scheda personalizzata utilizzando XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Procedura: modificare la posizione di una scheda della barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Procedura: il componente aggiuntivo Mostra errori dell'interfaccia utente](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  