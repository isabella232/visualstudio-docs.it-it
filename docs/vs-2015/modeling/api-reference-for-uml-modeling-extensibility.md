---
title: Riferimento API per l'estensibilità di modellazione UML | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dff485db59f418fe05cd586335b6f9ceae153428
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785040"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>Riferimento API per l'estensibilità di modellazione UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile scrivere codice programma per leggere e modificare i modelli creati con Visual Studio. Il riferimento alle API fornisce informazioni sulle classi specifiche a questo scopo. Per altre informazioni e orientati alle attività, vedere gli argomenti in [modelli e diagrammi UML estendere](../modeling/extend-uml-models-and-diagrams.md). Per individuare le versioni di Visual Studio che supportano i modelli UML, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="assemblies"></a>Assembly  
  
|Assembly|Operazioni consentite|  
|--------------|--------------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces.dll|-Leggere e modificare gli elementi del modello quali IUseCase, IAssociation e così via.<br />-Spostarsi nelle relazioni tra gli elementi.<br /><br /> Gli spazi dei nomi e i tipi corrispondono a quelli definiti nella specifica UML.|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|: Consente di creare nuove istanze di elementi del modello<br />-Accedere e modificare le forme e diagrammi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Riferimento API per SDK di modellazione per Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)



