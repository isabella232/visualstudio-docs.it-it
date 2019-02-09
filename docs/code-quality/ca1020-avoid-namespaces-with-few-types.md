---
title: "CA1020: Evitare l'uso di spazi dei nomi con un numero ridotto di tipi"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 396208b9594e46aa179c3eebddc5a552ce0fca3c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55916661"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Evitare l'uso di spazi dei nomi con un numero ridotto di tipi

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Uno spazio dei nomi diversi da spazio dei nomi globale contiene meno di cinque tipi.

## <a name="rule-description"></a>Descrizione della regola

Assicurarsi che ogni spazio dei nomi disponga di un'organizzazione logica e che esista un motivo valido per inserire tipi in uno spazio dei nomi scarsamente popolato. Gli spazi dei nomi devono contenere tipi che vengono utilizzati insieme nella maggior parte degli scenari. Quando le applicazioni si escludono a vicenda, tipi devono trovarsi in spazi dei nomi distinti. Ad esempio, il <xref:System.Web.UI> spazio dei nomi contiene tipi usati nelle applicazioni web e il <xref:System.Windows.Forms> dello spazio dei nomi contiene tipi utilizzabili in [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]-applicazioni basate su. Anche se entrambi gli spazi dei nomi presenti tipi che consentono di controllare gli aspetti dell'interfaccia utente, questi tipi non sono progettati per l'uso nella stessa applicazione. Pertanto, si trovano in spazi dei nomi distinti. Un'attenta organizzazione dello spazio dei nomi può essere utile in quanto aumenta l'esposizione al rilevamento di una funzionalità. Esaminando la gerarchia dello spazio dei nomi, i consumer della libreria deve essere in grado di individuare i tipi che implementano una funzionalità.

> [!NOTE]
> Le autorizzazioni e i tipi in fase di progettazione non devono essere unite in altri spazi dei nomi per la conformità con questa linea guida. Questi tipi fanno parte di spazi dei nomi dedicati sotto lo spazio dei nomi principale e deve terminare con spazi dei nomi `.Design` e `.Permissions`, rispettivamente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, provare a combinare gli spazi dei nomi che contengono alcuni tipi in un unico spazio dei nomi.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola quando lo spazio dei nomi non contiene tipi che vengono usati con i tipi di spazi dei nomi.