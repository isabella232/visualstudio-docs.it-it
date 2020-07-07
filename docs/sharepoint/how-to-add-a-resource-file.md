---
title: 'Procedura: aggiungere un file di risorse | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 657eb473adcff40a62d2fc9b09518ebe8135eeb4
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015176"
---
# <a name="how-to-add-a-resource-file"></a>Procedura: aggiungere un file di risorse
  I comandi per l'aggiunta di file di risorse sono presenti nel menu di scelta rapida del nodo della soluzione e dei nodi della funzionalità in Esplora soluzioni. Per ulteriori informazioni, vedere [localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Per aggiungere un file di risorse globale a una soluzione SharePoint

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aprire una soluzione di SharePoint.

2. In **Esplora soluzioni**scegliere un nodo di progetto SharePoint, quindi nella barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

3. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere il modello **file di risorse globali** , quindi scegliere il pulsante **Aggiungi** .

   > [!NOTE]
   > Il modello di elemento di progetto file di risorse globali viene visualizzato solo quando è selezionato un elemento del progetto SharePoint.

4. Nella finestra di dialogo **Aggiungi risorsa** scegliere le impostazioni cultura per il file di risorse, ad esempio inglese (Stati Uniti).

    Questo passaggio aggiunge un file di risorse globale alla soluzione nel formato Resource_x_**.** <em>impostazioni cultura</em><strong>.</strong> resx, ad esempio, *Resource1. en-US. resx*.

5. Quando si apre l' **editor di risorse** [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , aggiungere le risorse al file di risorse.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Per aggiungere un file di risorse della funzionalità a una funzionalità di SharePoint

1. Se la soluzione SharePoint non è già aperta in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , aprire la soluzione.

2. In **Esplora soluzioni**aprire il menu di scelta rapida per il nome di una funzionalità nel nodo **funzionalità** , quindi scegliere **Aggiungi risorsa funzionalità**.

     Questo passaggio aggiunge un file di risorse alla funzionalità nel formato _resourceFileName_**.** _culture_**. resx**, ad esempio, *Feature1. en-US. resx*.

3. Quando si apre l' **editor di risorse** [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , aggiungere le risorse al file di risorse.

## <a name="see-also"></a>Vedere anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
