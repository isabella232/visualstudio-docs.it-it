---
title: 'CA2228: Non specificare formati di risorse non rilasciati'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f8a672056c8663c2e27ec730e542083aee9738f
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714975"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Non specificare formati di risorse non rilasciati

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un file di risorse è stato creato utilizzando una versione di .NET che non è attualmente supportato.

## <a name="rule-description"></a>Descrizione della regola

File di risorse che sono stati compilati usando versioni non definitive di .NET potrebbero non essere utilizzabili dalle versioni supportate di .NET.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, generare la risorsa utilizzando una versione supportata di .NET.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.
