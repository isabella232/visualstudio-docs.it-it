---
title: 'CA1722: gli identificatori non devono contenere un prefisso errato | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0f50c5aca934886f03a54692d98a6be3f8bb5562
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671586"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Gli identificatori non devono contenere il prefisso non corretto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Category|Microsoft. Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un identificatore ha un prefisso errato.

## <a name="rule-description"></a>Descrizione della regola
 Per convenzione, solo determinati elementi di programmazione presentano nomi che iniziano con un prefisso specifico.

 I nomi dei tipi non hanno un prefisso specifico e non devono essere preceduti da un prefisso ' c'. Questa regola segnala le violazioni dei nomi dei tipi, ad esempio ' CMyClass ', e non segnala violazioni per i nomi dei tipi come ' cache '.

 Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e si aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente esperto nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere il prefisso dall'identificatore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA1715: Gli identificatori devono contenere il prefisso corretto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)
