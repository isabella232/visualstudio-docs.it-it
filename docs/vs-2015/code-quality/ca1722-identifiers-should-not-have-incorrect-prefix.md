---
title: 'CA1722: Gli identificatori non devono contenere il prefisso non corretto | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0c9aa6600578da0d9868df2ecff9992bff9e818c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68191238"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Gli identificatori non devono contenere il prefisso non corretto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un identificatore ha un prefisso non corretto.

## <a name="rule-description"></a>Descrizione della regola
 Per convenzione, solo determinati elementi di programmazione presentano nomi che iniziano con un prefisso specifico.

 I nomi di tipo non è un prefisso specifico e non devono essere preceduti da "C". Questa regola segnala le violazioni per i nomi dei tipi, ad esempio 'CMyClass' e non segnalare le violazioni per i nomi dei tipi, ad esempio "Cache".

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere il prefisso dall'identificatore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA1715: Gli identificatori devono contenere il prefisso corretto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)
