---
title: 'CA1812: evitare classi interne prive di istanze | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f5a36ee8cffc221d15243ff72e2e71558e867319
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645401"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Evitare classi interne prive di istanze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Category|Microsoft. performance|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un'istanza di un tipo a livello di assembly non viene creata dal codice nell'assembly.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola tenta di individuare una chiamata a uno dei costruttori del tipo e segnala una violazione se non viene trovata alcuna chiamata.

 I tipi seguenti non vengono esaminati da questa regola:

- Tipi valore

- Tipi astratti

- Enumerazioni

- Delegati

- Tipi di matrici emesse dal compilatore

- Tipi di cui non è possibile creare un'istanza e che definiscono solo i metodi `static` (`Shared` in Visual Basic).

  Se si applicano <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> all'assembly analizzato, questa regola non verrà eseguita su alcun costruttore contrassegnato come `internal` perché non è possibile stabilire se un campo è utilizzato da un altro assembly di `friend`.

  Anche se non è possibile aggirare questa limitazione nell'analisi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] codice, l'FxCop autonomo esterno si verificherà sui costruttori interni se ogni assembly `friend` è presente nell'analisi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il tipo o aggiungere il codice che lo utilizza. Se il tipo contiene solo metodi statici, aggiungere uno degli elementi seguenti al tipo per impedire al compilatore di emettere un costruttore di istanza pubblica predefinito:

- Un costruttore privato per i tipi destinati a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] versioni 1,0 e 1,1.

- Il modificatore `static` (`Shared` in Visual Basic) per i tipi destinati [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola in modo sicuro. Si consiglia di non visualizzare più questo avviso nelle situazioni seguenti:

- La classe viene creata tramite metodi di reflection ad associazione tardiva, ad esempio <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- La classe viene creata automaticamente dalla fase di esecuzione o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Ad esempio, le classi che implementano <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> o <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- La classe viene passata come parametro di tipo generico con un nuovo vincolo. Nell'esempio seguente, ad esempio, verrà generata questa regola.

  ```csharp
  internal class MyClass
  {
      public DoSomething()
      {
      }
  }
  public class MyGeneric<T> where T : new()
  {
      public T Create()
      {
          return new T();
      }
  }
  // [...]
  MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
  mc.Create();
  ```

  In questi casi, è consigliabile non visualizzare questo avviso.

## <a name="related-rules"></a>Regole correlate
 [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801: Rivedere i parametri non usati](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Rimuovere locali non usati](../code-quality/ca1804-remove-unused-locals.md)
