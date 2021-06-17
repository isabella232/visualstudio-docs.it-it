---
title: 'Procedura: Creare un modello BDC | Microsoft Docs'
description: Creare un modello BDC (Business Data Connectivity) usando il modello Visual Studio per questo tipo di elemento e quindi aggiungendo il modello a qualsiasi progetto SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd5184f87cf3895e1519a91e6f7e6661702f1181
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112407"
---
# <a name="how-to-create-a-bdc-model"></a>Procedura: Creare un modello BDC

  È possibile creare un modello BDC (Business Data Connectivity) usando il modello per tale tipo di elemento e quindi aggiungendo il modello a qualsiasi progetto SharePoint. Per altre informazioni, vedere [Creare un modello di connettività dati business](../sharepoint/creating-a-business-data-connectivity-model.md). Per altre informazioni su come progettare il modello, vedere Progettare un modello di [connettività dati business](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="to-create-a-bdc-project"></a>Per creare un progetto BDC

1. Sulla barra dei menu scegliere **File**  >  **nuovo**  >  **progetto**.
::: moniker range="=vs-2017"
   > [!NOTE]
   > Se l'IDE è impostato per l'Visual Basic di sviluppo, scegliere **File**  >  **nuovo progetto**.

  Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. In **Visual Basic** o **Visual C#** scegliere **Office/SharePoint**, **Soluzioni SharePoint**.

3. Nel riquadro **Modelli** scegliere l'elemento **SharePoint 2013 - Progetto** vuoto e quindi scegliere **OK.**

     Verrà **visualizzata la Personalizzazione guidata SharePoint.**
::: moniker-end
::: moniker range=">=vs-2019"
2. Nella finestra **di dialogo Crea un nuovo** progetto selezionare il progetto Vuoto di *SharePoint** per la versione specifica di SharePoint installata. Ad esempio, se si ha l'installazione di SharePoint 2019, selezionare il modello **SharePoint 2019 - Progetto** vuoto.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Modificare il nome del progetto, se necessario, e quindi scegliere il **pulsante** Crea.

::: moniker-end
4. Nella pagina **Specificare** il sito e il livello di sicurezza per il debug specificare l'URL di un sito di SharePoint nel computer locale, scegliere il pulsante di opzione Distribuisci come soluzione **farm** e quindi scegliere il **pulsante** Fine.

     Il modello verrà testato nel sito di SharePoint specificato.

    > [!IMPORTANT]
    > È necessario distribuire il progetto come soluzione farm perché i modelli BDC supportano solo soluzioni farm.

     Viene creato un progetto SharePoint vuoto.

5. Sulla barra dei menu scegliere **Progetto**  >  **Aggiungi nuovo elemento**.

6. Nella finestra **di dialogo Aggiungi nuovo** elemento scegliere il nodo **Office/SharePoint.**

7. Nell'elenco dei modelli di SharePoint scegliere **Modello di connettività dati business (solo soluzione farm).**

8. Nella casella **Nome** specificare un nome per il modello BDC e quindi scegliere il **pulsante** Aggiungi.

     Al **progetto viene** aggiunto un elemento Modello di connettività dati business. Per impostazione predefinita, il modello viene visualizzato nella finestra di progettazione del data center BDC. Per altre informazioni, vedere [Creare un modello di connettività dati business](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="see-also"></a>Vedi anche

- [Creare un modello di connettività dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Procedura: Aggiungere un file di modello BDC esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Procedura: Usare un file di risorse per specificare nomi, proprietà e autorizzazioni localizzati](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Procedura: Includere un assembly personalizzato in una funzionalità BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrazione dei dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
