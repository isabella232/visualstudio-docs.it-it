---
title: 'CA2117: I tipi APTCA devono estendere solo tipi di base APTCA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 09fa055fbf1b11e06b1dde32df5a316a3ec39848
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658662"
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
 Un tipo pubblico o protetto in un assembly con l'attributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> eredita da un tipo dichiarato in un assembly che non dispone dell'attributo.

## <a name="rule-description"></a>Descrizione della regola
 Per impostazione predefinita, i tipi pubblici o protetti negli assembly con nomi sicuri vengono protetti in modo implicito da una [richiesta di ereditarietà](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) per l'attendibilità totale. Gli assembly con nome sicuro contrassegnati con l'attributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) non dispongono di questa protezione. L'attributo Disabilita la richiesta di ereditarietà. In questo modo i tipi esposti dichiarati nell'assembly possono essere ereditati da tipi privi di attendibilità totale.

 Quando l'attributo APTCA è presente in un assembly completamente attendibile e un tipo nell'assembly eredita da un tipo che non consente chiamanti parzialmente attendibili, è possibile un exploit di sicurezza. Se due tipi `T1` e `T2` soddisfano le condizioni seguenti, i chiamanti malintenzionati possono utilizzare il tipo `T1` per ignorare la richiesta di ereditarietà dell'attendibilità totale implicita che protegge `T2`:

- `T1` è un tipo pubblico dichiarato in un assembly completamente attendibile con l'attributo APTCA.

- `T1` eredita da un tipo `T2` all'esterno del relativo assembly.

- l'assembly `T2` non dispone dell'attributo APTCA e, pertanto, non deve essere ereditabile dai tipi in assembly parzialmente attendibili.

  Un tipo parzialmente attendibile `X` può ereditare da `T1`, che consente l'accesso ai membri ereditati dichiarati in `T2`. Poiché `T2` non dispone dell'attributo APTCA, il relativo tipo derivato immediato (`T1`) deve soddisfare una richiesta di ereditarietà per l'attendibilità totale; `T1` ha attendibilità totale e pertanto soddisfa questa verifica. Il rischio per la sicurezza è dovuto al fatto che `X` non partecipa alla soddisfazione della richiesta di ereditarietà che protegge `T2` dalla sottoclasse non attendibile. Per questo motivo, i tipi con l'attributo APTCA non devono estendere i tipi che non dispongono dell'attributo.

  Un altro problema di sicurezza, probabilmente più comune, è che il tipo derivato (`T1`) può, tramite un errore del programmatore, esporre membri protetti dal tipo che richiede l'attendibilità totale (`T2`). Quando ciò si verifica, i chiamanti non attendibili ottengono l'accesso alle informazioni che devono essere disponibili solo per i tipi completamente attendibili.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Se il tipo segnalato dalla violazione si trova in un assembly che non richiede l'attributo APTCA, rimuoverlo.

 Se l'attributo APTCA è obbligatorio, aggiungere una richiesta di ereditarietà per l'attendibilità totale al tipo. Ciò impedisce l'ereditarietà da tipi non attendibili.

 È possibile correggere una violazione aggiungendo l'attributo APTCA agli assembly dei tipi di base segnalati dalla violazione. Non eseguire questa operazione senza prima eseguire un'intensa revisione della sicurezza di tutto il codice negli assembly e tutto il codice che dipende dagli assembly.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che i membri protetti esposti dal tipo non consentano direttamente o indirettamente ai chiamanti non attendibili di accedere a informazioni riservate, operazioni o risorse che possono essere utilizzate in modo distruttivo.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono utilizzati due assembly e un'applicazione di test per illustrare la vulnerabilità di sicurezza rilevata da questa regola. Il primo assembly non dispone dell'attributo APTCA e non deve essere ereditabile da tipi parzialmente attendibili (rappresentati da `T2` nella discussione precedente).

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>Esempio
 Il secondo assembly, rappresentato da `T1` nella discussione precedente, è completamente attendibile e consente chiamanti parzialmente attendibili.

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>Esempio
 Il tipo di test, rappresentato da `X` nella discussione precedente, si trova in un assembly parzialmente attendibile.

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 Questo esempio produce il seguente output:

 **Scopri le ore di glen 2/22/2003 12:00:00 AM!** 
**da test: Sunny meadow** 
**Meet the Sunny Meadow 2/22/2003 12:00:00 AM!**
## <a name="related-rules"></a>Regole correlate
 [CA2116: I metodi APTCA devono chiamare solo metodi APTCA ](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Vedere anche
 [Linee guida per la codifica sicura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Assembly .NET Framework richiamabili da codice parzialmente attendibile](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [Utilizzo di librerie da codice parzialmente attendibile](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [Richieste di ereditarietà](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)
