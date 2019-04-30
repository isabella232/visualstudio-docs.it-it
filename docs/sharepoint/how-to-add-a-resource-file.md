---
title: 'Procedura: Aggiungere un File di risorse | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: e7b8394d0c21ed5a45639e4dad5fe3695aaccc27
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439990"
---
# <a name="how-to-add-a-resource-file"></a>Procedura: Aggiungere un file di risorse
  I comandi per l'aggiunta di file di risorse è il menu di scelta rapida del nodo della soluzione e i nodi di funzionalità in Esplora soluzioni. Per altre informazioni, vedere [soluzioni SharePoint localizzazione](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Per aggiungere un file di risorse globali per una soluzione di SharePoint

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], aprire una soluzione di SharePoint.

2. Nelle **Esplora soluzioni**, scegliere un nodo di progetto SharePoint e quindi nella barra dei menu, scegliere **Project** > **Aggiungi nuovo elemento**.

3. Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere la **File di risorse globali** modello e quindi scegliere il **Add** pulsante.

   > [!NOTE]
   > Il modello di elemento di progetto di File di risorse globali viene visualizzata solo quando viene selezionato un elemento di progetto SharePoint.

4. Nel **Aggiungi risorsa** finestra di dialogo scegliere delle impostazioni cultura per il file di risorse, ad esempio inglese (Stati Uniti).

    Questo passaggio aggiunge un file di risorse globale per la soluzione nel formato, Resource_x_**.** <em>delle impostazioni cultura</em><strong>.</strong> RESX, ad esempio, *Resource1-US. resx*.

5. Quando la **Editor di risorse** viene aperto in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], aggiungere risorse al file di risorse.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Per aggiungere un file di risorse di funzionalità a una funzionalità di SharePoint

1. Se la soluzione di SharePoint non è già aperta in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], aprire la soluzione.

2. In **Esplora soluzioni**, aprire il menu di scelta rapida per il nome di una funzionalità inclusa la **funzionalità** nodo e quindi scegliere **Aggiungi risorsa funzionalità**.

     Questo passaggio aggiunge un file di risorse per la funzionalità nel formato _ResourceFileName_**.** _delle impostazioni cultura_**resx**, ad esempio *Feature1-US. resx*.

3. Quando la **Editor di risorse** viene aperto in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], aggiungere risorse al file di risorse.

## <a name="see-also"></a>Vedere anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
