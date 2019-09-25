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
ms.openlocfilehash: 6e5c50f607253304b05dd7ab9350646a0df05e70
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236234"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Evitare l'uso di spazi dei nomi con un numero ridotto di tipi

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Category|Microsoft.Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Uno spazio dei nomi diverso dallo spazio dei nomi globale contiene meno di cinque tipi.

## <a name="rule-description"></a>Descrizione della regola

Verificare che ogni spazio dei nomi disponga di un'organizzazione logica e che esista un motivo valido per inserire i tipi in uno spazio dei nomi con popolamento sparse. Gli spazi dei nomi devono contenere i tipi utilizzati insieme nella maggior parte degli scenari. Quando le applicazioni si escludono a vicenda, i tipi devono trovarsi in spazi dei nomi distinti. Ad esempio, lo <xref:System.Web.UI> spazio dei nomi contiene i tipi utilizzati nelle applicazioni Web e lo <xref:System.Windows.Forms> spazio dei nomi contiene i tipi utilizzati [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]nelle applicazioni basate su. Anche se entrambi gli spazi dei nomi includono tipi che controllano aspetti dell'interfaccia utente, questi tipi non sono progettati per l'uso nella stessa applicazione. Si trovano quindi in spazi dei nomi distinti. Un'organizzazione dello spazio dei nomi attenta può essere utile anche perché aumenta l'individuabilità di una funzionalità. Esaminando la gerarchia dello spazio dei nomi, i consumer della libreria devono essere in grado di individuare i tipi che implementano una funzionalità.

> [!NOTE]
> I tipi e le autorizzazioni della fase di progettazione non devono essere Uniti in altri spazi dei nomi per conformarsi a questa linea guida. Questi tipi appartengono ai rispettivi spazi dei nomi sotto lo spazio dei nomi principale e gli spazi dei nomi devono `.Design` terminare `.Permissions`rispettivamente con e.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, provare a combinare gli spazi dei nomi che contengono solo pochi tipi in un singolo spazio dei nomi.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola quando lo spazio dei nomi non contiene i tipi usati con i tipi negli altri spazi dei nomi.