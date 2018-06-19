---
title: 'CA1814: Preferire matrici di matrici rispetto a matrici multidimensionali'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cbcf3cc6167cc98cb61380aa1ac54af5a291eb09
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915744"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: Preferire matrici di matrici rispetto a matrici multidimensionali
|||
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|Category|Microsoft.Performance|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un membro viene dichiarato come una matrice multidimensionale.

## <a name="rule-description"></a>Descrizione della regola
 Una matrice di matrici è una matrice i cui elementi sono costituiti da matrici. Poiché le matrici che costituiscono gli elementi possono presentare dimensioni diverse, la quantità di spazio inutilizzato sarà inferiore per alcuni insiemi di dati.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare la matrice multidimensionale in una matrice di matrici.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Escludere un avviso da questa regola se la matrice multidimensionale non causare uno spreco di spazio.

## <a name="example"></a>Esempio
 L'esempio seguente mostra le dichiarazioni per le matrici di matrici e multidimensionali.

 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-csharp[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]