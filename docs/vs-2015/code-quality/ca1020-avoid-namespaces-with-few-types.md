---
title: 'CA1020: evitare gli spazi dei nomi con pochi tipi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ddd69c62eb4d6b818410a588967c1e23f164f9a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546731"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Evitare l'uso di spazi dei nomi con un numero ridotto di tipi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Uno spazio dei nomi diverso dallo spazio dei nomi globale contiene meno di cinque tipi.

## <a name="rule-description"></a>Descrizione della regola
 Verificare che ogni spazio dei nomi disponga di un'organizzazione logica e che esista un motivo valido per inserire i tipi in uno spazio dei nomi con popolamento sparse. Gli spazi dei nomi devono contenere i tipi utilizzati insieme nella maggior parte degli scenari. Quando le applicazioni si escludono a vicenda, i tipi devono trovarsi in spazi dei nomi distinti. Ad esempio, lo <xref:System.Web.UI> spazio dei nomi contiene i tipi utilizzati nelle applicazioni Web e lo <xref:System.Windows.Forms> spazio dei nomi contiene i tipi utilizzati nelle [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] applicazioni basate su. Anche se entrambi gli spazi dei nomi includono tipi che controllano aspetti dell'interfaccia utente, questi tipi non sono progettati per l'uso nella stessa applicazione. Si trovano quindi in spazi dei nomi distinti. Un'organizzazione dello spazio dei nomi attenta può essere utile anche perché aumenta l'individuabilità di una funzionalità. Esaminando la gerarchia dello spazio dei nomi, i consumer della libreria devono essere in grado di individuare i tipi che implementano una funzionalità.

> [!NOTE]
> I tipi e le autorizzazioni della fase di progettazione non devono essere Uniti in altri spazi dei nomi per conformarsi a questa linea guida. Questi tipi appartengono ai rispettivi spazi dei nomi sotto lo spazio dei nomi principale e gli spazi dei nomi devono `.Design` terminare `.Permissions` rispettivamente con e.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, provare a combinare gli spazi dei nomi che contengono solo pochi tipi in un singolo spazio dei nomi.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando lo spazio dei nomi non contiene i tipi usati con i tipi negli altri spazi dei nomi.
