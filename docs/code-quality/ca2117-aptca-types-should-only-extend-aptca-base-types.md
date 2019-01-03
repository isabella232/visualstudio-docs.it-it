---
title: 'CA2117: I tipi APTCA devono estendere solo tipi di base APTCA'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc2086038187093397d53e80b1a26f2006c32c80
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873353"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: I tipi APTCA devono estendere solo tipi di base APTCA

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un tipo pubblico o protetto in un assembly con il <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> attributo eredita da un tipo dichiarato in un assembly che non dispone dell'attributo.

## <a name="rule-description"></a>Descrizione della regola

Per impostazione predefinita, pubblici o protetti tipi negli assembly con nomi sicuri sono protetti in modo implicito da un [InheritanceDemand](xref:System.Security.Permissions.SecurityAction#System_Security_Permissions_SecurityAction_InheritanceDemand) per un'attendibilità totale. Assembly con nome sicuro è contrassegnato con il <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attributo (APTCA) non è questo tipo di protezione. L'attributo disabilita la richiesta di ereditarietà. I tipi esposti dichiarati in un assembly senza una richiesta di ereditarietà sono ereditabili dai tipi che non dispongono di attendibilità totale.

Quando l'attributo APTCA è presente in un assembly completamente attendibile e un tipo nell'assembly eredita da un tipo che non consente chiamanti parzialmente attendibili, è possibile una violazione della sicurezza. Se due tipi `T1` e `T2` soddisfa le condizioni seguenti, i chiamanti malintenzionati possono usare il tipo `T1` per ignorare la richiesta di ereditarietà implicita con attendibilità totale che protegge `T2`:

- `T1` è un tipo pubblico dichiarato in un assembly completamente attendibile che ha l'attributo APTCA.

- `T1` eredita da un tipo `T2` esterno dell'assembly.

- `T2`dell'assembly non ha l'attributo APTCA e, pertanto, non può essere ereditato dai tipi negli assembly parzialmente attendibile.

Un tipo parzialmente attendibile `X` possono ereditare `T1`, che fornisce accesso ai membri ereditati dichiarati in `T2`. In quanto `T2` non ha l'attributo APTCA, il relativo tipo derivato immediata (`T1`) deve soddisfare una richiesta di ereditarietà per l'attendibilità totale; `T1` sia totalmente attendibile e pertanto soddisfa questo controllo. Il rischio di sicurezza, infatti `X` contribuisce a soddisfare la richiesta di ereditarietà che protegge `T2` dalle sottoclassi non attendibili. Per questo motivo, i tipi con l'attributo APTCA non devono estendere tipi che non dispongono dell'attributo.

Un altro problema di sicurezza e magari più comuni, che è il tipo derivato (`T1`) può, a causa di errori del programmatore, esporre i membri protetti dal tipo che richiede attendibilità totale (`T2`). Quando si verifica questo rischio, i chiamanti non attendibili accedere a informazioni che devono essere disponibili solo ai tipi completamente attendibili.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Se il tipo segnalato dalla violazione è in un assembly che non richiede l'attributo APTCA, rimuoverlo.

Se l'attributo APTCA è necessario, aggiungere una richiesta di ereditarietà per l'attendibilità totale per il tipo. La richiesta di ereditarietà protezione dall'ereditarietà da tipi non attendibili.

È possibile correggere una violazione, aggiungere l'attributo APTCA agli assembly dei tipi di base segnalati dalla violazione. Non eseguire questa operazione senza prima eseguire una verifica di sicurezza con utilizzo intensivo di tutto il codice negli assembly e tutto il codice che dipende dagli assembly.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che i membri protetti esposti dal tipo non direttamente o indirettamente consentono ai chiamanti non attendibili di accedere a informazioni riservate, operazioni o risorse che possono essere usate in modo distruttivo.

## <a name="example"></a>Esempio

L'esempio seguente usa due assembly e un'applicazione di test per illustrare la vulnerabilità di sicurezza rilevata da questa regola. Il primo assembly non ha l'attributo APTCA e non deve essere ereditato dai tipi parzialmente attendibili (rappresentato da `T2` nella precedente discussione riguardo).

[!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]

Il secondo assembly, rappresentato da `T1` nella precedente discussione è completamente attendibile e consente ai chiamanti parzialmente attendibili.

[!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]

Il tipo di test, rappresentato da `X` nella discussione precedente è in un assembly parzialmente attendibile.

[!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]

Questo esempio produce il seguente output:

```txt
Meet at the shady glen 2/22/2003 12:00:00 AM!
From Test: sunny meadow
Meet at the sunny meadow 2/22/2003 12:00:00 AM!
```

## <a name="related-rules"></a>Regole correlate

[CA2116: I metodi APTCA devono chiamare solo metodi APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Vedere anche

- [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)
- [Uso di librerie da codice parzialmente attendibile](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
