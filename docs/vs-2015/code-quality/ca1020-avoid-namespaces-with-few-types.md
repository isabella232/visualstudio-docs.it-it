---
title: 'CA1020: Evitare gli spazi dei nomi con alcuni tipi | Microsoft Docs'
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
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b3a7f1c0b6cdfbf96542d9edc76596295f2d695a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47541172"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Evitare l'utilizzo di spazi dei nomi con un numero ridotto di tipi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1020: evitare gli spazi dei nomi con alcuni tipi](https://docs.microsoft.com/visualstudio/code-quality/ca1020-avoid-namespaces-with-few-types).

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Uno spazio dei nomi diversi da spazio dei nomi globale contiene meno di cinque tipi.

## <a name="rule-description"></a>Descrizione della regola
 Assicurarsi che ogni spazio dei nomi disponga di un'organizzazione logica e che esista un motivo valido per inserire tipi in uno spazio dei nomi scarsamente popolato. Gli spazi dei nomi devono contenere tipi che vengono utilizzati insieme nella maggior parte degli scenari. Quando le applicazioni si escludono a vicenda, tipi devono trovarsi in spazi dei nomi distinti. Ad esempio, il <xref:System.Web.UI> spazio dei nomi contiene tipi usati nelle applicazioni Web e il <xref:System.Windows.Forms> dello spazio dei nomi contiene tipi utilizzabili in [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)]-applicazioni basate su. Anche se entrambi gli spazi dei nomi presenti tipi che consentono di controllare gli aspetti dell'interfaccia utente, questi tipi non sono progettati per l'uso nella stessa applicazione. Pertanto, si trovano in spazi dei nomi distinti. Un'attenta organizzazione dello spazio dei nomi può essere utile in quanto aumenta l'esposizione al rilevamento di una funzionalità. Esaminando la gerarchia dello spazio dei nomi, i consumer della libreria deve essere in grado di individuare i tipi che implementano una funzionalità.

> [!NOTE]
>  Le autorizzazioni e i tipi in fase di progettazione non devono essere unite in altri spazi dei nomi per la conformità con questa linea guida. Questi tipi fanno parte di spazi dei nomi dedicati sotto lo spazio dei nomi principale e deve terminare con spazi dei nomi `.Design` e `.Permissions`, rispettivamente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, provare a combinare gli spazi dei nomi che contengono alcuni tipi in un unico spazio dei nomi.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando lo spazio dei nomi non contiene tipi che vengono usati con i tipi di spazi dei nomi.


