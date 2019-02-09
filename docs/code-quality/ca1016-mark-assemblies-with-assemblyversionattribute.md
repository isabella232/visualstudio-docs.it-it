---
title: 'CA1016: Contrassegnare gli assembly con AssemblyVersionAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a00c8e30e981794e69d4572e0a924438514780c7
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55917779"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Contrassegnare gli assembly con AssemblyVersionAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

L'assembly non è un numero di versione.

## <a name="rule-description"></a>Descrizione della regola

L'identità di un assembly prevede le seguenti informazioni:

- Nome assembly

- Numero di versione

- culture

- Chiave pubblica (per assembly con nome sicuro).

.NET Framework Usa il numero di versione per identificare in modo univoco un assembly e per associare tipi in assembly con nome sicuro. Il numero di versione viene utilizzato insieme ai criteri di versione ed editore. Per impostazione predefinita, le applicazioni vengono eseguite solo con la versione di assembly con cui sono state compilate.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere un numero di versione dell'assembly usando il <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> attributo. Vedere l'esempio seguente.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola per gli assembly che vengono usati da terze parti o in un ambiente di produzione.

## <a name="example"></a>Esempio
 L'esempio seguente illustra un assembly avente il <xref:System.Reflection.AssemblyVersionAttribute> attributo viene applicato.

 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]

## <a name="see-also"></a>Vedere anche

- [Controllo delle versioni degli assembly](/dotnet/framework/app-domains/assembly-versioning)
- [Procedura: Creare criteri editore](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)