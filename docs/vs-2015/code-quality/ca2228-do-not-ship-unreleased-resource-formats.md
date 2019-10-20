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
ms.openlocfilehash: 9297ea0bb24eed54d0134a5f3c0fce87e6757adb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662878"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Non fornire formati di risorse non rilasciati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un file di risorse è stato compilato con una versione del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] attualmente non supportata.

## <a name="rule-description"></a>Descrizione della regola
 I file di risorse compilati utilizzando versioni non definitive del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] potrebbero non essere utilizzabili dalle versioni supportate del .NET Framework.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, compilare la risorsa usando una versione supportata del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]k.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.
