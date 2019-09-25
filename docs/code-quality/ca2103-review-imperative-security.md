---
title: 'CA2103: Controllare la sicurezza imperativa'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2792f1cccad26fe5bb073af800a2fcf0ebcb4b4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232989"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Controllare la sicurezza imperativa

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Category|Microsoft.Security|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un metodo utilizza la sicurezza imperativa e potrebbe costruire l'autorizzazione tramite le informazioni sullo stato o i valori restituiti che possono essere modificati mentre la richiesta è attiva.

## <a name="rule-description"></a>Descrizione della regola
La sicurezza imperativa usa oggetti gestiti per specificare le autorizzazioni e le azioni di sicurezza durante l'esecuzione del codice, rispetto alla sicurezza dichiarativa, che usa gli attributi per archiviare le autorizzazioni e le azioni nei metadati. La sicurezza imperativa è molto flessibile perché è possibile impostare lo stato di un oggetto autorizzazione e selezionare le azioni di sicurezza usando le informazioni che non sono disponibili fino alla fase di esecuzione. Insieme a tale flessibilità, il rischio che le informazioni di runtime utilizzate per determinare lo stato di un'autorizzazione non rimangano invariate finché l'azione è attiva.

Usare la sicurezza dichiarativa quando possibile. Le richieste dichiarative sono più facili da comprendere.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Esaminare le richieste di sicurezza imperative per assicurarsi che lo stato dell'autorizzazione non si basi sulle informazioni che possono essere modificate fino a quando viene utilizzata l'autorizzazione.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola se l'autorizzazione non si basa sulla modifica dei dati. Tuttavia, è preferibile modificare la richiesta imperativa nell'equivalente dichiarativo.

## <a name="see-also"></a>Vedere anche

- [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)
- [Dati e modellazione](/dotnet/framework/data/index)