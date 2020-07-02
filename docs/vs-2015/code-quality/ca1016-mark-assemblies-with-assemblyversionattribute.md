---
title: 'CA1016: contrassegnare gli assembly con AssemblyVersionAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 97bd41e51c8d6b5415ffb91c5696c7055f46cf7c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545405"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Contrassegnare gli assembly con AssemblyVersionAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 L'assembly non dispone di un numero di versione.

## <a name="rule-description"></a>Descrizione della regola
 L'identità di un assembly è costituita dalle seguenti informazioni:

- Nome assembly

- Numero di versione

- Impostazioni cultura

- Chiave pubblica (per gli assembly con nome sicuro).

  In [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] viene utilizzato il numero di versione per identificare in modo univoco un assembly e per stabilire associazioni a tipi in assembly con nome sicuro. Il numero di versione viene utilizzato insieme ai criteri di versione ed editore. Per impostazione predefinita, le applicazioni vengono eseguite solo con la versione di assembly con cui sono state compilate.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere un numero di versione all'assembly usando l' <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> attributo. Vedere l'esempio seguente.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola per gli assembly utilizzati da terze parti o in un ambiente di produzione.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un assembly a cui è <xref:System.Reflection.AssemblyVersionAttribute> applicato l'attributo.

 [!code-cpp[FxCop.Design.AssembliesVersion#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cpp/FxCop.Design.AssembliesVersion.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cs/FxCop.Design.AssembliesVersion.cs#1)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/vb/FxCop.Design.AssembliesVersion.vb#1)]

## <a name="see-also"></a>Vedere anche
 [Controllo delle versioni degli assembly](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [procedura: creare criteri editore](https://msdn.microsoft.com/library/8046bc5d-2fa9-4277-8a5e-6dcc96c281d9)
