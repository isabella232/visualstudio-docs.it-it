---
title: 'CA2228: non spedire formati di risorse non rilasciati | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4adcae1c1cc616cdbcf5a7aa15342d221c2f4300
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540582"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Non specificare formati di risorse non rilasciati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un file di risorse è stato compilato utilizzando una versione di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] che non è attualmente supportata.

## <a name="rule-description"></a>Descrizione della regola
 I file di risorse compilati utilizzando versioni non [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] definitive di potrebbero non essere utilizzabili dalle versioni supportate del .NET Framework.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, compilare la risorsa usando una versione supportata di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] k.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.
