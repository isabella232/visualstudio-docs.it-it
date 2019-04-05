---
title: 'CA2114: Sicurezza del metodo deve essere un superset del tipo | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c9e0024ae6db5af3f1cf23c07fe29fbac8e4827d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968277"
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
 Un tipo dispone di sicurezza dichiarativa e uno dei relativi metodi ha la sicurezza dichiarativa per la stessa azione di sicurezza e l'azione di sicurezza non è [linking](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) oppure [richieste di ereditarietà](http://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)e le autorizzazioni selezionata per il tipo non sono un sottoinsieme di autorizzazioni controllato dal metodo.

## <a name="rule-description"></a>Descrizione della regola
 Un metodo non deve avere sia una sicurezza dichiarativa a livello di metodo e a livello di tipo per la stessa azione. Non vengono combinati i due controlli; viene applicata solo la richiesta a livello di metodo. Ad esempio, se un tipo richiede l'autorizzazione `X`, e uno dei relativi metodi richiede l'autorizzazione `Y`, codice non è necessario disporre dell'autorizzazione `X` all'esecuzione del metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Esaminare il codice per assicurarsi che entrambe le azioni sono obbligatori. Se sono necessarie entrambe le azioni, assicurarsi che l'azione a livello di metodo include la sicurezza a livello di tipo specificata. Ad esempio, se il tipo richiede l'autorizzazione `X`, e il relativo metodo deve anche richiedere l'autorizzazione `Y`, il metodo deve richiedere in modo esplicito `X` e `Y`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il metodo non richiede la sicurezza specificata dal tipo. Tuttavia, ciò non è uno scenario comune e potrebbe indicare la necessità di una revisione di un'attenta progettazione.

## <a name="example"></a>Esempio
 Nell'esempio seguente usa le autorizzazioni dell'ambiente per illustrare i pericoli di violazione di questa regola. In questo esempio, il codice dell'applicazione crea un'istanza del tipo protetto prima di negare l'autorizzazione necessaria per il tipo. In uno scenario reale delle minacce, l'applicazione potrebbe richiedere un altro modo per ottenere un'istanza dell'oggetto.

 Nell'esempio seguente, la libreria richiede autorizzazioni di scrittura per un tipo e l'autorizzazione per un metodo di lettura.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>Esempio
 Il codice dell'applicazione seguente illustra la vulnerabilità della libreria chiamando il metodo anche se non soddisfa il requisito di sicurezza a livello di tipo.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 Questo esempio produce il seguente output:

 **[Tutte le autorizzazioni] Informazioni personali: 6 o 16/1964 12:00:00 AM**
 **[Nessuna autorizzazione di scrittura (richiesta dal tipo)] dati personali: 6 o 16/1964 12:00:00 AM**
 **[Nessuna autorizzazione di lettura (richiesta dal metodo)] è stato possibile accedere alle informazioni personali: Richiesta non riuscita.**
## <a name="see-also"></a>Vedere anche
 [Linee guida per la generazione di codice sicuro](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [richieste di ereditarietà](http://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [collegarle](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [dati e modellazione](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
