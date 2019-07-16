---
title: 'CA1050: Dichiarare i tipi negli spazi dei nomi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f13684df70db7026e874bc8edb6282faca2cf98d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200550"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Dichiarare i tipi negli spazi dei nomi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Sebbene sia mai necessario eliminare un avviso da questa regola, è consigliabile eseguire questa operazione se l'assembly non verrà mai utilizzato insieme ad altri assembly.

## <a name="example"></a>Esempio
 Nell'esempio seguente mostra una libreria che ha un tipo dichiarato in modo non corretto all'esterno di uno spazio dei nomi e un tipo che ha lo stesso nome dichiarato in uno spazio dei nomi.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>Esempio
 La seguente applicazione usa la libreria che è stata definita in precedenza. Si noti che il tipo dichiarato all'esterno di uno spazio dei nomi viene creato quando il nome `Test` non sono qualificati da uno spazio dei nomi. Si noti inoltre che per accedere la `Test` digitare `Goodspace`, il nome dello spazio dei nomi è obbligatorio.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]
