---
title: 'CA2133: i delegati devono essere associati a metodi con trasparenza coerente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 12132622900d5698a6b78a1914c687a369d7dc03
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547732"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: I delegati devono essere associati ai metodi con trasparenza consistente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

> [!NOTE]
> Questo avviso viene applicato solo al codice che esegue CoreCLR (la versione di CLR specifica per le applicazioni Web Silverlight).

## <a name="cause"></a>Causa
 Questo avviso viene generato su un metodo che associa un delegato contrassegnato con <xref:System.Security.SecurityCriticalAttribute> a un metodo trasparente o contrassegnato con <xref:System.Security.SecuritySafeCriticalAttribute> . L'avviso genera anche un metodo che associa un delegato che è trasparente o critico per la sicurezza a un metodo critico.

## <a name="rule-description"></a>Descrizione della regola
 I tipi delegati e i metodi a cui sono associati devono avere una trasparenza coerente. I delegati SecurityTransparent e SecurityCritical possono essere associati solo ad altri metodi trasparenti o critici per la sicurezza. Analogamente, i delegati critici possono essere associati solo a metodi critici. Queste regole di associazione assicurano che l'unico codice che può richiamare un metodo tramite un delegato possa avere anche richiamato direttamente lo stesso metodo. Ad esempio, le regole di associazione impediscono al codice trasparente di chiamare codice critico direttamente tramite un delegato trasparente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questo avviso, modificare la trasparenza del delegato o del metodo associato in modo che la trasparenza dei due siano equivalenti.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2133.delegatesmustbindwithconsistenttransparency/cs/ca2133 - delegatesmustbindwithconsistenttransparency.cs#1)]
