---
title: 'CA2133: Delegati devono essere associati ai metodi con trasparenza consistente'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11f6738d1f280869d5390b8109e61a6efb9c64b9
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545541"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: Delegati devono essere associati ai metodi con trasparenza consistente

|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

> [!NOTE]
> Questo avviso viene applicato solo al codice che esegue CoreCLR (la versione di CLR è specifico per le applicazioni web Silverlight).

## <a name="cause"></a>Causa

Questo avviso viene attivato su un metodo che associa un delegato contrassegnato con il <xref:System.Security.SecurityCriticalAttribute> a un metodo trasparente o contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute>. L'avviso genera anche un metodo che associa un delegato che è trasparente o critico per la sicurezza a un metodo critico.

## <a name="rule-description"></a>Descrizione della regola

I tipi delegati e i metodi che vengono associate devono avere trasparenza consistente. I delegati trasparenti e richiamabile da codice trasparente possono associare solo ad altri metodi trasparente o critico. Allo stesso modo, critici delegati possono solo associare ai metodi critici. Queste regole di associazione assicurano che l'unico codice che può richiamare un metodo tramite un delegato può inoltre aver richiamato il metodo di stesso direttamente. Ad esempio, regole di associazione impediscono di chiamata di codice critico direttamente tramite un delegato trasparente codice trasparente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questo avviso, modificare la trasparenza del delegato o del metodo che associa in modo che la trasparenza dei due sono equivalenti.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.

### <a name="code"></a>Codice

[!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]