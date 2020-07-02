---
title: "CA2123: l'override delle richieste di collegamento deve essere identico a base | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a722eb95561a1a81b0d17b8876df8b4bac048b5c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544261"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: Le richieste di collegamento negli override devono essere identiche a quelle nei metodi di base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo pubblico o protetto in un tipo pubblico esegue l'override di un metodo o implementa un'interfaccia e non ha le stesse [richieste di collegamento](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) dell'interfaccia o del metodo virtuale.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola associa un metodo al relativo metodo di base che può essere un'interfaccia o un metodo virtuale in un altro tipo, quindi confronta le richieste di collegamento in ognuno. Una violazione viene segnalata se il metodo o il metodo di base dispone di una richiesta di collegamento e l'altro no.

 Se questa regola viene violata, un chiamante malintenzionato può ignorare la richiesta di collegamento semplicemente chiamando il metodo non protetto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, applicare la stessa richiesta di collegamento al metodo o all'implementazione di Sostituisci. Se questa operazione non è possibile, contrassegnare il metodo con una richiesta completa oppure rimuovere completamente l'attributo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrate varie violazioni di questa regola.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.OverridesAndSecurity/cs/FxCop.Security.OverridesAndSecurity.cs#1)]

## <a name="see-also"></a>Vedere anche
 [Linee guida per la codifica protetta](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [richieste di collegamento](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
