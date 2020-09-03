---
title: 'CA2121: i costruttori statici devono essere privati | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f95b33e1391ca755a6c0df261fa2bd05bd3c7a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544313"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: I costruttori statici devono essere privati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo dispone di un costruttore statico che non è privato.

## <a name="rule-description"></a>Descrizione della regola
 Un costruttore statico, noto anche come costruttore di classe, viene usato per inizializzare un tipo. Il costruttore statico viene chiamato prima che venga creata la prima istanza del tipo o venga fatto riferimento a qualsiasi membro statico. L'utente non ha alcun controllo sul momento in cui viene chiamato il costruttore statico. Se un costruttore statico non è privato, può essere chiamato da codice esterno al sistema. A seconda delle operazioni eseguite nel costruttore, questa situazione può causare comportamenti imprevisti.

 Questa regola viene applicata dai compilatori C# e Visual Basic .NET.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Le violazioni sono in genere dovute a una delle azioni seguenti:

- È stato definito un costruttore statico per il tipo e non è stato reso privato.

- Il compilatore del linguaggio di programmazione ha aggiunto un costruttore statico predefinito al tipo e non è stato reso privato.

  Per correggere il primo tipo di violazione, rendere privato il costruttore statico. Per correggere il secondo tipo, aggiungere un costruttore statico privato al tipo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere queste violazioni. Se la progettazione del software richiede una chiamata esplicita a un costruttore statico, è probabile che la progettazione contenga gravi errori e che sia necessario esaminarla.
