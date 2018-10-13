---
title: 'CA1040: Evitare di interfacce vuote | Microsoft Docs'
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
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b5e2ff26842f63ea1c21e599b301e4ce4e78bf80
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190320"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Evitare l'utilizzo di interfacce vuote
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 L'interfaccia non dichiarato alcun membro o implementare due o più interfacce.

## <a name="rule-description"></a>Descrizione della regola
 Le interfacce definiscono membri che forniscono un comportamento o un contratto di utilizzo. La funzionalità descritta dall'interfaccia può essere adottata da qualsiasi tipo, indipendentemente dal punto in cui il tipo è visualizzato nella gerarchia di ereditarietà. Un tipo implementa un'interfaccia fornendo implementazioni per i membri dell'interfaccia. Un'interfaccia vuota non definisce alcun membro. Pertanto, non definisce un contratto che può essere implementato.

 Se la progettazione include vuota sono deve implementare le interfacce che è stato digitato, probabilmente si sta usando un'interfaccia come marcatore o come un modo per identificare un gruppo di tipi. Se questa identificazione si verifica in fase di esecuzione, il modo corretto per eseguire questa operazione è usare un attributo personalizzato. Usare la presenza o assenza dell'attributo o le proprietà dell'attributo, per identificare i tipi di destinazione. Se l'identificazione deve verificarsi in fase di compilazione, quindi è possibile utilizzare un'interfaccia vuota.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere l'interfaccia o aggiungervi membri. Se l'interfaccia vuota viene utilizzato per etichettare un set di tipi, sostituire l'interfaccia con un attributo personalizzato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando l'interfaccia viene utilizzata per identificare un set di tipi in fase di compilazione.

## <a name="example"></a>Esempio
 L'esempio seguente illustra un'interfaccia vuota.

 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cpp/FxCop.Design.InterfacesNotEmpty.cpp#1)]
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cs/FxCop.Design.InterfacesNotEmpty.cs#1)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/vb/FxCop.Design.InterfacesNotEmpty.vb#1)]



