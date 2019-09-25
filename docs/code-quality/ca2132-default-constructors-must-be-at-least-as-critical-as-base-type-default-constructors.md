---
title: 'CA2132: I costruttori predefiniti devono essere Critical almeno come i costruttori predefiniti del tipo base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c5ca98219444515d01baf670489120238cb8dda
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232334"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: I costruttori predefiniti devono essere Critical almeno come i costruttori predefiniti del tipo base

|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|Category|Microsoft.Security|
|Modifica|Interruzione|

> [!NOTE]
> Questo avviso viene applicato solo al codice che esegue CoreCLR (la versione di CLR specifica per le applicazioni Web Silverlight).

## <a name="cause"></a>Causa

L'attributo Transparency del costruttore predefinito di una classe derivata non è critico come la trasparenza della classe base.

## <a name="rule-description"></a>Descrizione della regola

I <xref:System.Security.SecurityCriticalAttribute> tipi e i membri che non possono essere usati dal codice dell'applicazione Silverlight. I tipi e i membri critici per la sicurezza possono essere usati solo da codice attendibile nella libreria di classi .NET Framework per Silverlight. Poiché una costruzione pubblica o protetta in una classe derivata deve disporre della trasparenza uguale o superiore alla classe di base, una classe in un'applicazione non può essere derivata da una classe contrassegnata come SecurityCritical.

Per il codice di piattaforma CoreCLR, se un tipo di base ha un costruttore predefinito non trasparente pubblico o protetto, il tipo derivato deve rispettare le regole di ereditarietà predefinite del costruttore. Il tipo derivato deve avere anche un costruttore predefinito e il costruttore deve essere almeno come un costruttore predefinito critico del tipo di base.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere la violazione, rimuovere il tipo o non derivare da un tipo non trasparente di sicurezza.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non eliminare gli avvisi da questa regola. Le violazioni di questa regola da parte del codice dell'applicazione comporteranno la reimpostazione del CoreCLR per il <xref:System.TypeLoadException>caricamento del tipo con un.

### <a name="code"></a>Codice

[!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]