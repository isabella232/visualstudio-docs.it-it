---
title: 'CA2116: I metodi APTCA devono chiamare solo metodi APTCA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 916b30cf4cff357ba468faae524d6b0ca7806959
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955791"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: I metodi APTCA devono chiamare solo metodi APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo in un assembly con il <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> attributo chiama un metodo in un assembly che non dispone dell'attributo.

## <a name="rule-description"></a>Descrizione della regola
 Per impostazione predefinita, i metodi pubblici o protetti negli assembly con nomi sicuri sono protetti in modo implicito da un [linking](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) per un'attendibilità totale; solo è considerato completamente attendibile i chiamanti possono accedere a un assembly con nome sicuro. Assembly con nome sicuro è contrassegnato con il <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attributo (APTCA) non è questo tipo di protezione. L'attributo disabilita la richiesta di collegamento, l'assembly vengono resi accessibili a chiamanti privi di attendibilità totale, ad esempio di codice in esecuzione da una rete intranet o Internet.

 Quando l'attributo APTCA è presente in un assembly completamente attendibile e l'assembly esegue codice in un altro assembly che non consente chiamanti parzialmente attendibili, è possibile una violazione della sicurezza. Se i due metodi `M1` e `M2` soddisfa le condizioni seguenti, i chiamanti malintenzionati possono usare il metodo `M1` per ignorare la richiesta di collegamento implicite con attendibilità totale che protegge `M2`:

- `M1` è un metodo pubblico dichiarato in un assembly completamente attendibile che ha l'attributo APTCA.

- `M1` chiama un metodo `M2` esterno `M1`dell'assembly.

- `M2`dell'assembly non ha l'attributo APTCA e, pertanto non deve essere eseguito da o per conto di chiamanti parzialmente attendibili.

  Un chiamante parzialmente attendibile `X` può chiamare metodo `M1`, provocando `M1` chiamare `M2`. In quanto `M2` non ha l'attributo APTCA, il relativo chiamante immediato (`M1`) deve soddisfare una richiesta di collegamento per l'attendibilità totale; `M1` sia totalmente attendibile e pertanto soddisfa questo controllo. Il rischio di sicurezza, infatti `X` contribuisce a soddisfare la richiesta di collegamento che consente di proteggere `M2` da chiamanti non attendibili. Di conseguenza, i metodi con l'attributo APTCA non devono chiamare metodi che non dispongono dell'attributo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Se è richiesto l'attributo APCTA, usare una richiesta per proteggere il metodo che chiama l'assembly con attendibilità totale. Le autorizzazioni esatte dipenderà è richiesta la funzionalità esposta dal metodo. Se è possibile, proteggere il metodo con una richiesta di attendibilità garantire che la funzionalità sottostante non viene esposta a chiamanti parzialmente attendibili. In caso contrario, selezionare un set di autorizzazioni che protegge in modo efficace le funzionalità esposte. Per altre informazioni sulle richieste, vedere [pretese](http://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che le funzionalità esposte tramite il metodo non direttamente o indirettamente consentano ai chiamanti di accedere a informazioni riservate, operazioni o risorse che possono essere usate in modo distruttivo.

## <a name="example"></a>Esempio
 L'esempio seguente usa due assembly e un'applicazione di test per illustrare la vulnerabilità di sicurezza rilevata da questa regola. Il primo assembly non ha l'attributo APTCA e non devono essere accessibili a chiamanti parzialmente attendibili (rappresentato da `M2` nella precedente discussione riguardo).

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>Esempio
 Il secondo assembly completamente attendibile e consente ai chiamanti parzialmente attendibili (rappresentato da `M1` nella precedente discussione riguardo).

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>Esempio
 L'applicazione di test (rappresentato da `X` nella precedente discussione riguardo) è parzialmente attendibile.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 Questo esempio produce il seguente output:

 **La richiesta di attendibilità completa: richiesta non è riuscita. ** 
 **ClassRequiringFullTrust.DoWork è stato chiamato.**
## <a name="related-rules"></a>Regole correlate
 [CA2117: I tipi APTCA devono estendere solo tipi di base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Vedere anche
 [Linee guida per la generazione di codice sicuro](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [assembly .NET Framework possono essere chiamati da codice parzialmente attendibile](http://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [usare parzialmente librerie da codice attendibile](http://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [richieste](http://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48) [Collegarle](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [dati e modellazione](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
