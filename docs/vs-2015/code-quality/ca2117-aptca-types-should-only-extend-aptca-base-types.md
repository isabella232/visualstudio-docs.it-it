---
title: 'CA2117: I tipi APTCA devono estendere solo tipi di base APTCA | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 409133c173f497b1f21b36c7d8c4c89561c0aa15
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49171457"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: I tipi APTCA devono estendere solo tipi di base APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto in un assembly con il <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> attributo eredita da un tipo dichiarato in un assembly che non dispone dell'attributo.

## <a name="rule-description"></a>Descrizione della regola
 Per impostazione predefinita, pubblici o protetti tipi negli assembly con nomi sicuri sono protetti in modo implicito da un [richieste di ereditarietà](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9) per un'attendibilità totale. Assembly con nome sicuro è contrassegnato con il <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attributo (APTCA) non è questo tipo di protezione. L'attributo disabilita la richiesta di ereditarietà. In questo modo i tipi esposti dichiarati nell'assembly ereditabili dai tipi che non dispongono di attendibilità totale.

 Quando l'attributo APTCA è presente in un assembly completamente attendibile e un tipo nell'assembly eredita da un tipo che non consente chiamanti parzialmente attendibili, è possibile una violazione della sicurezza. Se due tipi `T1` e `T2` soddisfa le condizioni seguenti, i chiamanti malintenzionati possono usare il tipo `T1` per ignorare la richiesta di ereditarietà implicita con attendibilità totale che protegge `T2`:

-   `T1` è un tipo pubblico dichiarato in un assembly completamente attendibile che ha l'attributo APTCA.

-   `T1` eredita da un tipo `T2` esterno dell'assembly.

-   `T2`dell'assembly non ha l'attributo APTCA e, pertanto, non può essere ereditato dai tipi negli assembly parzialmente attendibile.

 Un tipo parzialmente attendibile `X` possono ereditare `T1`, che fornisce accesso ai membri ereditati dichiarati in `T2`. In quanto `T2` non ha l'attributo APTCA, il relativo tipo derivato immediata (`T1`) deve soddisfare una richiesta di ereditarietà per l'attendibilità totale; `T1` sia totalmente attendibile e pertanto soddisfa questo controllo. Il rischio di sicurezza, infatti `X` contribuisce a soddisfare la richiesta di ereditarietà che protegge `T2` dalle sottoclassi non attendibili. Per questo motivo, i tipi con l'attributo APTCA non devono estendere tipi che non dispongono dell'attributo.

 Un altro problema di sicurezza e magari più comuni, che è il tipo derivato (`T1`) può, a causa di errori del programmatore, esporre i membri protetti dal tipo che richiede attendibilità totale (`T2`). In questo caso, i chiamanti non attendibili accedere a informazioni che devono essere disponibili solo ai tipi completamente attendibili.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Se il tipo segnalato dalla violazione è in un assembly che non richiede l'attributo APTCA, rimuoverlo.

 Se l'attributo APTCA è necessario, aggiungere una richiesta di ereditarietà per l'attendibilità totale per il tipo. Ciò consente di evitare ereditarietà dai tipi non attendibili.

 È possibile correggere una violazione, aggiungere l'attributo APTCA agli assembly dei tipi di base segnalati dalla violazione. Non eseguire questa operazione senza prima eseguire una verifica di sicurezza con utilizzo intensivo di tutto il codice negli assembly e tutto il codice che dipende dagli assembly.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che i membri protetti esposti dal tipo non direttamente o indirettamente consentono ai chiamanti non attendibili di accedere a informazioni riservate, operazioni o risorse che possono essere usate in modo distruttivo.

## <a name="example"></a>Esempio
 L'esempio seguente usa due assembly e un'applicazione di test per illustrare la vulnerabilità di sicurezza rilevata da questa regola. Il primo assembly non ha l'attributo APTCA e non deve essere ereditato dai tipi parzialmente attendibili (rappresentato da `T2` nella precedente discussione riguardo).

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>Esempio
 Il secondo assembly, rappresentato da `T1` nella precedente discussione è completamente attendibile e consente ai chiamanti parzialmente attendibili.

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>Esempio
 Il tipo di test, rappresentato da `X` nella discussione precedente è in un assembly parzialmente attendibile.

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 Questo esempio produce il seguente output:

 **Meet al glen conoscerete 2/22/2003 12:00:00 AM. ** 
 **Dal Test: Prato sunny**
**riunisce le Prato sunny 2/22/2003 12:00:00 AM.**
## <a name="related-rules"></a>Regole correlate
 [CA2116: I metodi APTCA devono chiamare solo metodi APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Vedere anche
 [Linee guida per la generazione di codice sicuro](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [assembly .NET Framework possono essere chiamati da codice parzialmente attendibile](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [usare parzialmente librerie da codice attendibile](http://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [richieste di ereditarietà](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)




