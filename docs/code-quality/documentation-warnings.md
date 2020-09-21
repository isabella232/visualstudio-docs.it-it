---
title: Regole della documentazione
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- rules, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f4ec6a0dd154dae89145add26c60a8b1322a444
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808652"
---
# <a name="documentation-rules"></a>Regole della documentazione

Le regole della documentazione supportano la scrittura di librerie ben documentate tramite l'uso corretto di commenti relativi alla [documentazione XML](/dotnet/csharp/codedoc) per le API visibili esternamente.

## <a name="in-this-section"></a>Contenuto della sezione

| Regola | Descrizione |
| - | - |
| [CA1200: Evitare l'uso di tag cref con un prefisso](../code-quality/ca1200.md) | L'attributo [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) in un tag di documentazione XML significa "riferimento al codice". Specifica che il testo all'interno del tag è un elemento di codice, ad esempio un tipo, un metodo o una proprietà. Evitare di usare `cref` i tag con i prefissi, perché impedisce al compilatore di verificare i riferimenti. Impedisce inoltre a Visual Studio Integrated Development Environment (IDE) di trovare e aggiornare questi riferimenti ai simboli durante i refactoring. |

## <a name="see-also"></a>Vedere anche

- [Regole di analisi del codice](../code-quality/code-analysis-for-managed-code-warnings.md)
