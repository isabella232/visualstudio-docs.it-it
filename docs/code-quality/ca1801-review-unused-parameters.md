---
title: 'CA1801: Controllare i parametri non usati'
ms.date: 06/24/2019
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6de48bf273a5c93afcd14e7bab2c5d4c4c4b5a7c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233834"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Controllare i parametri non usati

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni: se il membro non è visibile all'esterno dell'assembly, indipendentemente dalla modifica apportata.<br /><br /> Senza interruzioni: se si modifica il membro per usare il parametro all'interno del corpo.<br /><br /> Suddivisione: se si rimuove il parametro ed è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa

Una firma del metodo include un parametro che non viene usato nel corpo del metodo.

Questa regola non esamina i tipi di metodi seguenti:

- Metodi a cui fa riferimento un delegato.

- Metodi utilizzati come gestori eventi.

- Metodi dichiarati `abstract` con`MustOverride` il modificatore (in Visual Basic).

- Metodi dichiarati `virtual` con`Overridable` il modificatore (in Visual Basic).

- Metodi dichiarati `override` con`Overrides` il modificatore (in Visual Basic).

- Metodi dichiarati `extern` con`Declare` il modificatore (statement in Visual Basic).

Se si usano gli [analizzatori FxCop](install-fxcop-analyzers.md), questa regola non contrassegna i parametri denominati con il simbolo di `_1` [scarto](/dotnet/csharp/discards) , `_`ad esempio,, e `_2`. In questo modo si riduce il rumore di avviso sui parametri necessari per i requisiti di firma, ad esempio un metodo usato come delegato, un parametro con attributi speciali o un parametro il cui valore viene eseguito in modo implicito in fase di esecuzione da un Framework, ma a cui non viene fatto riferimento in codice.

## <a name="rule-description"></a>Descrizione della regola

Esaminare i parametri nei metodi non virtuali che non vengono utilizzati nel corpo del metodo per assicurarsi che non esistano errori di accesso. I parametri inutilizzati comportano costi di manutenzione e di prestazioni.

In alcuni casi, una violazione di questa regola può puntare a un bug di implementazione nel metodo. Ad esempio, il parametro deve essere stato usato nel corpo del metodo. Non visualizzare gli avvisi di questa regola se il parametro deve esistere a causa della compatibilità con le versioni precedenti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rimuovere il parametro inutilizzato (una modifica di rilievo) o utilizzare il parametro nel corpo del metodo (una modifica senza interruzioni).

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola in modo sicuro:

- Nel codice distribuito in precedenza per il quale la correzione sarebbe una modifica di rilievo.

- Per il `this` parametro in un metodo di estensione personalizzato <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=nameWithType>per. Le funzioni nella <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> classe sono statiche, quindi non è necessario accedere al `this` parametro nel corpo del metodo.

## <a name="example"></a>Esempio

Nell'esempio seguente vengono illustrati due metodi. Un metodo viola la regola e l'altro metodo soddisfa la regola.

[!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>Regole correlate

[CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812 Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1804: Rimuovi variabili locali non usate](../code-quality/ca1804-remove-unused-locals.md)
