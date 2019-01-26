---
title: 'CA2102: Individuare le eccezioni non CLSCompliant nei gestori generali'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a831e771ce771ef492089dae14f719de6429e32
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002600"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Individuare le eccezioni non CLSCompliant nei gestori generali

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Category|Microsoft.Security|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un membro in un assembly che non sia contrassegnato con il <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> o è contrassegnata `RuntimeCompatibility(WrapNonExceptionThrows = false)` contiene un blocco catch che gestisce <xref:System.Exception?displayProperty=fullName> e non contiene un blocco catch generale immediatamente successivo. Questa regola ignora [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] assembly.

## <a name="rule-description"></a>Descrizione della regola

Un blocco catch che gestisce <xref:System.Exception> intercetta tutte le eccezioni conforme a Common Language Specification (CLS). Tuttavia, non rileva eccezioni non CLS. Non conforme a CLS possono essere generate eccezioni dal codice nativo o da codice gestito che è stato generato da Microsoft intermediate language (MSIL) dell'Assembler. Si noti che il codice c# e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilatori non consente non conformi a CLS conforme di eccezioni e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] non intercetta eccezioni non CLS. Se si intende del blocco catch per gestire tutte le eccezioni, usare la sintassi di blocco catch generale seguente.

- C#: `catch {}`

- C++: `catch(...) {}` o `catch(Object^) {}`

Eccezione non gestita non conformi a CLS conformi diventa un problema di sicurezza quando vengono rimosse le autorizzazioni concesse in precedenza nel blocco catch. Poiché non vengono rilevate eccezioni non CLS, è stato possibile eseguire un metodo dannoso che genera un'eccezione non CLS eccezione compatibile con autorizzazioni elevate.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola quando si desidera intercettare tutte le eccezioni, sostituire o aggiungere un blocco catch generale o contrassegnare l'assembly `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Se le autorizzazioni vengono rimossi in un blocco catch, duplicati in generale la funzionalità blocco catch. Se non è lo scopo di gestire tutte le eccezioni, sostituire il blocco catch che gestisce <xref:System.Exception> con blocchi catch che gestiscono tipi di eccezione specifici.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola se il blocco try non contiene tutte le istruzioni che possono generare un'eccezione non CLS conforme. Poiché qualsiasi codice nativo o gestito potrebbe generare un non conformi a CLS eccezione conforme, ciò richiede una conoscenza di tutto il codice che può essere eseguito in tutti i percorsi del codice nel blocco try. Si noti che-eccezioni non CLS conformi non vengono generate da common language runtime.

## <a name="example-1"></a>Esempio 1

Nell'esempio seguente viene illustrata una classe di codice MSIL che genera un'eccezione non CLS conforme.

```cpp
.assembly ThrowNonClsCompliantException {}
.class public auto ansi beforefieldinit ThrowsExceptions
{
   .method public hidebysig static void
         ThrowNonClsException() cil managed
   {
      .maxstack  1
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()
      IL_0005:  throw
   }
}
```

## <a name="example-2"></a>Esempio 2

Nell'esempio seguente viene illustrato un metodo che contiene un blocco catch generale che soddisfa la regola.

[!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

Compilare gli esempi precedenti, come indicato di seguito.

```cpp
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Regole correlate

[CA1031: Non rilevare tipi di eccezione generali](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Vedere anche

- [Eccezioni e gestione delle eccezioni](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)
- [Ilasm.exe (Assembler IL)](/dotnet/framework/tools/ilasm-exe-il-assembler)
- [Indipendenza del linguaggio e componenti indipendenti dal linguaggio](/dotnet/standard/language-independence-and-language-independent-components)