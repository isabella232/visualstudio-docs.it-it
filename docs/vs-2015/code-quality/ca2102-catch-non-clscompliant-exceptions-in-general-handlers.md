---
title: 'CA2102: Individuare le eccezioni non CLSCompliant nei gestori generali | Microsoft Docs'
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
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5c2797b32bbcabd1c63fbfd510aec05c8bf54d21
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877420"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Individuare le eccezioni non conformi a CLS nei gestori generali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Category|Microsoft.Security|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un membro in un assembly che non sia contrassegnato con il <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> o è contrassegnata `RuntimeCompatibility(WrapNonExceptionThrows = false)` contiene un blocco catch che gestisce <xref:System.Exception?displayProperty=fullName> e non contiene un blocco catch generale immediatamente successivo. Questa regola ignora [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] assembly.

## <a name="rule-description"></a>Descrizione della regola
 Un blocco catch che gestisce <xref:System.Exception> intercetta tutte le eccezioni conforme a Common Language Specification (CLS). Tuttavia, non rileva eccezioni non CLS. Non conforme a CLS possono essere generate eccezioni dal codice nativo o da codice gestito che è stato generato da Microsoft intermediate language (MSIL) dell'Assembler. Si noti che il codice c# e [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilatori non consente non conformi a CLS conforme di eccezioni e [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] non intercetta eccezioni non CLS. Se si intende del blocco catch per gestire tutte le eccezioni, usare la sintassi di blocco catch generale seguente.

- C#: `catch {}`

- C++: `catch(...) {}` o `catch(Object^) {}`

  Eccezione non gestita non conformi a CLS conformi diventa un problema di sicurezza quando vengono rimosse le autorizzazioni concesse in precedenza nel blocco catch. Poiché non vengono rilevate eccezioni non CLS, è stato possibile eseguire un metodo dannoso che genera un'eccezione non CLS eccezione compatibile con autorizzazioni elevate.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola quando si desidera intercettare tutte le eccezioni, sostituire o aggiungere un blocco catch generale o contrassegnare l'assembly `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Se le autorizzazioni vengono rimossi in un blocco catch, duplicati in generale la funzionalità blocco catch. Se non è lo scopo di gestire tutte le eccezioni, sostituire il blocco catch che gestisce <xref:System.Exception> con blocchi catch che gestiscono tipi di eccezione specifici.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il blocco try non contiene tutte le istruzioni che possono generare un'eccezione non CLS conforme. Poiché qualsiasi codice nativo o gestito potrebbe generare un non conformi a CLS eccezione conforme, ciò richiede una conoscenza di tutto il codice che può essere eseguito in tutti i percorsi del codice nel blocco try. Si noti che-eccezioni non CLS conformi non vengono generate da common language runtime.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una classe di codice MSIL che genera un'eccezione non CLS conforme.

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

 Compilare gli esempi precedenti, come indicato di seguito.

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Regole correlate
 [CA1031: Non rilevare tipi di eccezione generali](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Vedere anche
 [Le eccezioni e gestione delle eccezioni](http://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) [Ilasm.exe (Assembler IL)](http://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) [eseguendo l'override dei controlli di sicurezza](http://msdn.microsoft.com/en-us/4acdeff5-fc05-41bf-8505-7387cdbfca28) [Language Independence and Language-Independent Components](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



