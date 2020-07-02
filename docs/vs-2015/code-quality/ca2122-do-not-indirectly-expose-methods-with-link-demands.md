---
title: 'CA2122: non esporre indirettamente metodi con richieste di collegamento | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 846ce010cddfd505bb967ec612a5c31dd8321977
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544326"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Non esporre in modo indiretto metodi con richieste di collegamento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un membro pubblico o protetto presenta [richieste di collegamento](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) e viene chiamato da un membro che non esegue alcun controllo di sicurezza.

## <a name="rule-description"></a>Descrizione della regola
 Una richiesta di collegamento controlla esclusivamente le autorizzazioni del chiamante immediato. Se un membro `X` non esegue richieste di sicurezza dei chiamanti e chiama il codice protetto da una richiesta di collegamento, un chiamante senza l'autorizzazione necessaria può utilizzare `X` per accedere al membro protetto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Aggiungere i dati di sicurezza [e la modellazione](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) o la richiesta di collegamento al membro in modo che non fornisca più l'accesso non sicuro al membro protetto da richiesta di collegamento.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che il codice non conceda ai chiamanti l'accesso a operazioni o risorse che possono essere utilizzate in modo distruttivo.

## <a name="example"></a>Esempio
 Negli esempi seguenti viene illustrata una libreria che viola la regola e un'applicazione che dimostra la debolezza della libreria. La libreria di esempio fornisce due metodi che insieme violano la regola. Il `EnvironmentSetting` metodo è protetto da una richiesta di collegamento per l'accesso illimitato alle variabili di ambiente. Il `DomainInformation` metodo non esegue alcuna richiesta di sicurezza dei chiamanti prima di chiamare `EnvironmentSetting` .

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>Esempio
 L'applicazione seguente chiama il membro della libreria non protetta.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 Questo esempio produce il seguente output:

 **Valore da membro non protetto: seattle.corp.contoso.com**
## <a name="see-also"></a>Vedere anche
 [Linee guida per la codifica sicura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [collegamento richieste](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [di dati e modellazione](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
