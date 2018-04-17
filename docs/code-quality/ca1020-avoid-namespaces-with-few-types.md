---
title: 'CA1020: Evitare gli spazi dei nomi con pochi tipi | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a90f43735092591ad019fd2a46569e9302cf0c3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Evitare l'utilizzo di spazi dei nomi con un numero ridotto di tipi
|||  
|-|-|  
|TypeName|AvoidNamespacesWithFewTypes|  
|CheckId|CA1020|  
|Category|Microsoft.Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Uno spazio dei nomi diversi da spazio dei nomi globale contiene meno di cinque tipi.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Verificare che ognuno degli spazi dei nomi disponga di un'organizzazione logica e che esista un motivo valido per inserire tipi in uno spazio dei nomi scarsamente popolato. Spazi dei nomi deve contenere tipi utilizzati nella maggior parte degli scenari. Quando le applicazioni si escludono a vicenda, tipi devono essere collocati in spazi dei nomi distinti. Ad esempio, il <xref:System.Web.UI> dello spazio dei nomi contiene i tipi che sono usati nelle applicazioni Web, e <xref:System.Windows.Forms> spazio dei nomi contiene tipi che sono utilizzati in [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]-applicazioni basate su. Anche se entrambi gli spazi dei nomi sono tipi che consentono di controllare aspetti dell'interfaccia utente, questi tipi non sono progettati per l'utilizzo nella stessa applicazione. Pertanto, si trovano in spazi dei nomi distinti. Attenzione organizzazione dello spazio dei nomi può essere utile poiché in questo modo l'individuazione di una funzionalità. Esaminando la gerarchia dello spazio dei nomi, i consumer della libreria deve essere in grado di individuare i tipi che implementano una funzionalità.  
  
> [!NOTE]
>  Le autorizzazioni e i tipi in fase di progettazione non devono essere unite in altri spazi dei nomi per la conformità con questa linea guida. Questi tipi appartengono i propri spazi dei nomi sotto lo spazio dei nomi principale e gli spazi dei nomi deve terminare con `.Design` e `.Permissions`, rispettivamente.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, tenta di combinare gli spazi dei nomi che contengono un numero ridotto di tipi in un singolo spazio dei nomi.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola quando lo spazio dei nomi non contiene tipi utilizzati con i tipi di spazi dei nomi.