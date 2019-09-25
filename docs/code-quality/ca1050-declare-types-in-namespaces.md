---
title: 'CA1050: Dichiarare i tipi negli spazi dei nomi'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8127c68cfe7eb541b8adea8affad99027e0c1fe7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235757"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Dichiarare i tipi negli spazi dei nomi

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Category|Microsoft.Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un tipo pubblico o protetto viene definito al di fuori dell'ambito di uno spazio dei nomi denominato.

## <a name="rule-description"></a>Descrizione della regola
I tipi vengono dichiarati negli spazi dei nomi per evitare conflitti di nomi e come modo per organizzare i tipi correlati in una gerarchia di oggetti. I tipi che sono all'esterno di uno spazio dei nomi denominato si trovano in uno spazio dei nomi globale a cui non è possibile fare riferimento nel codice.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, inserire il tipo in uno spazio dei nomi.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Sebbene non sia mai necessario eliminare un avviso da questa regola, è possibile eseguire questa operazione in modo sicuro quando l'assembly non verrà mai usato insieme ad altri assembly.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrata una libreria con un tipo dichiarato in modo non corretto all'esterno di uno spazio dei nomi e un tipo con lo stesso nome dichiarato in uno spazio dei nomi.

[!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
[!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]

## <a name="example"></a>Esempio
Nell'applicazione seguente viene utilizzata la libreria definita in precedenza. Si noti che il tipo dichiarato all'esterno di uno spazio dei nomi viene creato `Test` quando il nome non è qualificato da uno spazio dei nomi. Si noti inoltre che per accedere `Test` al tipo `Goodspace`in, il nome dello spazio dei nomi è obbligatorio.

[!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
[!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]