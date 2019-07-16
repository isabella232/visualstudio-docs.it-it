---
title: 'CA2147: I metodi Transparent non possono usare la sicurezza delle asserzioni | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3e8ac2e907e3c13a019e5f534faf86ae425ae30a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142635"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: I metodi Transparent non possono usare asserzioni di sicurezza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il codice che è contrassegnato come <xref:System.Security.SecurityTransparentAttribute> non vengono concesse autorizzazioni sufficienti per l'asserzione.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola analizza tutti i metodi e tipi in un assembly che entrambi 100% transparent o una combinazione trasparente/critico e contrassegna l'utilizzo dichiarativo o imperativo di <xref:System.Security.CodeAccessPermission.Assert%2A>.

 In fase di esecuzione delle chiamate a <xref:System.Security.CodeAccessPermission.Assert%2A> da codice trasparente causerà un <xref:System.InvalidOperationException> generata. Ciò può verificarsi in entrambi gli assembly trasparente a 100% e anche in un assembly trasparente/critico misti in cui un metodo o un tipo viene dichiarato trasparente, ma include un dichiarativo o imperativo di Assert.

 Il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 ha introdotto una funzionalità denominata *trasparenza*. Tipi, campi, le interfacce, classi e i singoli metodi possono essere trasparente o critico.

 Il codice trasparente non è consentito di elevare i privilegi di sicurezza. Pertanto, tutte le autorizzazioni concesse o richiesta viene automaticamente vengono passate tramite il codice al dominio dell'applicazione chiamante o l'host. Le elevazioni sono esempi di istruzioni Assert, i LinkDemand, SuppressUnmanagedCode e `unsafe` codice.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per risolvere il problema, contrassegnare il codice che chiama il metodo Assert con il <xref:System.Security.SecurityCriticalAttribute>, o rimuovere l'asserzione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un messaggio da questa regola.

## <a name="example"></a>Esempio
 Questo codice avrà esito negativo se `SecurityTestClass` sono trasparenti, quando il `Assert` metodo genera un <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Esempio
 Una possibilità consiste nel revisione del codice il metodo SecurityTransparentMethod nell'esempio seguente e se il metodo è considerato sicuro per l'elevazione dei privilegi, contrassegnarlo con secure strategica ciò richiede che un dettagliati, completato e privi di errori di sicurezza controllo deve essere eseguito sul metodo insieme a eventuali callout che si verificano all'interno del metodo sotto il functoid asserzione:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Un'altra opzione consiste nel rimuovere l'asserzione dal codice e consentire qualsiasi file successive i/o autorizzazione richieste SecurityTransparentMethod al chiamante. In questo modo i controlli di sicurezza. In questo caso, nessun controllo di sicurezza a livello generale è necessario, perché le richieste di autorizzazione passeranno al chiamante e/o il dominio dell'applicazione. Le richieste di autorizzazione sono strettamente controllate mediante criteri di sicurezza, ambiente host e concede l'autorizzazione di codice sorgente.

## <a name="see-also"></a>Vedere anche
 [Avvisi di sicurezza](../code-quality/security-warnings.md)
