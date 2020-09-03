---
title: 'CA1050: dichiarare i tipi negli spazi dei nomi | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a0a4dcc53fac7dc9b7e189686a3b32e2fb4fd030
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539594"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Dichiarare i tipi negli spazi dei nomi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto viene definito al di fuori dell'ambito di uno spazio dei nomi denominato.

## <a name="rule-description"></a>Descrizione della regola
 I tipi vengono dichiarati negli spazi dei nomi per evitare conflitti di nomi e come modo per organizzare i tipi correlati in una gerarchia di oggetti. I tipi che sono all'esterno di uno spazio dei nomi denominato si trovano in uno spazio dei nomi globale a cui non è possibile fare riferimento nel codice.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, inserire il tipo in uno spazio dei nomi.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Sebbene non sia mai necessario eliminare un avviso da questa regola, è possibile eseguire questa operazione in modo sicuro quando l'assembly non verrà mai usato insieme ad altri assembly.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una libreria con un tipo dichiarato in modo non corretto all'esterno di uno spazio dei nomi e un tipo con lo stesso nome dichiarato in uno spazio dei nomi.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>Esempio
 Nell'applicazione seguente viene utilizzata la libreria definita in precedenza. Si noti che il tipo dichiarato all'esterno di uno spazio dei nomi viene creato quando il nome `Test` non è qualificato da uno spazio dei nomi. Si noti inoltre che per accedere al `Test` tipo in `Goodspace` , il nome dello spazio dei nomi è obbligatorio.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]
