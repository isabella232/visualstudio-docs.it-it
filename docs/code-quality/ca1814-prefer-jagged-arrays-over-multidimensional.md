---
title: 'CA1814: Preferire matrici di matrici rispetto a matrici multidimensionali'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2dca4a038dcd5809863037daf7a96811fb60df05
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233570"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: Preferire matrici di matrici rispetto a matrici multidimensionali

|||
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|Category|Microsoft.Performance|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un membro viene dichiarato come matrice multidimensionale.

## <a name="rule-description"></a>Descrizione della regola
Una matrice di matrici è una matrice i cui elementi sono costituiti da matrici. Poiché le matrici che costituiscono gli elementi possono presentare dimensioni diverse, la quantità di spazio inutilizzato sarà inferiore per alcuni insiemi di dati.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, modificare la matrice multidimensionale in una matrice di matrici.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Eliminare un avviso da questa regola se la matrice multidimensionale non spreca spazio.

## <a name="example"></a>Esempio
Nell'esempio seguente vengono illustrate le dichiarazioni per matrici frastagliate e multidimensionali.

[!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
[!code-csharp[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]