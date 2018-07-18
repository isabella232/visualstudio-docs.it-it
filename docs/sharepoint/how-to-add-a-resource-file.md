---
title: 'Procedura: aggiungere un File di risorse | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3406e65ad96b93cd21890d61270c0ed989ad496c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756571"
---
# <a name="how-to-add-a-resource-file"></a>Procedura: aggiungere un file di risorse
  I comandi per l'aggiunta di file di risorse è il menu di scelta rapida del nodo della soluzione e i nodi di funzionalità in Esplora soluzioni. Per altre informazioni, vedere [soluzioni SharePoint localizzazione](../sharepoint/localizing-sharepoint-solutions.md).  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Per aggiungere un file di risorse globali per una soluzione di SharePoint  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], aprire una soluzione di SharePoint.  
  
2.  Nelle **Esplora soluzioni**, scegliere un nodo di progetto SharePoint e quindi nella barra dei menu, scegliere **Project** > **Aggiungi nuovo elemento**.  
  
3.  Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere la **File di risorse globali** modello e quindi scegliere il **Add** pulsante.  
  
    > [!NOTE]  
    >  Il modello di elemento di progetto di File di risorse globali viene visualizzata solo quando viene selezionato un elemento di progetto SharePoint.  
  
4.  Nel **Aggiungi risorsa** finestra di dialogo scegliere delle impostazioni cultura per il file di risorse, ad esempio inglese (Stati Uniti).  
  
     Questo passaggio aggiunge un file di risorse globale per la soluzione in formato Resource * x ***.*** le impostazioni cultura ***.** RESX, ad esempio, *Resource1-US. resx*.  
  
5.  Quando la **Editor di risorse** viene aperto in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], aggiungere risorse al file di risorse.  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Per aggiungere un file di risorse di funzionalità a una funzionalità di SharePoint  
  
1.  Se la soluzione di SharePoint non è già aperta in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], aprire la soluzione.  
  
2.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il nome di una funzionalità inclusa la **funzionalità** nodo e quindi scegliere **Aggiungi risorsa funzionalità**.  
  
     Questo passaggio aggiunge un file di risorse per la funzionalità nel formato * ResourceFileName ***.*** le impostazioni cultura ***.** RESX, ad esempio, *Feature1-US. resx*.  
  
3.  Quando la **Editor di risorse** viene aperto in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], aggiungere risorse al file di risorse.  
  
## <a name="see-also"></a>Vedere anche
 [Lo sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
 
