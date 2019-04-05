---
title: 'CA2121: I costruttori statici devono essere privati | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d7894b4ec0039b28a579239605c22c2397c300f3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955121"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: I costruttori statici devono essere privati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo ha un costruttore statico non è privato.

## <a name="rule-description"></a>Descrizione della regola
 Un costruttore statico, noto anche come un costruttore di classe, viene utilizzato per inizializzare un tipo. Il costruttore statico viene chiamato prima che venga creata la prima istanza del tipo o venga fatto riferimento a qualsiasi membro statico. L'utente non ha alcun controllo su quando viene chiamato il costruttore statico. Se un costruttore statico non è privato, può essere chiamato da codice esterno al sistema. A seconda delle operazioni eseguite nel costruttore, questa situazione può causare comportamenti imprevisti.

 Questa regola viene applicata dai compilatori c# e Visual Basic .NET.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Le violazioni sono in genere causate da una delle azioni seguenti:

- È definito un costruttore statico per il tipo e non hai apportato privata.

- Il compilatore del linguaggio di programmazione aggiunto un costruttore statico predefinito al tipo e non hai apportato privata.

  Per risolvere il tipo prima della violazione, rendere privato il costruttore statico. Per risolvere il tipo di secondo, aggiungere un costruttore statico privato per il tipo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non visualizzare tali violazioni. Se la progettazione software richiede una chiamata esplicita a un costruttore statico, è probabile che la struttura contiene difetti grave e deve essere esaminata.
