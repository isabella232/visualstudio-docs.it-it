---
title: 'CA1040: evitare le interfacce vuote | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ef6dc666cbc3c26d58358c9b59264f93a7bf184
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548252"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Evitare l'uso di interfacce vuote
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 L'interfaccia non dichiara membri né implementa due o più interfacce.

## <a name="rule-description"></a>Descrizione della regola
 Le interfacce definiscono membri che forniscono un comportamento o un contratto di utilizzo. La funzionalità descritta dall'interfaccia può essere adottata da qualsiasi tipo, indipendentemente dal punto in cui il tipo è visualizzato nella gerarchia di ereditarietà. Un tipo implementa un'interfaccia fornendo implementazioni per i membri dell'interfaccia. Un'interfaccia vuota non definisce membri. Pertanto, non definisce un contratto che può essere implementato.

 Se la progettazione include interfacce vuote che i tipi dovrebbero implementare, probabilmente si utilizza un'interfaccia come marcatore o un modo per identificare un gruppo di tipi. Se questa identificazione si verifica in fase di esecuzione, il modo corretto per eseguire questa operazione consiste nell'usare un attributo personalizzato. Usare la presenza o l'assenza dell'attributo oppure le proprietà dell'attributo per identificare i tipi di destinazione. Se l'identificazione deve verificarsi in fase di compilazione, è accettabile usare un'interfaccia vuota.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere l'interfaccia o aggiungervi membri. Se l'interfaccia vuota viene utilizzata per etichettare un set di tipi, sostituire l'interfaccia con un attributo personalizzato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando l'interfaccia viene usata per identificare un set di tipi in fase di compilazione.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata un'interfaccia vuota.

 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cpp/FxCop.Design.InterfacesNotEmpty.cpp#1)]
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cs/FxCop.Design.InterfacesNotEmpty.cs#1)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/vb/FxCop.Design.InterfacesNotEmpty.vb#1)]
