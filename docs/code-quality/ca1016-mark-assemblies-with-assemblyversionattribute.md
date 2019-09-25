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
ms.openlocfilehash: 140037b025db88230762bc0d540d933cec7a5119
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236316"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Contrassegnare gli assembly con AssemblyVersionAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Category|Microsoft.Design|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

L'assembly non dispone di un numero di versione.

## <a name="rule-description"></a>Descrizione della regola

L'identità di un assembly è costituita dalle seguenti informazioni:

- Nome assembly

- Numero di versione

- culture

- Chiave pubblica (per gli assembly con nome sicuro).

.NET usa il numero di versione per identificare in modo univoco un assembly e per eseguire il binding ai tipi in assembly con nome sicuro. Il numero di versione viene utilizzato insieme ai criteri di versione ed editore. Per impostazione predefinita, le applicazioni vengono eseguite solo con la versione di assembly con cui sono state compilate.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, aggiungere un numero di versione all'assembly usando l' <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> attributo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non eliminare un avviso da questa regola per gli assembly utilizzati da terze parti o in un ambiente di produzione.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un assembly a cui <xref:System.Reflection.AssemblyVersionAttribute> è applicato l'attributo.

[!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
[!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
[!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]

## <a name="see-also"></a>Vedere anche

- [Controllo delle versioni degli assembly](/dotnet/framework/app-domains/assembly-versioning)
- [Procedura: Creazione di un criterio editore](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)