---
title: 'CA1720: Gli identificatori non devono contenere nomi di tipo | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 60b7bbb0852544f7e2c5267daf0d9fdf1e1214cb
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47541170"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Gli identificatori non devono contenere nomi di tipo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1720: gli identificatori non devono contenere nomi di tipo](https://docs.microsoft.com/visualstudio/code-quality/ca1720-identifiers-should-not-contain-type-names).

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il nome di un parametro in un membro visibile esternamente contiene un nome di tipo di dati.

 oppure

 Il nome di un membro visibile esternamente contiene un nome di tipo di dati specifico del linguaggio.

## <a name="rule-description"></a>Descrizione della regola
 I nomi dei parametri e membri sono meglio utilizzati per comunicare il significato di to descriverne il tipo, il quale viene in genere fornito dagli strumenti di sviluppo. Per i nomi dei membri, se è necessario utilizzare un nome di tipo di dati, usare un nome indipendente dalla lingua anziché uno specifico del linguaggio. Anziché il nome di tipo c# 'int', ad esempio, usare il nome del tipo di dati indipendenti dal linguaggio, Int32.

 Ogni token discreti il nome del parametro o un membro viene confrontato con i nomi dei tipi di dati specifico del linguaggio seguenti, in modo tra maiuscole e minuscole:

-   Bool

-   WChar

-   Int8

-   UInt8

-   Short

-   UShort

-   Int

-   UInt

-   Integer

-   UInteger

-   Long

-   ULong

-   Senza segno

-   Firmato

-   Float

-   float32

-   float64

 Inoltre, i nomi di parametro sono anche confrontati con i nomi dei tipi di dati indipendenti dal linguaggio seguente, in modo tra maiuscole e minuscole:

-   Object

-   obj

-   Booleano

-   Char

-   Stringa

-   SByte

-   Byte

-   UByte

-   Int16

-   UInt16

-   Int32

-   UInt32

-   Int64

-   UInt64

-   IntPtr

-   PTR

-   Puntatore

-   UInptr

-   UPtr

-   UPointer

-   Single

-   Double

-   Decimale

-   GUID

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 **Se viene generato con un parametro:**

 Sostituire l'identificatore del tipo di dati del nome del parametro con un termine che meglio descrive il significato o un termine più generico, ad esempio 'value'.

 **Se generato da un membro:**

 Sostituire l'identificatore del tipo di dati specifico del linguaggio il nome del membro con un termine che meglio descrive il significato, un equivalente indipendente dal linguaggio o un termine più generico, ad esempio 'value'.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Uso occasionale di nomi di parametri e membri in base al tipo potrebbe essere appropriato. Tuttavia, per i nuovi sviluppi, nessun noti verificarsi gli scenari in cui si deve eliminare un avviso da questa regola. Per le librerie fornite in precedenza, potrebbe essere necessario eliminare un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: I nomi dei parametri non devono corrispondere ai nomi dei membri](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)


