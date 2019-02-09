---
title: 'CA2116: I metodi APTCA devono chiamare solo metodi APTCA'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03948506d928f7d638b21c1fa4bc0a35818ec09a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926911"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: I metodi APTCA devono chiamare solo metodi APTCA

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un metodo in un assembly con il <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> attributo chiama un metodo in un assembly che non dispone dell'attributo.

## <a name="rule-description"></a>Descrizione della regola

Per impostazione predefinita, i metodi pubblici o protetti negli assembly con nomi sicuri sono protetti in modo implicito da un [linking](/dotnet/framework/misc/link-demands) per un'attendibilità totale; solo è considerato completamente attendibile i chiamanti possono accedere a un assembly con nome sicuro. Assembly con nome sicuro è contrassegnato con il <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attributo (APTCA) non è questo tipo di protezione. L'attributo disabilita la richiesta di collegamento, l'assembly vengono resi accessibili a chiamanti privi di attendibilità totale, ad esempio di codice in esecuzione da una rete intranet o Internet.

Quando l'attributo APTCA è presente in un assembly completamente attendibile e l'assembly esegue codice in un altro assembly che non consente chiamanti parzialmente attendibili, è possibile una violazione della sicurezza. Se i due metodi `M1` e `M2` soddisfa le condizioni seguenti, i chiamanti malintenzionati possono usare il metodo `M1` per ignorare la richiesta di collegamento implicite con attendibilità totale che protegge `M2`:

- `M1` è un metodo pubblico dichiarato in un assembly completamente attendibile che ha l'attributo APTCA.

- `M1` chiama un metodo `M2` esterno `M1`dell'assembly.

- `M2`dell'assembly non ha l'attributo APTCA e, pertanto non deve essere eseguito da o per conto di chiamanti parzialmente attendibili.

Un chiamante parzialmente attendibile `X` può chiamare metodo `M1`, provocando `M1` chiamare `M2`. In quanto `M2` non ha l'attributo APTCA, il relativo chiamante immediato (`M1`) deve soddisfare una richiesta di collegamento per l'attendibilità totale; `M1` sia totalmente attendibile e pertanto soddisfa questo controllo. Il rischio di sicurezza, infatti `X` contribuisce a soddisfare la richiesta di collegamento che consente di proteggere `M2` da chiamanti non attendibili. Di conseguenza, i metodi con l'attributo APTCA non devono chiamare metodi che non dispongono dell'attributo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Se è richiesto l'attributo APCTA, usare una richiesta per proteggere il metodo che chiama l'assembly con attendibilità totale. Le autorizzazioni esatte dipenderà è richiesta la funzionalità esposta dal metodo. Se è possibile, proteggere il metodo con una richiesta di attendibilità garantire che la funzionalità sottostante non viene esposta a chiamanti parzialmente attendibili. In caso contrario, selezionare un set di autorizzazioni che protegge in modo efficace le funzionalità esposte.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che le funzionalità esposte tramite il metodo non direttamente o indirettamente consentano ai chiamanti di accedere a informazioni riservate, operazioni o risorse che possono essere usate in modo distruttivo.

## <a name="example-1"></a>Esempio 1
 L'esempio seguente usa due assembly e un'applicazione di test per illustrare la vulnerabilità di sicurezza rilevata da questa regola. Il primo assembly non ha l'attributo APTCA e non devono essere accessibili a chiamanti parzialmente attendibili (rappresentato da `M2` nella precedente discussione riguardo).

 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example-2"></a>Esempio 2
 Il secondo assembly completamente attendibile e consente ai chiamanti parzialmente attendibili (rappresentato da `M1` nella precedente discussione riguardo).

 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example-3"></a>Esempio 3
 L'applicazione di test (rappresentato da `X` nella precedente discussione riguardo) è parzialmente attendibile.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

Questo esempio produce il seguente output:

```txt
Demand for full trust:Request failed.
ClassRequiringFullTrust.DoWork was called.
```

## <a name="related-rules"></a>Regole correlate

- [CA2117: I tipi APTCA devono estendere solo tipi di base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Vedere anche

- [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)
- [Uso di librerie da codice parzialmente attendibile](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
- [Richieste di collegamento](/dotnet/framework/misc/link-demands)
- [Dati e modellazione](/dotnet/framework/data/index)