---
title: 'CA2118: Esaminare la sintassi di SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: eb76233e968ad8212d15fbcc815c31ffd0f1838a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059175"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: Verificare la sintassi di SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un membro o un tipo pubblico o protetto presenta il <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> attributo.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> modifica il comportamento del sistema di sicurezza predefinito per i membri che eseguono codice non gestito mediante la chiamata di piattaforma o di interoperabilità COM. In genere, il sistema esegue una [dati e modellazione](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) autorizzazione per codice non gestito. Questa richiesta si verifica in fase di esecuzione per ogni chiamata del membro e controlla ogni chiamante nello stack di chiamate per l'autorizzazione. Quando l'attributo è presente, il sistema esegue una [linking](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) per l'autorizzazione: vengono controllate le autorizzazioni del chiamante immediato quando il chiamante viene compilato tramite JIT.

 Questo attributo viene principalmente usato per aumentare le prestazioni. L'aumento delle prestazioni, tuttavia, comporta notevoli rischi in termini di sicurezza. Se si inserisce l'attributo in membri pubblici che chiamano i metodi nativi, i chiamanti nello stack di chiamate (diverso dal chiamante immediato) non sono necessario l'autorizzazione di codice non gestito per eseguire codice non gestito. A seconda delle azioni del membro pubblico e la gestione dell'input, potrebbe consentire ai chiamanti non attendibili per accedere alla funzionalità in genere limitate al codice attendibile.

 Il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] si basa su controlli di sicurezza per impedire che i chiamanti abbiano accesso diretto a spazio degli indirizzi del processo corrente. Poiché questo attributo Ignora sicurezza normale, il codice comporta un grave rischio se può essere utilizzato per leggere o scrivere nella memoria del processo. Si noti che il rischio non è limitato ai metodi che forniscono intenzionalmente l'accesso per l'elaborazione di memoria. è inoltre presente in qualsiasi scenario in cui codice dannoso può ottenere l'accesso con qualsiasi mezzo, ad esempio, fornendo input sorprendente, in formato non valido o non valido.

 I criteri di sicurezza predefinito non concedere l'autorizzazione di codice non gestito a un assembly a meno che non venga eseguito dal computer locale o è un membro di uno dei seguenti gruppi:

- Il gruppo di codice di area Computer

- Gruppo di codice nome sicuro di Microsoft

- Gruppo di codice nome sicuro di ECMA

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Esaminare attentamente il codice per garantire che questo attributo è assolutamente necessario. Se si ha familiarità con la sicurezza di codice gestito o non supportano le implicazioni di sicurezza di questo attributo, rimuoverlo dal codice. Se l'attributo è obbligatorio, è necessario assicurarsi che i chiamanti non è possibile usare il codice da utenti malintenzionati. Se il codice non ha l'autorizzazione per eseguire codice non gestito, questo attributo non ha alcun effetto e deve essere rimosso.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che il codice non fornisce i chiamanti accesso alle operazioni native o risorse che possono essere usate in modo distruttivo.

## <a name="example"></a>Esempio
 Nell'esempio seguente viola la regola.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesDoNotSuppress/cs/FxCop.Security.TypesDoNotSuppress.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente, il `DoWork` metodo fornisce un percorso di codice accessibile pubblicamente per il metodo di chiamata `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PInvokeAndSuppress/cs/FxCop.Security.PInvokeAndSuppress.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente, il metodo pubblico `DoDangerousThing` provoca una violazione. Per risolvere la violazione `DoDangerousThing` deve essere reso privato, e l'accesso a esso deve avvenire tramite un metodo pubblico è protetto da una richiesta di sicurezza, come illustrato di `DoWork` (metodo).

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress/cs/FxCop.Security.TypeInvokeAndSuppress.cs#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> [Linee guida per la generazione di codice sicuro](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [ottimizzazioni della sicurezza](http://msdn.microsoft.com/cf255069-d85d-4de3-914a-e4625215a7c0) [dati e modellazione](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [le richieste di collegamento](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
