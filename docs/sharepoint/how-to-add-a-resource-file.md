---
title: 'Procedura: Aggiungere un file di risorse | Microsoft Docs'
description: Aggiungere un file di risorse in Visual Studio, usando i comandi del menu di scelta rapida del nodo della soluzione e dei nodi delle funzionalità in Esplora soluzioni.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: b11fdbdda72f1929afc1f5d2726332246b312d07
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625145"
---
# <a name="how-to-add-a-resource-file"></a>Procedura: Aggiungere un file di risorse
  I comandi per l'aggiunta di file di risorse sono disponibili nel menu di scelta rapida del nodo della soluzione e dei nodi di funzionalità in Esplora soluzioni. Per altre informazioni, vedere [Localizzazione di SharePoint soluzioni](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Per aggiungere un file di risorse globale a una soluzione SharePoint globale

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aprire una soluzione SharePoint predefinita.

2. In **Esplora soluzioni** scegliere un nodo SharePoint progetto e quindi, sulla barra dei menu, scegliere Project  >  **Aggiungi nuovo elemento**.

3. Nella finestra **di dialogo Aggiungi nuovo** elemento scegliere il modello File di **risorse** globali e quindi scegliere il **pulsante** Aggiungi.

   > [!NOTE]
   > Il modello di elemento di progetto File di risorse globali viene visualizzato solo quando SharePoint selezionato un elemento di progetto.

4. Nella finestra **di dialogo Aggiungi** risorsa scegliere le impostazioni cultura per il file di risorse, ad esempio Inglese (Stati Uniti).

    Questo passaggio aggiunge un file di risorse globale alla soluzione nel formato Resource_x_ **.** <em>culture</em><strong>.</strong> resx, ad *esempio, Resource1.en-US.resx*.

5. Quando si **apre l'Editor** risorse in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , aggiungere risorse al file di risorse.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Per aggiungere un file di risorse della funzionalità a una SharePoint funzionalità

1. Se la SharePoint non è già aperta in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , aprire la soluzione.

2. In **Esplora soluzioni** aprire il menu di scelta rapida per  il nome di una funzionalità nel nodo Funzionalità e quindi scegliere **Aggiungi risorsa funzionalità**.

     Questo passaggio aggiunge un file di risorse alla funzionalità nel formato _ResourceFileName_**.** _culture_**.resx,** ad esempio *Feature1.en-US.resx*.

3. Quando si **apre l'Editor** risorse in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , aggiungere risorse al file di risorse.

## <a name="see-also"></a>Vedi anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
