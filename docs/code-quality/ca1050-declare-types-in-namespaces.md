---
title: 'CA1050: Dichiarare i tipi negli spazi dei nomi'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5bff984d9ea11ba8fd7f2e42deb5898f04da7d44
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548484"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Dichiarare i tipi negli spazi dei nomi

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Viene definito un tipo pubblico o protetto all'esterno dell'ambito di uno spazio dei nomi denominato.

## <a name="rule-description"></a>Descrizione della regola
 I tipi sono dichiarati negli spazi dei nomi per evitare conflitti tra nomi e un modo per organizzare i tipi correlati in una gerarchia di oggetti. I tipi che si trovano all'esterno di qualsiasi spazio dei nomi denominato sono in uno spazio dei nomi globale che non è possibile farvi riferimento nel codice.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, inserire il tipo in uno spazio dei nomi.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Sebbene sia mai necessario eliminare un avviso da questa regola, è consigliabile eseguire questa operazione se l'assembly non verrà mai utilizzato insieme ad altri assembly.

## <a name="example"></a>Esempio
 Nell'esempio seguente mostra una libreria che ha un tipo dichiarato in modo non corretto all'esterno di uno spazio dei nomi e un tipo che ha lo stesso nome dichiarato in uno spazio dei nomi.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]

## <a name="example"></a>Esempio
 La seguente applicazione usa la libreria che è stata definita in precedenza. Si noti che il tipo dichiarato all'esterno di uno spazio dei nomi viene creato quando il nome `Test` non sono qualificati da uno spazio dei nomi. Si noti inoltre che per accedere la `Test` digitare `Goodspace`, il nome dello spazio dei nomi è obbligatorio.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]