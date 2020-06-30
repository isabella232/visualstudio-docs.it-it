---
title: 'CA2106: asserzioni protette | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: eb0e097c2f13fa9d9279a5f3e9761a53cb6e4b1d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547745"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Asserzioni protette
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo asserisce un'autorizzazione e non vengono eseguiti controlli di sicurezza sul chiamante.

## <a name="rule-description"></a>Descrizione della regola
 Quando si asserisce un'autorizzazione di sicurezza senza eseguire alcun controllo di sicurezza, nel codice potrebbero restare punti deboli nella sicurezza. Un percorso dello stack di sicurezza si interrompe quando viene dichiarata un'autorizzazione di sicurezza. Se si dichiara un'autorizzazione senza eseguire controlli sul chiamante, il chiamante potrebbe eseguire indirettamente il codice utilizzando le autorizzazioni. Le asserzioni senza controlli di sicurezza sono consentite solo quando si è certi che l'asserzione non può essere usata in modo dannoso. Un'asserzione è innocua se il codice chiamato è innocuo o se gli utenti non possono passare informazioni arbitrarie al codice chiamato.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere una richiesta di sicurezza al metodo o al relativo tipo dichiarante.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola solo dopo un'attenta revisione della sicurezza.

## <a name="see-also"></a>Vedere anche
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Linee guida per la generazione di codice sicuro](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
