---
title: 'CA1500: I nomi delle variabili non devono corrispondere ai nomi di campo | Microsoft Docs'
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
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fdac60aa7b3fb37f45cff7c1c9e5f17920efed18
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173940"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: I nomi delle variabili non devono corrispondere ai nomi dei campi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio 2017, vedere [CA1500: i nomi delle variabili non devono corrispondere ai nomi di campo](https://docs.microsoft.com/visualstudio/code-quality/ca1500-variable-names-should-not-match-field-names) su docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|VariableNamesShouldNotMatchFieldNames|  
|CheckId|CA1500|  
|Category|Microsoft.Maintainability|  
|Modifica importante|Quando viene attivato in un parametro che ha lo stesso nome di un campo:<br /><br /> Unificatori - se il campo e il metodo che dichiara il parametro non può essere visualizzate all'esterno dell'assembly, indipendentemente dalle modifiche apportate.<br />Sostanziale - Se si modifica il nome del campo e può essere visualizzato all'esterno dell'assembly.<br />-Sostanziale: se si modifica il nome del parametro e il metodo che lo dichiara può essere visualizzato all'esterno dell'assembly.<br /><br /> Quando viene attivato su una variabile locale avente lo stesso nome di un campo:<br /><br /> Unificatori - se il campo non può essere visibile all'esterno dell'assembly, indipendentemente dalle modifiche apportate.<br />Unificatori - se si modifica il nome della variabile locale e non modificare il nome del campo.<br />-Sostanziale: se si modifica il nome del campo e può essere visualizzato all'esterno dell'assembly.|  
  
## <a name="cause"></a>Causa  
 Un metodo di istanza dichiara un parametro o una variabile locale il cui nome corrisponde a un campo di istanza del tipo dichiarante. Per intercettare le variabili locali che violano la regola, l'assembly testata deve essere compilato usando le informazioni di debug e il file di database (con estensione pdb) del programma associato deve essere disponibile.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Quando il nome di un campo di istanza corrisponde a un parametro o un nome di variabile locale, il campo di istanza è accessibile tramite il `this` (`Me` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) (parola chiave) all'interno del corpo del metodo. Quando la gestione del codice, è facile dimenticare di questa differenza, supponendo che la variabile di parametri/elemento locale fa riferimento al campo di istanza, generando errori. Ciò vale soprattutto per i corpi di metodo di lunga durata.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rinominare il parametro/variabile o campo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra due violazioni della regola.  
  
 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/cs/FxCop.Maintainability.VarMatchesField.cs#1)]
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/vb/FxCop.Maintainability.VarMatchesField.vb#1)]

