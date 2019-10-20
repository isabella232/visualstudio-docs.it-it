---
title: Riferimento API per l'estendibilità di modellazione UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e48bf723b8b1cb77cc1f7f4de9cfb562caccde84
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672801"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>Riferimento API per l'estensibilità di modellazione UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile scrivere codice programma per leggere e modificare i modelli creati con Visual Studio. Il riferimento alle API fornisce informazioni sulle classi specifiche a questo scopo. Per altre informazioni orientate alle attività, vedere gli argomenti in [estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md). Per individuare le versioni di Visual Studio che supportano i modelli UML, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="assemblies"></a>Assembly

|Assembly|Operazioni consentite|
|--------------|--------------------------------|
|Microsoft.VisualStudio.Uml.Interfaces.dll|-Leggere e modificare gli elementi del modello, ad esempio IUseCase, IAssociation e così via.<br />-Esplora le relazioni tra gli elementi.<br /><br /> Gli spazi dei nomi e i tipi corrispondono a quelli definiti nella specifica UML.|
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|-Crea nuove istanze di elementi del modello<br />-Accedere e modificare forme e diagrammi.|

## <a name="see-also"></a>Vedere anche
 [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md) [riferimento API per l'SDK di modellazione per Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
