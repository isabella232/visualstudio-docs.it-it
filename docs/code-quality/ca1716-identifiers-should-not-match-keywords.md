---
title: 'CA1716: Gli identificatori non devono corrispondere a parole chiave'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b5ee844da2c04a1dd6eac6a7ca458957dd22a71
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550609"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Gli identificatori non devono corrispondere a parole chiave
|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un nome di uno spazio dei nomi, un tipo o un membro virtuale o di interfaccia corrisponde a una parola chiave riservata in un linguaggio di programmazione.

## <a name="rule-description"></a>Descrizione della regola
 Gli identificatori per spazi dei nomi, tipi e virtuali e i membri di interfaccia non devono corrispondere a parole chiave definite da linguaggi destinati a common language runtime. A seconda del linguaggio utilizzato e la parola chiave, le ambiguità e gli errori del compilatore possono rendere difficile da usare la libreria.

 Questa regola consente di controllare con parole chiave nelle seguenti lingue:

- Visual Basic

- C#

- C++/CLI

 Confronto tra maiuscole e minuscole viene usato per [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] parole chiave e il confronto tra maiuscole e minuscole viene usato per le altre lingue.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Selezionare un nome che non compare nell'elenco di parole chiave.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola se si sono convinti che l'identificatore sarà importante non confondere gli utenti dell'API e che sia utilizzabile in tutte le lingue disponibili nella libreria di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].