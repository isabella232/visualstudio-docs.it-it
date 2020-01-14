---
title: "CA1903: usare solo l'API del Framework di destinazione | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fa0d771d99ac8e7a4f4091db90a607cce970bc38
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917819"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Utilizzare solo API della versione di .NET Framework di destinazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente su Visual Studio, vedere [CA1903: usare solo l'API del Framework di destinazione](/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework).

|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Categoria|Microsoft. portabilità|
|Modifica importante|Suddivisione: quando viene attivato in base alla firma di un membro o di un tipo visibile esternamente.<br /><br /> Senza interruzioni: quando viene attivato nel corpo di un metodo.|

## <a name="cause"></a>Causa
 Un membro o un tipo usa un membro o un tipo introdotto in un Service Pack non incluso nel Framework di destinazione del progetto.

## <a name="rule-description"></a>Descrizione della regola
 I nuovi membri e tipi sono stati inclusi in .NET Framework 2,0 Service Pack 1 e 2, .NET Framework 3,0 Service Pack 1 e 2 e .NET Framework 3,5 Service Pack 1. I progetti destinati alle versioni principali del .NET Framework possono assumere involontariamente dipendenze da queste nuove API. Per evitare questa dipendenza, questa regola viene attivata per gli utilizzi di nuovi membri e tipi non inclusi per impostazione predefinita con il Framework di destinazione del progetto.

 **Dipendenze di Framework di destinazione e Service Pack**

|||
|-|-|
|Quando il Framework di destinazione è|Generato per gli utilizzi dei membri introdotti in|
|.NET Framework 2.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2|
|.NET Framework 3.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2, .NET Framework 3,0 SP1, .NET Framework 3,0 SP2|
|.NET Framework 3.5|.NET Framework 3.5 SP1|
|.NET Framework 4|N/D|

 Per modificare il Framework di destinazione di un progetto, vedere [targeting a Specific .NET Framework Version](../ide/targeting-a-specific-dotnet-framework-version.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per rimuovere la dipendenza dal Service Pack, rimuovere tutti gli utilizzi del nuovo membro o del nuovo tipo. Se si tratta di una dipendenza intenzionale, eliminare l'avviso o disattivare questa regola.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola se non si tratta di una dipendenza intenzionale dal Service Pack specificato. In questa situazione, l'esecuzione dell'applicazione potrebbe non riuscire nei sistemi senza questo Service Pack installato. Eliminare l'avviso o disattivare questa regola se si tratta di una dipendenza intenzionale.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una classe che utilizza il tipo DateTimeOffset disponibile solo in .NET 2,0 Service Pack 1. Questo esempio richiede che .NET Framework 2,0 sia stato selezionato nell'elenco a discesa Framework di destinazione nelle proprietà del progetto.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene corretta la violazione descritta in precedenza sostituendo gli utilizzi del tipo DateTimeOffset con il tipo DateTime.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]

## <a name="see-also"></a>Vedere anche
 [Avvisi di portabilità](../code-quality/portability-warnings.md) [destinati a una versione specifica di .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)
