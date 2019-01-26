---
title: 'CA1715: Gli identificatori devono contenere il prefisso corretto'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7c1e50c814c22ccddb43e90b41752f3f0bc5797e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986957"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: Gli identificatori devono contenere il prefisso corretto

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|Category|Microsoft.Naming|
|Modifica importante|Rilievo - quando viene attivato sulle interfacce.<br /><br /> Non sostanziale - Quando si è generato su parametri di tipo generico.|

## <a name="cause"></a>Causa
 Il nome di un'interfaccia visibile esternamente non inizia con una "I" maiuscola.

 -oppure-

 Il nome di un parametro di tipo generico su un tipo visibile esternamente o un metodo non inizia con una maiuscola l ' '.

## <a name="rule-description"></a>Descrizione della regola
 Per convenzione, i nomi di determinati elementi di programmazione iniziano con un prefisso specifico.

 I nomi di interfaccia devono iniziare con una lettera maiuscola 'I' seguito da un'altra lettera maiuscola. Questa regola segnala le violazioni per i nomi di interfaccia, ad esempio "MyInterface" e "IsolatedInterface".

 I nomi dei parametri di tipo generico deve iniziare con una ' T' ' e, facoltativamente, può essere seguita da un'altra lettera maiuscola. Questa regola segnala le violazioni per i nomi dei parametri di tipo generico, ad esempio "V" e 'Type'.

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rinominare l'identificatore in modo che in modo corretto viene aggiunto come prefisso.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 **L'esempio seguente illustra un'interfaccia denominata in modo errato.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

## <a name="example"></a>Esempio
 **Nell'esempio seguente consente di correggere la violazione precedente aggiungendo il prefisso dell'interfaccia 'I'.**

 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="example"></a>Esempio
 **Nell'esempio seguente mostra un parametro di tipo generico denominata in modo errato.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

## <a name="example"></a>Esempio
 **Nell'esempio seguente consente di correggere la violazione precedente anteponendo il parametro di tipo generico con l ' '.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA1722: Gli identificatori non devono contenere il prefisso non corretto](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)