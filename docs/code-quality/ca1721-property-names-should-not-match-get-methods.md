---
title: 'CA1721: I nomi delle proprietà non devono corrispondere ai metodi get'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e2b9c878f630d9e739efc46380ecdfc6555880be
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57869219"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: I nomi delle proprietà non devono corrispondere ai metodi get

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Il nome di un membro inizia con 'Get' e in caso contrario, corrisponde al nome di una proprietà. Ad esempio, un tipo che contiene un metodo denominato "GetColor" e una proprietà denominata 'Color' causare una violazione della regola.

Per impostazione predefinita, questa regola cerca solo in membri visibili esternamente e le proprietà, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

I metodi "Get" e le proprietà devono avere nomi indicano chiaramente la distinzione tra le funzioni.

Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. Questa coerenza consente di ridurre il tempo necessario per informazioni su una nuova libreria di software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Modificare il nome in modo che il nome di un metodo che ha il prefisso 'Get' non corrisponde.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.

> [!NOTE]
> Questo avviso può essere escluso se il metodo "Get" è causato dall'implementazione IExtenderProvider (interfaccia).

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```
dotnet_code_quality.ca1721.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (denominazione). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

L'esempio seguente contiene un metodo e proprietà che violano questa regola.

[!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
[!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>Regole correlate

- [CA1024: Utilizzare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)