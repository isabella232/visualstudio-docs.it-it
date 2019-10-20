---
title: 'CA2132: i costruttori predefiniti devono essere critici almeno come i costruttori predefiniti del tipo di base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ae271b116b372d4ae732d97ff3f9651ff9db426
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643304"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: I costruttori predefiniti devono essere Critical almeno come i costruttori predefiniti del tipo base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

> [!NOTE]
> Questo avviso viene applicato solo al codice che esegue CoreCLR (la versione di CLR specifica per le applicazioni Web Silverlight).

## <a name="cause"></a>Causa
 L'attributo Transparency del costruttore predefinito di una classe derivata non è critico come la trasparenza della classe base.

## <a name="rule-description"></a>Descrizione della regola
 I tipi e i membri con <xref:System.Security.SecurityCriticalAttribute> non possono essere usati dal codice dell'applicazione Silverlight. I tipi e i membri critici per la sicurezza possono essere usati solo da codice attendibile nella libreria di classi .NET Framework per Silverlight. Poiché una costruzione pubblica o protetta in una classe derivata deve disporre della trasparenza uguale o superiore alla classe di base, una classe in un'applicazione non può essere derivata da una classe contrassegnata come SecurityCritical.

 Per il codice di piattaforma CoreCLR, se un tipo di base ha un costruttore predefinito non trasparente pubblico o protetto, il tipo derivato deve rispettare le regole di ereditarietà predefinite del costruttore. Il tipo derivato deve avere anche un costruttore predefinito e il costruttore deve essere almeno come un costruttore predefinito critico del tipo di base.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere la violazione, rimuovere il tipo o non derivare da un tipo non trasparente di sicurezza.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare gli avvisi da questa regola. Le violazioni di questa regola da parte del codice dell'applicazione comporteranno la reimpostazione del CoreCLR per il caricamento del tipo con un <xref:System.TypeLoadException>.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency/cs/ca2132 - defaultconstructorsmusthaveconsistenttransparency.cs#1)]

### <a name="comments"></a>Comments
