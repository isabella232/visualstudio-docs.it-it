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
ms.openlocfilehash: f09817e9248fdc28f56ac0162e783bf72643ee5c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232679"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: I metodi APTCA devono chiamare solo metodi APTCA

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Category|Microsoft.Security|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Un metodo in un assembly con l' <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> attributo chiama un metodo in un assembly che non dispone dell'attributo.

## <a name="rule-description"></a>Descrizione della regola

Per impostazione predefinita, i metodi pubblici o protetti negli assembly con nomi sicuri vengono protetti in modo implicito da [richieste di collegamento](/dotnet/framework/misc/link-demands) per l'attendibilità totale. solo i chiamanti completamente attendibili possono accedere a un assembly con nome sicuro. Gli assembly con nome sicuro contrassegnati con <xref:System.Security.AllowPartiallyTrustedCallersAttribute> l'attributo (APTCA) non dispongono di questa protezione. L'attributo Disabilita la richiesta di collegamento, rendendo l'assembly accessibile ai chiamanti privi di attendibilità totale, ad esempio il codice eseguito da una rete Intranet o Internet.

Quando l'attributo APTCA è presente in un assembly completamente attendibile e l'assembly esegue codice in un altro assembly che non consente chiamanti parzialmente attendibili, è possibile che si sia verificata una violazione della sicurezza. Se due metodi `M1` e `M2` soddisfano le condizioni seguenti, i chiamanti malintenzionati `M1` possono usare il metodo per ignorare la richiesta di collegamento `M2`di attendibilità totale implicita che protegge:

- `M1`è un metodo pubblico dichiarato in un assembly completamente attendibile con l'attributo APTCA.

- `M1`chiama un metodo `M2` esterno `M1`all'assembly.

- `M2`l'assembly di non dispone dell'attributo APTCA e, pertanto, non deve essere eseguito da o per conto di chiamanti parzialmente attendibili.

Un chiamante `X` parzialmente attendibile può chiamare `M1`il metodo `M1` , causando la chiamata `M2`a. Poiché `M2` non dispone dell'attributo APTCA, il chiamante immediato (`M1`) deve soddisfare una richiesta di collegamento per l'attendibilità totale; `M1` ha attendibilità totale e pertanto soddisfa questo controllo. Il rischio per la sicurezza `X` è dovuto al fatto che non partecipa alla soddisfazione della `M2` richiesta di collegamento che protegge da chiamanti non attendibili. Pertanto, i metodi con l'attributo APTCA non devono chiamare metodi che non dispongono dell'attributo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Se l'attributo APCTA è obbligatorio, usare una richiesta per proteggere il metodo che chiama nell'assembly con attendibilità totale. Le autorizzazioni richieste dipenderanno dalle funzionalità esposte dal metodo. Se possibile, proteggere il metodo con una richiesta di attendibilità totale per assicurarsi che la funzionalità sottostante non venga esposta a chiamanti parzialmente attendibili. Se ciò non è possibile, selezionare un set di autorizzazioni che protegga efficacemente la funzionalità esposta.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che la funzionalità esposta dal metodo non consenta direttamente o indirettamente ai chiamanti di accedere a informazioni riservate, operazioni o risorse che possono essere utilizzate in modo distruttivo.

## <a name="example-1"></a>Esempio 1
Nell'esempio seguente vengono utilizzati due assembly e un'applicazione di test per illustrare la vulnerabilità di sicurezza rilevata da questa regola. Il primo assembly non dispone dell'attributo APTCA e non deve essere accessibile ai chiamanti parzialmente attendibili (rappresentati `M2` da nella discussione precedente).

[!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example-2"></a>Esempio 2
Il secondo assembly è completamente attendibile e consente chiamanti parzialmente attendibili ( `M1` rappresentati da nella discussione precedente).

[!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example-3"></a>Esempio 3
L'applicazione di test (rappresentata da `X` nella discussione precedente) è parzialmente attendibile.

[!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

Questo esempio produce il seguente output:

```txt
Demand for full trust:Request failed.
ClassRequiringFullTrust.DoWork was called.
```

## <a name="related-rules"></a>Regole correlate

- [CA2117 I tipi APTCA devono estendere solo tipi di base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Vedere anche

- [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)
- [Uso di librerie da codice parzialmente attendibile](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
- [Richieste di collegamento](/dotnet/framework/misc/link-demands)
- [Dati e modellazione](/dotnet/framework/data/index)