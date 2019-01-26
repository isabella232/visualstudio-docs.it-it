---
title: 'CA1500: I nomi delle variabili non devono corrispondere ai nomi dei campi'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 56deb12f98767a62aed55f4e979ff666200ea044
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54995141"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: I nomi delle variabili non devono corrispondere ai nomi dei campi

|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|Category|Microsoft.Maintainability|
|Modifica importante|Quando viene attivato in un parametro che ha lo stesso nome di un campo:<br /><br /> Unificatori - se il campo e il metodo che dichiara il parametro non può essere visualizzate all'esterno dell'assembly, indipendentemente dalle modifiche apportate.<br />Sostanziale - Se si modifica il nome del campo e può essere visualizzato all'esterno dell'assembly.<br />-Sostanziale: se si modifica il nome del parametro e il metodo che lo dichiara può essere visualizzato all'esterno dell'assembly.<br /><br /> Quando viene attivato su una variabile locale avente lo stesso nome di un campo:<br /><br /> Unificatori - se il campo non può essere visibile all'esterno dell'assembly, indipendentemente dalle modifiche apportate.<br />Unificatori - se si modifica il nome della variabile locale e non modificare il nome del campo.<br />-Sostanziale: se si modifica il nome del campo e può essere visualizzato all'esterno dell'assembly.|

## <a name="cause"></a>Causa

Un metodo di istanza dichiara un parametro o una variabile locale il cui nome corrisponde a un campo di istanza del tipo dichiarante. Per intercettare le variabili locali che violano la regola, l'assembly testata deve essere compilato usando le informazioni di debug e il file di database (con estensione pdb) del programma associato deve essere disponibile.

## <a name="rule-description"></a>Descrizione della regola

Quando il nome di un campo di istanza corrisponde a un parametro o un nome di variabile locale, il campo di istanza è accessibile tramite il `this` (`Me` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) (parola chiave) all'interno del corpo del metodo. Quando la gestione del codice, è facile dimenticare di questa differenza, supponendo che la variabile di parametri/elemento locale fa riferimento al campo di istanza, generando errori. Ciò vale soprattutto per i corpi di metodo di lunga durata.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rinominare il parametro/variabile o campo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio

L'esempio seguente illustra due violazioni della regola.

[!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
[!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]