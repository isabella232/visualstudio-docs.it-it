---
title: 'CA2228: Non fornire formati di risorse non rilasciati | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 84dc7c20f4109f7d66ed83b22fcec36dacc5eb3f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589678"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Non fornire formati di risorse non rilasciati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA2228: non fornire formati di risorse non rilasciati](https://docs.microsoft.com/visualstudio/code-quality/ca2228-do-not-ship-unreleased-resource-formats).

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un file di risorse è stato creato usando una versione del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] che non è attualmente supportato.

## <a name="rule-description"></a>Descrizione della regola
 File di risorse che sono stati compilati usando versioni non definitive del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] potrebbe non essere utilizzabili dalle versioni supportate di .NET Framework.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, generare la risorsa utilizzando una versione supportata del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]k.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.



