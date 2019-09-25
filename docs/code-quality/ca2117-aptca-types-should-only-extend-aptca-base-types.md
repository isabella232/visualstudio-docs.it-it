---
title: 'CA2117: I tipi APTCA devono estendere solo tipi di base APTCA'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 832d2c9fc1d4b9138a7cd1bc39868b3c4bf1b814
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232651"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: I tipi APTCA devono estendere solo tipi di base APTCA

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Category|Microsoft.Security|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Un tipo pubblico o protetto in un assembly con l' <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> attributo eredita da un tipo dichiarato in un assembly che non dispone dell'attributo.

## <a name="rule-description"></a>Descrizione della regola

Per impostazione predefinita, i tipi pubblici o protetti negli assembly con nomi sicuri sono implicitamente protetti da un [InheritanceDemand](xref:System.Security.Permissions.SecurityAction#System_Security_Permissions_SecurityAction_InheritanceDemand) per l'attendibilità totale. Gli assembly con nome sicuro contrassegnati con <xref:System.Security.AllowPartiallyTrustedCallersAttribute> l'attributo (APTCA) non dispongono di questa protezione. L'attributo Disabilita la richiesta di ereditarietà. I tipi esposti dichiarati in un assembly senza una richiesta di ereditarietà sono ereditabili da tipi privi di attendibilità totale.

Quando l'attributo APTCA è presente in un assembly completamente attendibile e un tipo nell'assembly eredita da un tipo che non consente chiamanti parzialmente attendibili, è possibile un exploit di sicurezza. Se due tipi `T1` e `T2` soddisfano le condizioni seguenti, i chiamanti malintenzionati `T1` possono utilizzare il tipo per ignorare la richiesta implicita `T2`di ereditarietà dell'attendibilità totale che protegge:

- `T1`è un tipo pubblico dichiarato in un assembly completamente attendibile con l'attributo APTCA.

- `T1`eredita da un tipo `T2` all'esterno del relativo assembly.

- `T2`l'assembly di non dispone dell'attributo APTCA e, pertanto, non deve essere ereditabile dai tipi in assembly parzialmente attendibili.

Un tipo `X` parzialmente attendibile può ereditare da `T1`, che consente l'accesso ai membri ereditati dichiarati in `T2`. Poiché `T2` non dispone dell'attributo APTCA, il relativo tipo derivato immediato (`T1`) deve soddisfare una richiesta di ereditarietà per l'attendibilità totale; `T1` ha attendibilità totale e pertanto soddisfa questo controllo. Il rischio per la sicurezza `X` è dovuto al fatto che non partecipa alla soddisfazione della `T2` richiesta di ereditarietà che protegge dalla sottoclasse non attendibile. Per questo motivo, i tipi con l'attributo APTCA non devono estendere i tipi che non dispongono dell'attributo.

Un altro problema di sicurezza, probabilmente più comune, è che il tipo derivato (`T1`) può, tramite un errore del programmatore, esporre membri protetti dal tipo che richiede l'attendibilità totale (`T2`). Quando si verifica questa esposizione, i chiamanti non attendibili ottengono l'accesso alle informazioni che devono essere disponibili solo per i tipi completamente attendibili.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Se il tipo segnalato dalla violazione si trova in un assembly che non richiede l'attributo APTCA, rimuoverlo.

Se l'attributo APTCA è obbligatorio, aggiungere una richiesta di ereditarietà per l'attendibilità totale al tipo. La richiesta di ereditarietà protegge dall'ereditarietà da tipi non attendibili.

È possibile correggere una violazione aggiungendo l'attributo APTCA agli assembly dei tipi di base segnalati dalla violazione. Non eseguire questa operazione senza prima eseguire un'intensa revisione della sicurezza di tutto il codice negli assembly e tutto il codice che dipende dagli assembly.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che i membri protetti esposti dal tipo non consentano direttamente o indirettamente ai chiamanti non attendibili di accedere a informazioni riservate, operazioni o risorse che possono essere utilizzate in modo distruttivo.

## <a name="example"></a>Esempio

Nell'esempio seguente vengono utilizzati due assembly e un'applicazione di test per illustrare la vulnerabilità di sicurezza rilevata da questa regola. Il primo assembly non dispone dell'attributo APTCA e non deve essere ereditabile da tipi parzialmente attendibili (rappresentati `T2` da nella discussione precedente).

[!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]

Il secondo assembly, rappresentato dalla `T1` precedente discussione, è completamente attendibile e consente chiamanti parzialmente attendibili.

[!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]

Il tipo di test, rappresentato `X` dalla precedente discussione, si trova in un assembly parzialmente attendibile.

[!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]

Questo esempio produce il seguente output:

```txt
Meet at the shady glen 2/22/2003 12:00:00 AM!
From Test: sunny meadow
Meet at the sunny meadow 2/22/2003 12:00:00 AM!
```

## <a name="related-rules"></a>Regole correlate

[CA2116 I metodi APTCA devono chiamare solo metodi APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Vedere anche

- [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)
- [Uso di librerie da codice parzialmente attendibile](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
