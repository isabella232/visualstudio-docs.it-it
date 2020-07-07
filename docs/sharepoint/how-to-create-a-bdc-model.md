---
title: 'Procedura: creare un modello di integrazione applicativa dei dati | Microsoft Docs'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 139da31ced1d32def450a1dc176ca241b0c4677f
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014539"
---
# <a name="how-to-create-a-bdc-model"></a>Procedura: creare un modello di integrazione applicativa dei dati
  È possibile creare un modello di integrazione applicativa dei dati utilizzando il modello per quel tipo di elemento e quindi aggiungendo il modello a qualsiasi progetto SharePoint. Per altre informazioni, vedere [creare un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md). Per ulteriori informazioni sulla progettazione del modello, vedere [progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-bdc-project"></a>Per creare un progetto BDC

1. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto**.

    > [!NOTE]
    > Se l'IDE è configurato per usare Visual Basic impostazioni di sviluppo, scegliere **file**  >  **nuovo progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. In **Visual Basic** o **Visual C#** scegliere **Office/SharePoint**, **soluzioni SharePoint**.

3. Nel riquadro **modelli** scegliere l'elemento di **progetto SharePoint 2013-Empty** , quindi scegliere il pulsante **OK** .

     Verrà visualizzata la **procedura guidata di personalizzazione di SharePoint** .

4. Nella pagina **specificare il sito e il livello di sicurezza per il debug** specificare l'URL di un sito di SharePoint nel computer locale, scegliere il pulsante di opzione **Distribuisci come soluzione farm** , quindi scegliere il pulsante **fine** .

     Il modello viene testato nel sito di SharePoint specificato.

    > [!IMPORTANT]
    > È necessario distribuire il progetto come soluzione farm perché i modelli di integrazione applicativa dei dati supportano solo le soluzioni farm.

     Viene creato un progetto SharePoint vuoto.

5. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

6. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere il nodo **Office/SharePoint** .

7. Nell'elenco dei modelli di SharePoint scegliere **modello di integrazione applicativa dei dati (solo soluzione farm)**.

8. Nella casella **nome** specificare un nome per il modello di integrazione applicativa dei dati, quindi scegliere il pulsante **Aggiungi** .

     Al progetto viene aggiunto un elemento del **modello di integrazione applicativa dei dati** . Per impostazione predefinita, il modello viene visualizzato nella finestra di progettazione BDC. Per altre informazioni, vedere [creare un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="see-also"></a>Vedere anche
- [Creare un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Procedura: aggiungere un file modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Procedura: usare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Procedura: includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
