---
title: 'CA2228: Non fornire formati di risorse non rilasciati'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2823933e4792dd6127ffbd4b1bfe5dfe1b71a0c
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547549"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Non fornire formati di risorse non rilasciati
|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un file di risorse è stato creato usando una versione del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] che non è attualmente supportato.

## <a name="rule-description"></a>Descrizione della regola
 File di risorse che sono stati compilati usando versioni non definitive del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] potrebbe non essere utilizzabili dalle versioni supportate di .NET Framework.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, generare la risorsa utilizzando una versione supportata del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]k.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.