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
ms.openlocfilehash: b3c6298c2186b6a73b4a7ef441b5f4c42c90ff6a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231054"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Non specificare formati di risorse non rilasciati

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un file di risorse è stato compilato con una versione di .NET che non è attualmente supportata.

## <a name="rule-description"></a>Descrizione della regola

I file di risorse compilati con le versioni preliminari di .NET potrebbero non essere utilizzabili dalle versioni supportate di .NET.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, compilare la risorsa usando una versione supportata di .NET.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola.
