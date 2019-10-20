---
title: 'CA2103: controllare la sicurezza imperativa | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b4abf0b15a4fbba1abc61572da8a2f6126c754f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652155"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Controllare la sicurezza imperativa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo utilizza la sicurezza imperativa e potrebbe costruire l'autorizzazione tramite le informazioni sullo stato o i valori restituiti che possono essere modificati mentre la richiesta è attiva.

## <a name="rule-description"></a>Descrizione della regola
 La sicurezza imperativa usa oggetti gestiti per specificare le autorizzazioni e le azioni di sicurezza durante l'esecuzione del codice, rispetto alla sicurezza dichiarativa, che usa gli attributi per archiviare le autorizzazioni e le azioni nei metadati. La sicurezza imperativa è molto flessibile perché è possibile impostare lo stato di un oggetto autorizzazione e selezionare le azioni di sicurezza usando le informazioni che non sono disponibili fino alla fase di esecuzione. Insieme a tale flessibilità, il rischio che le informazioni di runtime utilizzate per determinare lo stato di un'autorizzazione non rimangano invariate finché l'azione è attiva.

 Usare la sicurezza dichiarativa quando possibile. Le richieste dichiarative sono più facili da comprendere.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Esaminare le richieste di sicurezza imperative per assicurarsi che lo stato dell'autorizzazione non si basi sulle informazioni che possono essere modificate fino a quando viene utilizzata l'autorizzazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se l'autorizzazione non si basa sulla modifica dei dati. Tuttavia, è preferibile modificare la richiesta imperativa nell'equivalente dichiarativo.

## <a name="see-also"></a>Vedere anche
 [Sicurezza](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [e modellazione dei dati](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) delle linee guida per la codifica
