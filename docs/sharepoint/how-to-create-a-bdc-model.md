---
title: 'Procedura: Creare un modello di integrazione applicativa dei dati | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c01b8c54a762436f7bf76fd8186765a4fe1b9b6a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955620"
---
# <a name="how-to-create-a-bdc-model"></a>Procedura: Creare un modello di integrazione applicativa dei dati
  È possibile creare un modello di integrazione applicativa dei dati (BDC) usando il modello per tale tipo di elemento e quindi aggiungere il modello a qualsiasi progetto SharePoint. Per altre informazioni, vedere [creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md). Per altre informazioni su come progettare il modello, vedere [progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-bdc-project"></a>Per creare un progetto di integrazione applicativa dei dati  
  
1.  Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.  
  
    > [!NOTE]  
    >  Se l'IDE è configurato per usare le impostazioni di sviluppo di Visual Basic, scegli **File** > **nuovo progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  In presenza di una **Visual Basic** oppure **Visual c#**, scegliere **Office/SharePoint**, **soluzioni SharePoint**.  
  
3.  Nel **modelli** riquadro, scegliere il **SharePoint 2013 - progetto vuoto** elemento e quindi scegliere il **OK** pulsante.  
  
     Il **Personalizzazione guidata SharePoint** apre.  
  
4.  Nel **specificare il livello di sito e la sicurezza per il debug** pagina, specificare l'URL di un sito di SharePoint nel computer locale, scegliere il **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **Finish** pulsante.  
  
     Si testerà il modello nel sito di SharePoint specificato.  
  
    > [!IMPORTANT]  
    >  Poiché i modelli BDC supportano solo soluzioni farm, è necessario distribuire il progetto come soluzione farm.  
  
     Viene creato un progetto SharePoint vuoto.  
  
5.  Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.  
  
6.  Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere la **Office/SharePoint** nodo.  
  
7.  Nell'elenco dei modelli di SharePoint, scegliere **Business Data Connectivity Model (solo soluzione Farm)**.  
  
8.  Nel **Name** casella, specificare un nome per il modello di integrazione applicativa dei dati e quindi scegliere il **Add** pulsante.  
  
     Oggetto **Business Data Connectivity Model** elemento viene aggiunto al progetto. Per impostazione predefinita, il modello viene visualizzato nella finestra di progettazione integrazione applicativa dei dati. Per altre informazioni, vedere [creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="see-also"></a>Vedere anche
 [Creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Procedura: Aggiungere un file di modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Procedura: Usare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Procedura: Includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrazione di dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
