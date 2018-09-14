---
title: 'CA2106: Asserzioni protette'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ff16cdce4be04bd076c93763fb6a22d2721675f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551782"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Asserzioni protette

|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo asserisce un'autorizzazione e non esegue alcuna verifica di sicurezza sul chiamante.

## <a name="rule-description"></a>Descrizione della regola
 Quando si asserisce un'autorizzazione di sicurezza senza eseguire alcun controllo di sicurezza, nel codice potrebbero restare punti deboli nella sicurezza. Uno stack di sicurezza si interrompe quando viene dichiarata un'autorizzazione di sicurezza. Se si asserisce un'autorizzazione senza eseguire alcun controllo sul chiamante, il chiamante indirettamente potrebbe eseguire codice con le autorizzazioni. Asserzioni senza controlli di sicurezza sono consentiti se si conosce che l'asserzione non può essere usata in modo dannoso. Un'asserzione non crea problemi se il codice chiamato sia innocuo o se gli utenti non è possibile passare informazioni arbitrarie al codice che si chiama.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere una richiesta di sicurezza per il metodo o nel relativo tipo dichiarante.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Eliminare un avviso da questa regola solo dopo un'attenta revisione della sicurezza.

## <a name="see-also"></a>Vedere anche

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)