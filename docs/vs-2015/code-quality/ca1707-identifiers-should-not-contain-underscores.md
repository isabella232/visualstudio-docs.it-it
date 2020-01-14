---
title: 'CA1707: gli identificatori non devono contenere caratteri di sottolineatura | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5a06e87f8d28ceb225e240d7702a47e00122feea
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919171"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Gli identificatori non devono contenere caratteri di sottolineatura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente su Visual Studio, vedere [CA1707: gli identificatori non devono contenere caratteri di sottolineatura](/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores).

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Categoria|Microsoft.Naming|
|Modifica importante|Suddivisione in caso di generazione di assembly<br /><br /> Senza interruzioni: quando viene generato un parametro di tipo|

## <a name="cause"></a>Causa
 Il nome di un identificatore contiene il carattere di sottolineatura (_).

## <a name="rule-description"></a>Descrizione della regola
 Per convenzione i nomi degli identificatori non contengono il carattere di sottolineatura (_). La regola controlla gli spazi dei nomi, i tipi, i membri e i parametri.

 Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e si aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente esperto nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere tutti i caratteri di sottolineatura dal nome.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
