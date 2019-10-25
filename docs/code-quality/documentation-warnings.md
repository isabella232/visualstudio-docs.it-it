---
title: Avvisi della documentazione
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation warnings
- managed code analysis warnings, documentation warnings
- warnings, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4946c69bbbe4bf1c240967ebd93ef58cfa79e333
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2019
ms.locfileid: "72807105"
---
# <a name="documentation-warnings"></a>Avvisi della documentazione

Gli avvisi relativi alla documentazione supportano la scrittura di librerie ben documentate tramite l'uso corretto di commenti relativi alla [documentazione XML](/dotnet/csharp/codedoc) per le API visibili esternamente.

## <a name="in-this-section"></a>In questa sezione

| Regola | Descrizione |
| - | - |
| [Ca1200: evitare di usare tag cref con un prefisso](../code-quality/ca1200.md) | L'attributo [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) in un tag di documentazione XML significa "riferimento al codice". Specifica che il testo all'interno del tag è un elemento di codice, ad esempio un tipo, un metodo o una proprietà. Evitare di usare i tag `cref` con i prefissi, perché impedisce al compilatore di verificare i riferimenti. Impedisce inoltre a Visual Studio Integrated Development Environment (IDE) di trovare e aggiornare questi riferimenti ai simboli durante i refactoring. |

## <a name="see-also"></a>Vedere anche

- [Avvisi di analisi del codice](../code-quality/code-analysis-for-managed-code-warnings.md)
