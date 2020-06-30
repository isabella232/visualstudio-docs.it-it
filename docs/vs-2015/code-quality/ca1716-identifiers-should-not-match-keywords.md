---
title: 'CA1716: gli identificatori non devono corrispondere a parole chiave | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 67a3588a857a0eea7d338217f975ed593dfdad52
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543702"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Gli identificatori non devono corrispondere a parole chiave
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Category|Microsoft. Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il nome di uno spazio dei nomi, di un tipo o di un viritual o di un membro di interfaccia corrisponde a una parola chiave riservata in un linguaggio di programmazione.

## <a name="rule-description"></a>Descrizione della regola
 Gli identificatori per gli spazi dei nomi, i tipi e i membri virtuali e di interfaccia non devono corrispondere a parole chiave definite da linguaggi che hanno come destinazione il Common Language Runtime. A seconda del linguaggio usato e della parola chiave, gli errori del compilatore e le ambiguità possono rendere la libreria difficile da usare.

 Questa regola consente di controllare le parole chiave nelle seguenti lingue:

- Visual Basic

- C#

- C++/CLI

  Il confronto senza distinzione tra maiuscole e minuscole viene usato per [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] le parole chiave e il confronto con distinzione tra maiuscole e minuscole viene usato per gli altri

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Selezionare un nome che non sia presente nell'elenco delle parole chiave.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se si è certi che l'identificatore non consentirà di confondere gli utenti dell'API e che la libreria sia utilizzabile in tutte le lingue disponibili nell' [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .
