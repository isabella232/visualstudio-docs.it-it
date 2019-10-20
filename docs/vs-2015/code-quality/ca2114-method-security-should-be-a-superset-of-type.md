---
title: 'CA2114: la sicurezza del metodo deve essere un superset di tipo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1adc8f610644d736bc4546d8299457ba0234a1d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658664"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: La sicurezza del metodo deve essere un superset del tipo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo dispone di sicurezza dichiarativa e uno dei relativi metodi dispone di sicurezza dichiarativa per la stessa azione di sicurezza e l'azione di sicurezza non è [richiesta di collegamento](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) o [richieste di ereditarietà](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)e le autorizzazioni controllate dal tipo non sono un subset del autorizzazioni controllate dal metodo.

## <a name="rule-description"></a>Descrizione della regola
 Un metodo non deve avere una sicurezza dichiarativa a livello di metodo e a livello di tipo per la stessa azione. I due controlli non vengono combinati. viene applicata solo la richiesta a livello di metodo. Se, ad esempio, un tipo richiede l'autorizzazione `X` e uno dei relativi metodi richiede l'autorizzazione `Y`, non è necessario che il codice disponga delle autorizzazioni `X` per eseguire il metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Esaminare il codice per assicurarsi che siano necessarie entrambe le azioni. Se sono necessarie entrambe le azioni, assicurarsi che l'azione a livello di metodo includa la sicurezza specificata a livello di tipo. Se, ad esempio, il tipo richiede l'autorizzazione `X` e anche il metodo deve richiedere l'autorizzazione `Y`, il metodo deve richiedere in modo esplicito `X` e `Y`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il metodo non richiede la sicurezza specificata dal tipo. Tuttavia, non si tratta di uno scenario normale e potrebbe indicare la necessità di un'attenta revisione della progettazione.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono utilizzate le autorizzazioni di ambiente per illustrare i rischi derivanti dalla violazione di questa regola. In questo esempio, il codice dell'applicazione crea un'istanza del tipo protetto prima di negare l'autorizzazione richiesta dal tipo. In uno scenario di minaccia reale, l'applicazione richiederebbe un altro modo per ottenere un'istanza dell'oggetto.

 Nell'esempio seguente la libreria richiede l'autorizzazione di scrittura per un tipo e l'autorizzazione di lettura per un metodo.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>Esempio
 Il codice dell'applicazione seguente illustra la vulnerabilità della libreria chiamando il metodo anche se non soddisfa il requisito di sicurezza a livello di tipo.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 Questo esempio produce il seguente output:

 **[Tutte le autorizzazioni] informazioni personali: 6/16/1964 12:00:00 AM** 
 **[nessuna autorizzazione di scrittura (richiesta dal tipo)] informazioni personali: 6/16/1964 12:00:00 AM** 
 **[nessuna autorizzazione di lettura (richiesta dal metodo)] non è stato possibile accedere a personale informazioni: richiesta non riuscita.**
## <a name="see-also"></a>Vedere anche
 [Linee guida per il codice sicuro](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [ereditarietà richieste](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [collegamento richieste](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [di dati e modellazione](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
