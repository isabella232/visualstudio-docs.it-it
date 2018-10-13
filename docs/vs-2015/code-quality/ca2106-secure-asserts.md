---
title: 'CA2106: Proteggere asserzioni | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5c4c44fa8773b851ebcc80e47c3f94038b49a653
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287803"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Asserzioni protette
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo asserisce un'autorizzazione e non vengono eseguiti controlli di sicurezza sul chiamante.

## <a name="rule-description"></a>Descrizione della regola
 Quando si asserisce un'autorizzazione di sicurezza senza eseguire alcun controllo di sicurezza, nel codice potrebbero restare punti deboli nella sicurezza. Uno stack di sicurezza si interrompe quando viene dichiarata un'autorizzazione di sicurezza. Se si asserisce un'autorizzazione senza eseguire alcun controllo sul chiamante, il chiamante indirettamente potrebbe eseguire codice con le autorizzazioni. Asserzioni senza controlli di sicurezza sono consentiti solo quando si è certi che l'asserzione non è utilizzabile in modo dannoso. Un'asserzione non provoca problemi se il codice chiamato sia innocuo o gli utenti non è possibile passare informazioni arbitrarie al codice che si chiama.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere una richiesta di sicurezza per il metodo o nel relativo tipo dichiarante.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola solo dopo un'attenta revisione della sicurezza.

## <a name="see-also"></a>Vedere anche
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Linee guida per la generazione di codice sicuro](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)



