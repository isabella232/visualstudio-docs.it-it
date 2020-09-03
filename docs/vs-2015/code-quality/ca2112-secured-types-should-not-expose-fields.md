---
title: 'CA2112: i tipi protetti non devono esporre campi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4267b4f55f78106a4d1e8f3b2f9b296be9ddf618
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546536"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: I tipi protetti non devono esporre campi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto contiene campi pubblici ed è protetto da [richieste di collegamento](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Descrizione della regola
 Se il codice ha accesso a un'istanza di un tipo protetta da una richiesta di collegamento, non è necessario che il codice soddisfi la richiesta di collegamento per accedere ai campi del tipo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rendere i campi non pubblici e aggiungere proprietà o metodi pubblici che restituiscono i dati del campo. I controlli di sicurezza LinkDemand sui tipi proteggono l'accesso alle proprietà e ai metodi del tipo. Tuttavia, la sicurezza dall'accesso di codice non si applica ai campi.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Per motivi di sicurezza e per una progettazione corretta, è consigliabile correggere le violazioni rendendo i campi pubblici non pubblici. È possibile eliminare un avviso da questa regola se il campo non contiene informazioni che devono rimanere protette e non si basano sul contenuto del campo.

## <a name="example"></a>Esempio
 L'esempio seguente è costituito da un tipo di libreria ( `SecuredTypeWithFields` ) con campi non protetti, un tipo ( `Distributor` ) in grado di creare istanze del tipo di libreria e le istanze passate erroneamente ai tipi non dispongono dell'autorizzazione per crearle e del codice dell'applicazione in grado di leggere i campi di un'istanza anche se non dispone dell'autorizzazione che protegge il tipo.

 Il codice della libreria seguente viola la regola.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>Esempio
 L'applicazione non è in grado di creare un'istanza di a causa della richiesta di collegamento che protegge il tipo protetto. La classe seguente consente all'applicazione di ottenere un'istanza del tipo protetto.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>Esempio
 Nell'applicazione seguente viene illustrato come, senza l'autorizzazione ad accedere ai metodi di un tipo protetto, il codice può accedere ai relativi campi.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 Questo esempio produce il seguente output:

 **Creazione di un'istanza di SecuredTypeWithFields.** 
 **Campi di tipo protetto: 22, 33** 
 **Modifica del campo del tipo protetto in corso...** 
 **Campi oggetto memorizzati nella cache: 99, 33**
## <a name="related-rules"></a>Regole correlate
 [CA1051: Non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Vedere anche
 [Collegamento](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [di dati e modellazione](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) delle richieste
