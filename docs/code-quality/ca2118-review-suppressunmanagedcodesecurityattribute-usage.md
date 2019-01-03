---
title: 'CA2118: Esaminare la sintassi di SuppressUnmanagedCodeSecurityAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 1bc65c6c27a22e39e48cb69dbe32108692d5ffea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860820"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: Esaminare la sintassi di SuppressUnmanagedCodeSecurityAttribute

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un membro o un tipo pubblico o protetto presenta il <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> attributo.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> modifica il comportamento del sistema di sicurezza predefinito per i membri che eseguono codice non gestito mediante la chiamata di piattaforma o di interoperabilità COM. In genere, il sistema esegue una [dati e modellazione](/dotnet/framework/data/index) autorizzazione per codice non gestito. Questa richiesta si verifica in fase di esecuzione per ogni chiamata del membro e controlla ogni chiamante nello stack di chiamate per l'autorizzazione. Quando l'attributo è presente, il sistema esegue una [linking](/dotnet/framework/misc/link-demands) per l'autorizzazione: vengono controllate le autorizzazioni del chiamante immediato quando il chiamante viene compilato tramite JIT.

 Questo attributo viene principalmente usato per aumentare le prestazioni. L'aumento delle prestazioni, tuttavia, comporta notevoli rischi in termini di sicurezza. Se si inserisce l'attributo in membri pubblici che chiamano i metodi nativi, i chiamanti nello stack di chiamate (diverso dal chiamante immediato) non sono necessario l'autorizzazione di codice non gestito per eseguire codice non gestito. A seconda delle azioni del membro pubblico e la gestione dell'input, potrebbe consentire ai chiamanti non attendibili per accedere alla funzionalità in genere limitate al codice attendibile.

 .NET Framework si basa su controlli di sicurezza per impedire che i chiamanti abbiano accesso diretto a spazio degli indirizzi del processo corrente. Poiché questo attributo Ignora sicurezza normale, il codice comporta un grave rischio se può essere utilizzato per leggere o scrivere nella memoria del processo. Si noti che il rischio non è limitato ai metodi che forniscono intenzionalmente l'accesso per l'elaborazione di memoria. è inoltre presente in qualsiasi scenario in cui codice dannoso può ottenere l'accesso con qualsiasi mezzo, ad esempio, fornendo input sorprendente, in formato non valido o non valido.

 I criteri di sicurezza predefinito non concedere l'autorizzazione di codice non gestito a un assembly a meno che non venga eseguito dal computer locale o è un membro di uno dei seguenti gruppi:

- Il gruppo di codice di area Computer

- Gruppo di codice nome sicuro di Microsoft

- Gruppo di codice nome sicuro di ECMA

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Esaminare attentamente il codice per garantire che questo attributo è assolutamente necessario. Se si ha familiarità con la sicurezza di codice gestito o non supportano le implicazioni di sicurezza di questo attributo, rimuoverlo dal codice. Se l'attributo è obbligatorio, è necessario assicurarsi che i chiamanti non è possibile usare il codice da utenti malintenzionati. Se il codice non ha l'autorizzazione per eseguire codice non gestito, questo attributo non ha alcun effetto e deve essere rimosso.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che il codice non fornisce i chiamanti accesso alle operazioni native o risorse che possono essere usate in modo distruttivo.

## <a name="example-1"></a>Esempio 1
 Nell'esempio seguente viola la regola.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]

## <a name="example-2"></a>Esempio 2
 Nell'esempio seguente, il `DoWork` metodo fornisce un percorso di codice accessibile pubblicamente per il metodo di chiamata `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]

## <a name="example-3"></a>Esempio 3
 Nell'esempio seguente, il metodo pubblico `DoDangerousThing` provoca una violazione. Per risolvere la violazione `DoDangerousThing` deve essere reso privato, e l'accesso a esso deve avvenire tramite un metodo pubblico è protetto da una richiesta di sicurezza, come illustrato di `DoWork` (metodo).

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>
- [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)
- [Dati e modellazione](/dotnet/framework/data/index)
- [Richieste di collegamento](/dotnet/framework/misc/link-demands)