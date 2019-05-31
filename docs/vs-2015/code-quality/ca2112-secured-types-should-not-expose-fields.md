---
title: 'CA2112: I tipi protetti non devono esporre campi | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 17a52b952437ce136773d796972c6619a9733749
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687332"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: I tipi protetti non devono esporre campi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto contiene campi pubblici e protetta da un [richieste di collegamento](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Descrizione della regola
 Se il codice ha accesso a un'istanza di un tipo protetta da una richiesta di collegamento, non è necessario che il codice soddisfi la richiesta di collegamento per accedere ai campi del tipo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, contrassegnare i campi non pubblici e aggiungere i metodi che restituiscono i dati del campo o proprietà pubbliche. Controlli di sicurezza LinkDemand su tipi di proteggono l'accesso a proprietà e metodi del tipo. Sicurezza dall'accesso di codice, tuttavia, non si applica ai campi.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Per problemi di sicurezza sia per una progettazione ottimale, è necessario correggere le violazioni, rendendo non pubblici campi pubblici. È possibile eliminare un avviso da questa regola se il campo non contiene informazioni che devono rimanere protette e non fare affidamento sul contenuto del campo.

## <a name="example"></a>Esempio
 Nell'esempio seguente è costituito da una libreria di tipi (`SecuredTypeWithFields`) con i campi non protetti, un tipo (`Distributor`) consente di creare istanze del tipo di libreria e passate erroneamente istanze di tipi di autorizzazioni insufficienti per crearli e il codice dell'applicazione può leggere i campi di un'istanza anche se non dispone dell'autorizzazione che protegge il tipo.

 Il codice di libreria seguente viola la regola.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>Esempio
 L'applicazione non è possibile creare un'istanza a causa la richiesta di collegamento che consente di proteggere il tipo protetto. La classe seguente consente all'applicazione ottenere un'istanza del tipo protetto.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>Esempio
 L'applicazione riportata di seguito viene illustrato come fare, senza l'autorizzazione per accedere ai metodi del tipo protetta, accessibile dal codice relativi campi.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 Questo esempio produce il seguente output:

 **Creazione di un'istanza di SecuredTypeWithFields.** 
**i campi di tipo protetta: 22, 33**
**modifica campo di tipo protetto...** 
**Campi dell'oggetto memorizzato nella cache: 99, 33**
## <a name="related-rules"></a>Regole correlate
 [CA1051: Non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Vedere anche
 [Le richieste di collegamento](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [dati e modellazione](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
