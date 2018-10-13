---
title: 'CA2135: Gli assembly di livello 2 non devono contenere LinkDemands | Microsoft Docs'
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
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4e4b4cd759557defc7761db34841e3d87a285558
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294801"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Gli assembly di livello 2 non devono contenere LinkDemands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Una classe o membro di classe Usa un <xref:System.Security.Permissions.SecurityAction> in un'applicazione che utilizza una sicurezza di livello 2.

## <a name="rule-description"></a>Descrizione della regola
 I LinkDemand sono deprecati nel set di regole per la sicurezza di livello 2. Invece di usare i LinkDemand per applicare la sicurezza in fase di compilazione just-in-time (JIT), contrassegnare i metodi, tipi e i campi con il <xref:System.Security.SecurityCriticalAttribute> attributo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il <xref:System.Security.Permissions.SecurityAction> e contrassegnare il tipo o membro con il <xref:System.Security.SecurityCriticalAttribute> attributo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente, il <xref:System.Security.Permissions.SecurityAction> devono essere rimossi e il metodo contrassegnato con il <xref:System.Security.SecurityCriticalAttribute> attributo.

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2135.securityrulesetlevel2methodsshouldnotbeprotectedwithlinkdemands/cs/ca2135.cs#1)]



