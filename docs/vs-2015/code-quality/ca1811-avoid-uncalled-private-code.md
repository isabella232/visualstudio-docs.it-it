---
title: 'CA1811: evitare il codice privato non chiamato | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 223b2ff9aa25ddd94a3c62eb9e641127a1cace4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543819"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Evitare il codice privato non chiamato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Category|Microsoft. performance|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un membro privato o interno (a livello di assembly) non contiene chiamanti nell'assembly, non viene richiamato dal Common Language Runtime e non viene richiamato da un delegato. I membri seguenti non vengono controllati da questa regola:

- Membri di interfaccia espliciti.

- Costruttori statici.

- Costruttori di serializzazione.

- Metodi contrassegnati con <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> .

- Membri che sono sostituzioni.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola può segnalare falsi positivi se si verificano punti di ingresso che non sono attualmente identificati dalla logica della regola. Inoltre, un compilatore può generare codice non chiamabile in un assembly.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il codice non chiamabile o aggiungere il codice che lo chiama.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola in modo sicuro.

## <a name="related-rules"></a>Regole correlate
 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Controllare i parametri non usati](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Rimuovere variabili locali non usate](../code-quality/ca1804-remove-unused-locals.md)
