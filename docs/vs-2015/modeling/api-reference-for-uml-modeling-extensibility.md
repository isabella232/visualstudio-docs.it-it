---
title: Riferimento API per l'estensibilità di modellazione UML | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: db042d59ce5f7363d9ed45e2baebbea45d3a0de4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528779"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>Riferimento API per l'estensibilità di modellazione UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [riferimento API per l'estendibilità di modellazione UML](https://docs.microsoft.com/visualstudio/modeling/api-reference-for-uml-modeling-extensibility).  
  
È possibile scrivere codice programma per leggere e modificare i modelli creati con Visual Studio. Il riferimento alle API fornisce informazioni sulle classi specifiche a questo scopo. Per altre informazioni e orientati alle attività, vedere gli argomenti in [modelli e diagrammi UML estendere](../modeling/extend-uml-models-and-diagrams.md). Per le versioni di Visual Studio che supportano i modelli UML, vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="assemblies"></a>Assembly  
  
|Assembly|Operazioni consentite|  
|--------------|--------------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces.dll|-Leggere e modificare gli elementi del modello quali IUseCase, IAssociation e così via.<br />-Spostarsi nelle relazioni tra gli elementi.<br /><br /> Gli spazi dei nomi e i tipi corrispondono a quelli definiti nella specifica UML.|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|: Consente di creare nuove istanze di elementi del modello<br />-Accedere e modificare le forme e diagrammi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Riferimento API per SDK di modellazione per Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)



