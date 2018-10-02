---
title: 'CA1716: Gli identificatori non devono corrispondere a parole chiave | Microsoft Docs'
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
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c1a3affbecf7a39ee323fd64bc8a56d92e8a4d5e
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589162"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Gli identificatori non devono corrispondere a parole chiave
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1716: gli identificatori non devono corrispondere a parole chiave](https://docs.microsoft.com/visualstudio/code-quality/ca1716-identifiers-should-not-match-keywords).

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

-   Visual Basic

-   C#

-   C++/CLI

 Confronto tra maiuscole e minuscole viene usato per [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] parole chiave e il confronto tra maiuscole e minuscole viene usato per le altre lingue.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Selezionare un nome che non compare nell'elenco di parole chiave.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se si sono convinti che l'identificatore sarà importante non confondere gli utenti dell'API e che sia utilizzabile in tutte le lingue disponibili nella libreria di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].



