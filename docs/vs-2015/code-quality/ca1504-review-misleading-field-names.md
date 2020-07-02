---
title: 'CA1504: controllare i nomi dei campi fuorvianti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d375b64bbc877cb377157f13b3e4cfa7c7cf1592
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547875"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Controllare i nomi dei campi fuorvianti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Category|Microsoft. gestibilità|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Il nome di un campo di istanza inizia con "s_" o il nome di `static` un `Shared` campo (in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) inizia con "m_".

## <a name="rule-description"></a>Descrizione della regola
 I nomi di campo che iniziano con "s_" sono associati a dati statici da molti utenti. Analogamente, i nomi di campo che iniziano con "m_" sono associati ai dati dell'istanza (membro). Per il codice più facile da gestire, i nomi devono seguire le convenzioni di uso generale.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rinominare il campo utilizzando il prefisso appropriato. In alternativa, fare in modo che il campo accetti il suffisso corrente aggiungendo o rimuovendo il `static` modificatore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.
