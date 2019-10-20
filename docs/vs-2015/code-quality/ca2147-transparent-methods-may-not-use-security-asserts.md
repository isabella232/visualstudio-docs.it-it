---
title: 'CA2147: i metodi Transparent non possono utilizzare asserzioni di sicurezza | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f2bd0042b6f9a8e46939ab34c86294218fb79f4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610165"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Il codice Transparent non può utilizzare asserzioni di sicurezza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Al codice contrassegnato come <xref:System.Security.SecurityTransparentAttribute> non sono concesse autorizzazioni sufficienti per l'asserzione.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola analizza tutti i metodi e i tipi in un assembly che è 100% trasparente o misto trasparente/critico e contrassegna qualsiasi utilizzo dichiarativo o imperativo di <xref:System.Security.CodeAccessPermission.Assert%2A>.

 In fase di esecuzione, qualsiasi chiamata a <xref:System.Security.CodeAccessPermission.Assert%2A> dal codice trasparente causerà la generazione di un <xref:System.InvalidOperationException>. Questa situazione può verificarsi in assembly trasparenti 100% e anche in assembly Transparent/Critical misti in cui un metodo o un tipo è dichiarato trasparente, ma include un'asserzione dichiarativa o imperativa.

 Il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2,0 ha introdotto una funzionalità denominata *trasparenza*. Singoli metodi, campi, interfacce, classi e tipi possono essere trasparenti o critici.

 Il codice Transparent non è autorizzato a elevare i privilegi di sicurezza. Pertanto, qualsiasi autorizzazione concessa o richiesta viene automaticamente passata attraverso il codice al chiamante o al dominio dell'applicazione host. Esempi di elevazioni includono asserzioni, I LinkDemand, attributo SuppressUnmanagedCode e codice `unsafe`.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per risolvere il problema, contrassegnare il codice che chiama l'asserzione con il <xref:System.Security.SecurityCriticalAttribute> oppure rimuovere l'asserzione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un messaggio da questa regola.

## <a name="example"></a>Esempio
 Questo codice avrà esito negativo se `SecurityTestClass` è trasparente, quando il metodo `Assert` genera un <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Esempio
 Un'opzione consiste nel riesaminare il metodo SecurityTransparentMethod nell'esempio riportato di seguito. se il metodo è considerato sicuro per l'elevazione dei privilegi, contrassegnare SecurityTransparentMethod con sicurezza critica richiede che una sicurezza dettagliata, completa e priva di errori. il controllo deve essere eseguito sul metodo insieme a eventuali chiamate che si verificano all'interno del metodo nell'asserzione:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Un'altra opzione consiste nel rimuovere l'asserzione dal codice e lasciare che le successive autorizzazioni di I/O dei file provengano oltre SecurityTransparentMethod al chiamante. In questo modo vengono abilitati i controlli di sicurezza. In questo caso, non è in genere necessario alcun controllo di sicurezza, perché le richieste di autorizzazione vengono propagate al chiamante e/o al dominio applicazione. Le richieste di autorizzazione sono strettamente controllate con i criteri di sicurezza, l'ambiente host e le concessioni di autorizzazione per l'origine codice.

## <a name="see-also"></a>Vedere anche
 [Avvisi di sicurezza](../code-quality/security-warnings.md)
