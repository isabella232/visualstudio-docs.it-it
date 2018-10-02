---
title: 'CA1722: Gli identificatori non devono contenere il prefisso non corretto | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: 83843a7713adf3d0c3680470df05bb378c797d38
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590049"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Gli identificatori non devono contenere il prefisso non corretto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1722: gli identificatori non devono contenere il prefisso non corretto](https://docs.microsoft.com/visualstudio/code-quality/ca1722-identifiers-should-not-have-incorrect-prefix).

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



