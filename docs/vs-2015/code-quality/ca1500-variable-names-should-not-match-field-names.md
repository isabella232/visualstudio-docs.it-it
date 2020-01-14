---
title: 'CA1500: i nomi delle variabili non devono corrispondere ai nomi dei campi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5753cc660d626098d234fbce93c0bf0269e52bb3
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919043"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: I nomi delle variabili non devono corrispondere ai nomi dei campi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente su Visual Studio, vedere [CA1500: i nomi delle variabili non devono corrispondere ai nomi dei campi](/visualstudio/code-quality/ca1500-variable-names-should-not-match-field-names).

|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|Categoria|Microsoft.Maintainability|
|Modifica importante|Quando viene attivato in un parametro con lo stesso nome di un campo:<br /><br /> -Senza interruzioni: se il campo e il metodo che dichiara il parametro non possono essere visualizzati all'esterno dell'assembly, indipendentemente dalla modifica apportata.<br />-Overstarting: se si modifica il nome del campo e può essere visualizzato al di fuori dell'assembly.<br />-Overstarting: se si modifica il nome del parametro e il metodo che lo dichiara può essere visualizzato all'esterno dell'assembly.<br /><br /> Quando viene generato in una variabile locale con lo stesso nome di un campo:<br /><br /> -Senza interruzioni: se non è possibile visualizzare il campo all'esterno dell'assembly, indipendentemente dalla modifica apportata.<br />-Senza interruzioni: se si modifica il nome della variabile locale e non si modifica il nome del campo.<br />-Overstarting: se si modifica il nome del campo e questo può essere visualizzato al di fuori dell'assembly.|

## <a name="cause"></a>Causa
 Un metodo di istanza dichiara un parametro o una variabile locale il cui nome corrisponde a un campo di istanza del tipo dichiarante. Per intercettare le variabili locali che violano la regola, è necessario compilare l'assembly testato utilizzando le informazioni di debug e il file di database di programma (con estensione pdb) associato.

## <a name="rule-description"></a>Descrizione della regola
 Quando il nome di un campo di istanza corrisponde a un parametro o a un nome di variabile locale, al campo dell'istanza viene eseguito l'accesso tramite la parola chiave `this` (`Me` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) all'interno del corpo del metodo. Quando si gestisce il codice, è facile dimenticare questa differenza e si presuppone che la variabile Parameter/local faccia riferimento al campo instance, che genera errori. Questo vale soprattutto per i corpi di metodo di lunga durata.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rinominare il parametro o la variabile o il campo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrate due violazioni della regola.

 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/cs/FxCop.Maintainability.VarMatchesField.cs#1)]
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/vb/FxCop.Maintainability.VarMatchesField.vb#1)]
