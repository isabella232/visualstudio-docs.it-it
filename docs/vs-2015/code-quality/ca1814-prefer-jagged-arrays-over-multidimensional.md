---
title: 'CA1814: Preferire matrici di matrici tramite multidimensionali | Microsoft Docs'
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
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 290e2f736e347aef68296207048f8ba5787234cc
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589153"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: Preferire matrici di matrici rispetto a matrici multidimensionali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1814: Preferire matrici di matrici tramite multidimensionali](https://docs.microsoft.com/visualstudio/code-quality/ca1814-prefer-jagged-arrays-over-multidimensional).

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
 Eliminare un avviso da questa regola se la matrice multidimensionale non spreco di spazio.

## <a name="example"></a>Esempio
 L'esempio seguente illustra le dichiarazioni per matrici e matrici multidimensionali.

 [!code-csharp[FxCop.Performance.JaggedArrays#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/cs/FxCop.Performance.JaggedArrays.cs#1)]
 [!code-vb[FxCop.Performance.JaggedArrays#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/vb/FxCop.Performance.JaggedArrays.vb#1)]



