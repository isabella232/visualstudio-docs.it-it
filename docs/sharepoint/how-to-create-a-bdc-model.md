---
title: 'Procedura: Creare un modello BDC | Microsoft Docs'
description: Creare un modello BDC (Business Data Connectivity) usando il modello Visual Studio per quel tipo di elemento e quindi aggiungendo il modello a qualsiasi SharePoint progetto.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 4180821b1b37c2d9f0e9e2fcd5cadb8780c0a86c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106816"
---
# <a name="how-to-create-a-bdc-model"></a>Procedura: Creare un modello BDC

  È possibile creare un modello BDC (Business Data Connectivity) usando il modello per tale tipo di elemento e quindi aggiungendo il modello a qualsiasi SharePoint progetto. Per altre informazioni, vedere [Creare un modello di connettività dei dati aziendali.](../sharepoint/creating-a-business-data-connectivity-model.md) Per altre informazioni su come progettare il modello, vedere [Progettare un modello di connettività dei dati aziendali.](../sharepoint/designing-a-business-data-connectivity-model.md)

## <a name="to-create-a-bdc-project"></a>Per creare un progetto BDC

1. Sulla barra dei menu scegliere **File**  >  **Nuovo**  >  **Project**.
::: moniker range="=vs-2017"
   > [!NOTE]
   > Se l'IDE è impostato per l'uso Visual Basic di sviluppo, scegliere **Nuovo**  >  **file Project**.

  Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. In **Visual Basic** o **Visual C#** scegliere **Office/SharePoint**, SharePoint **Soluzioni**.

3. Nel riquadro **Modelli** scegliere l'SharePoint **2013 - Vuoto** Project e quindi scegliere il pulsante **OK.**

     Verrà **visualizzata SharePoint personalizzazione guidata** impostazioni.
::: moniker-end
::: moniker range=">=vs-2019"
2. Nella finestra **di dialogo Create a New Project** (Crea un nuovo Project) selezionare SharePoint Empty *Project** (SharePoint vuoto ) per la versione specifica SharePoint installata. Ad esempio, se è stata installata SharePoint 2019, selezionare il SharePoint **2019 - Vuoto Project 2019.**
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Se si vuole, modificare il nome del progetto e quindi scegliere **il pulsante** Crea.

::: moniker-end
4. Nella  pagina Specificare il sito e il livello di sicurezza per il debug specificare l'URL di un sito di SharePoint nel computer locale, scegliere il pulsante di opzione Distribuisci come soluzione **farm** e quindi scegliere il pulsante **Fine.**

     Il modello verrà testato nel SharePoint specificato.

    > [!IMPORTANT]
    > È necessario distribuire il progetto come soluzione farm perché i modelli BDC supportano solo soluzioni farm.

     Viene creato SharePoint progetto vuoto.

5. Nella barra dei menu scegliere **Project**  >  **Aggiungi nuovo elemento**.

6. Nella finestra **di dialogo Aggiungi nuovo** elemento scegliere il **Office/SharePoint** nodo.

7. Nell'elenco dei modelli SharePoint scegliere **Modello di connettività dei dati di business (solo soluzione farm).**

8. Nella casella **Nome** specificare un nome per il modello BDC e quindi scegliere il **pulsante** Aggiungi.

     Un **elemento del modello di connettività** dei dati di business viene aggiunto al progetto. Per impostazione predefinita, il modello viene visualizzato nella finestra di progettazione del data center virtuale. Per altre informazioni, vedere [Creare un modello di connettività dei dati aziendali.](../sharepoint/creating-a-business-data-connectivity-model.md)

## <a name="see-also"></a>Vedi anche

- [Creare un modello di connettività dei dati aziendali](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Procedura: Aggiungere un file di modello BDC esistente a un SharePoint progetto](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Procedura: Usare un file di risorse per specificare nomi, proprietà e autorizzazioni localizzati](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Procedura: Includere un assembly personalizzato in una funzionalità BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrazione dei dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
