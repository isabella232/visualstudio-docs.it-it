---
title: 'CA2228: Non fornire formati di risorse non rilasciati | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2e49953a95da10653cd29132e003fa36de5b8d4c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968787"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Non specificare formati di risorse non rilasciati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
