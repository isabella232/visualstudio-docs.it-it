---
title: 'CA1501: Evitare ereditarietà eccessiva | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 05bafff1de36ed6560d2e75654a9d4c823dbae8d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240630"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: Evitare ereditarietà eccessiva
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|Category|Microsoft.Maintainability|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo si trova oltre il quarto livello di annidamento nella gerarchia di ereditarietà.

## <a name="rule-description"></a>Descrizione della regola
 Le gerarchie di tipi eccessivamente annidate possono comportare difficoltà di comprensione e gestione. Questa regola consente di limitare analysis alle gerarchie nello stesso modulo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, derivare il tipo da un tipo di base che è meno approfondito nella gerarchia di ereditarietà o eliminare alcuni dei tipi di base intermedi.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola. Tuttavia, il codice potrebbe essere più difficile da gestire. Si noti che, a seconda della visibilità dei tipi di base, la risoluzione delle violazioni di questa regola potrebbe creare le modifiche di rilievo. Ad esempio, la rimozione dei tipi di base pubblici è una modifica sostanziale.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/cs/FxCop.Maintainability.ExcessiveInheritance.cs#1)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/vb/FxCop.Maintainability.ExcessiveInheritance.vb#1)]



