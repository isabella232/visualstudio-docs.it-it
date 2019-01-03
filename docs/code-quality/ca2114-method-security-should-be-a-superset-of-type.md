---
title: 'CA2114: Sicurezza del metodo deve essere un superset del tipo'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec58e8060447a02309a0a902bcf63eea8805ca8c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53881792"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: Sicurezza del metodo deve essere un superset del tipo

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo dispone di sicurezza dichiarativa e uno dei relativi metodi ha la sicurezza dichiarativa per la stessa azione di sicurezza e l'azione di sicurezza non è [richieste di collegamento](/dotnet/framework/misc/link-demands), e le autorizzazioni selezionate per il tipo non sono un sottoinsieme delle autorizzazioni selezionata dal metodo.

## <a name="rule-description"></a>Descrizione della regola
 Un metodo non deve avere sia una sicurezza dichiarativa a livello di metodo e a livello di tipo per la stessa azione. Non vengono combinati i due controlli; viene applicata solo la richiesta a livello di metodo. Ad esempio, se un tipo richiede l'autorizzazione `X`, e uno dei relativi metodi richiede l'autorizzazione `Y`, codice non è necessario disporre dell'autorizzazione `X` all'esecuzione del metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Esaminare il codice per assicurarsi che entrambe le azioni sono obbligatori. Se sono necessarie entrambe le azioni, assicurarsi che l'azione a livello di metodo include la sicurezza a livello di tipo specificata. Ad esempio, se il tipo richiede l'autorizzazione `X`, e il relativo metodo deve anche richiedere l'autorizzazione `Y`, il metodo deve richiedere in modo esplicito `X` e `Y`.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola se il metodo non richiede la sicurezza specificata dal tipo. Tuttavia, ciò non è uno scenario comune e potrebbe indicare la necessità di una revisione di un'attenta progettazione.

## <a name="example-1"></a>Esempio 1

Nell'esempio seguente usa le autorizzazioni dell'ambiente per illustrare i pericoli di violazione di questa regola. In questo esempio, il codice dell'applicazione crea un'istanza del tipo protetto prima di negare l'autorizzazione necessaria per il tipo. In uno scenario reale delle minacce, l'applicazione potrebbe richiedere un altro modo per ottenere un'istanza dell'oggetto.

Nell'esempio seguente, la libreria richiede autorizzazioni di scrittura per un tipo e l'autorizzazione per un metodo di lettura.

[!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example-2"></a>Esempio 2

Il codice dell'applicazione seguente illustra la vulnerabilità della libreria chiamando il metodo anche se non soddisfa il requisito di sicurezza a livello di tipo.

[!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]

Questo esempio produce il seguente output:

```txt
[All permissions] Personal information: 6/16/1964 12:00:00 AM
[No write permission (demanded by type)] Personal information: 6/16/1964 12:00:00 AM
[No read permission (demanded by method)] Could not access personal information: Request failed.
```

## <a name="see-also"></a>Vedere anche

- [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)
- [Richieste di collegamento](/dotnet/framework/misc/link-demands)
- [Dati e modellazione](/dotnet/framework/data/index)