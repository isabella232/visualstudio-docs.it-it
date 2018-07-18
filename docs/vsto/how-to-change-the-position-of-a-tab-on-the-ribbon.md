---
title: 'Procedura: modificare la posizione di una scheda della barra multifunzione'
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 08bbdf81023be466d30e49215fc0dbe1d3812f20
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255389"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Procedura: modificare la posizione di una scheda della barra multifunzione
  È possibile modificare l'ordine delle schede personalizzate in una barra multifunzione usando il **Editor della raccolta Tab**. È possibile posizionare le schede personalizzate prima o dopo una scheda incorporata nella barra multifunzione. Una scheda incorporata rappresenta una scheda già presente sulla barra multifunzione di un'applicazione Microsoft Office. Ad esempio, il **dati** scheda è una scheda incorporata in Excel.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Per modificare l'ordine delle schede della barra multifunzione  
  
1.  Selezionare il file di codice della barra multifunzione (*vb* oppure *cs* file) in **Esplora**.  
  
2.  Nel **View** menu, fare clic su **progettazione**.  
  
3.  Fare doppio clic su finestra di progettazione della barra multifunzione e quindi fare clic su **proprietà**.  
  
4.  Nel **delle proprietà** finestra, seleziona la **schede** proprietà e quindi fare clic sul pulsante con puntini di sospensione (![ellisse della finestra di progettazione mobile ASP.NET](../sharepoint/media/mwellipsis.gif "ASP.NET per dispositivi mobili Ellisse progettazione")).  
  
     Il **Editor della raccolta Tab** viene visualizzata.  
  
5.  Nel **Editor della raccolta Tab**, nella **membri** elencare, selezionare la scheda che si desidera spostare e fare clic sulla freccia o freccia giù per modificare l'ordine di tabulazione.  
  
### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Per posizionare una scheda prima o dopo una scheda incorporata nella barra multifunzione  
  
1.  Nella finestra di progettazione della barra multifunzione, selezionare una scheda personalizzata.  
  
2.  Nel **delle proprietà** finestra, espandere il **ControlId** proprietà e quindi verificare che il valore del **ControlIdType** è impostata su **Custom**.  
  
3.  Nel **delle proprietà** finestra, espandere il **posizione** proprietà.  
  
4.  Impostare il **PositionType** proprietà sul valore appropriato:  
  
    -   **BeforeOfficeId** posiziona il gruppo prima di una scheda incorporata specificata.  
  
    -   **AfterOfficeId** posiziona il gruppo dopo una scheda incorporata specificata.  
  
5.  Impostare il **OfficeId** proprietà ID di controllo di una scheda incorporata.  
  
     Per un elenco ID di controllo, vedere [i file della Guida di Office 2010: identificatori del controllo dell'interfaccia utente Office fluent Office](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [XML della barra multifunzione](../vsto/ribbon-xml.md)   
 [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura dettagliata: Creare una scheda personalizzata utilizzando XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  