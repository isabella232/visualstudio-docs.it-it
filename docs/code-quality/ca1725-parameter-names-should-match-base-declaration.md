---
title: 'CA1725: I nomi dei parametri devono corrispondere alla dichiarazione di base'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75f214809d5bfab660b1d559e21d3de3c5ea75fa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233867"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: I nomi dei parametri devono corrispondere alla dichiarazione di base

|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Category|Microsoft.Naming|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Il nome di un parametro in un override del metodo non corrisponde al nome del parametro nella dichiarazione di base del metodo o al nome del parametro nella dichiarazione di interfaccia del metodo.

Per impostazione predefinita, questa regola esamina solo i metodi visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Una denominazione coerente dei parametri in una gerarchia di override aumenta la funzionalità degli override di metodo. Un nome di parametro in un metodo derivato diverso dal nome nella dichiarazione di base può provocare confusione sulla natura del metodo, ovvero se si tratta di un override del metodo di base o di un nuovo overload del metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rinominare il parametro in modo che corrisponda alla dichiarazione di base. La correzione è una modifica di rilievo per i metodi visibili a COM.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non eliminare un avviso da questa regola, ad eccezione dei metodi visibili a COM nelle librerie che sono state precedentemente spedite.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1725.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (denominazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).