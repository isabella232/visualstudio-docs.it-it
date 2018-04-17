---
title: 'CA2121: I costruttori statici devono essere privati | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6248371d4089b4d1e651a9ea3c391d293b94f40c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: I costruttori statici devono essere privati
|||  
|-|-|  
|TypeName|StaticConstructorsShouldBePrivate|  
|CheckId|CA2121|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo ha un costruttore statico non è privato.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Un costruttore statico, noto anche come un costruttore di classe, viene utilizzato per inizializzare un tipo. Il costruttore statico viene chiamato prima che venga creata la prima istanza del tipo o venga fatto riferimento a qualsiasi membro statico. L'utente non dispone di alcun controllo sulla quando viene chiamato il costruttore statico. Se un costruttore statico non è privato, può essere chiamato da codice esterno al sistema. A seconda delle operazioni eseguite nel costruttore, questa situazione può causare comportamenti imprevisti.  
  
 Questa regola viene applicata dai compilatori c# e Visual Basic.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Le violazioni vengono in genere causate da una delle azioni seguenti:  
  
-   Viene definito un costruttore statico per il tipo e non privata.  
  
-   Il compilatore di linguaggio di programmazione l'aggiunta di un costruttore statico predefinito al tipo e non renderlo privato.  
  
 Per risolvere il primo tipo di violazione, rendere privato il costruttore statico. Per correggere il secondo tipo, aggiungere un costruttore statico privato al tipo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere tali violazioni. Se la progettazione software richiede una chiamata esplicita a un costruttore statico, è probabile che la struttura contiene gravi difetti e deve essere riviste.