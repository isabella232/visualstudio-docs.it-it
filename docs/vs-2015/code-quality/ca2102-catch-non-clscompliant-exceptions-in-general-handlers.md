---
title: 'CA2102: intercettare le eccezioni non CLSCompliant nei gestori generali | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 051b59183a761477476269480ecdf83ccbf0cb37
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652166"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Individuare le eccezioni non conformi a CLS nei gestori generali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Category|Microsoft.Security|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un membro di un assembly che non è contrassegnato con <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> o è contrassegnato `RuntimeCompatibility(WrapNonExceptionThrows = false)` contiene un blocco catch che gestisce <xref:System.Exception?displayProperty=fullName> e non contiene un blocco catch generale immediatamente successivo. Questa regola ignora gli assembly [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].

## <a name="rule-description"></a>Descrizione della regola
 Un blocco catch che gestisce <xref:System.Exception> intercetta tutte le eccezioni conformi a CLS (Common Language Specification). Tuttavia, non intercetta le eccezioni non conformi a CLS. Le eccezioni non conformi a CLS possono essere generate dal codice nativo o dal codice gestito generato dall'assembler MSIL (Microsoft Intermediate Language). Si noti che C# i compilatori e [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] non consentono la generazione di eccezioni non conformi a cls e [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] non intercetta le eccezioni non conformi a CLS. Se lo scopo del blocco catch è quello di gestire tutte le eccezioni, utilizzare la seguente sintassi generale del blocco catch.

- C#: `catch {}`

- C++: `catch(...) {}` o `catch(Object^) {}`

  Un'eccezione non gestita non conforme a CLS diventa un problema di sicurezza quando le autorizzazioni consentite in precedenza vengono rimosse nel blocco catch. Poiché le eccezioni non conformi a CLS non vengono rilevate, un metodo dannoso che genera un'eccezione non conforme a CLS può essere eseguito con autorizzazioni elevate.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola quando lo scopo è intercettare tutte le eccezioni, sostituire o aggiungere un blocco catch generale oppure contrassegnare l'assembly `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Se le autorizzazioni vengono rimosse nel blocco catch, duplicare la funzionalità nel blocco catch generale. Se non è possibile gestire tutte le eccezioni, sostituire il blocco catch che gestisce <xref:System.Exception> con blocchi catch che gestiscono tipi di eccezione specifici.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il blocco try non contiene istruzioni che potrebbero generare un'eccezione non conforme a CLS. Poiché qualsiasi codice nativo o gestito potrebbe generare un'eccezione non conforme a CLS, è necessario conoscere tutto il codice che può essere eseguito in tutti i percorsi del codice all'interno del blocco try. Si noti che le eccezioni non conformi a CLS non vengono generate dal Common Language Runtime.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una classe MSIL che genera un'eccezione non conforme a CLS.

```
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

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che contiene un blocco catch generale che soddisfa la regola.

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.CatchNonClsCompliantException/cs/FxCop.Security.CatchNonClsCompliantException.cs#1)]

 Compilare gli esempi precedenti come indicato di seguito.

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Regole correlate
 [CA1031: Non rilevare tipi di eccezione generali](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Vedere anche
 [Eccezioni e gestione delle eccezioni](https://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) [Ilasm. exe (assembler il)](https://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) [override dei controlli di sicurezza](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [indipendenza dal linguaggio e componenti indipendenti dal linguaggio](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
