---
title: 'CA1030: usare gli eventi laddove appropriato | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1313c5ee79a7a13d3eb937a3431b13ea393857d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544521"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Usare eventi dove appropriato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un nome di metodo public, protected o private inizia con uno dei seguenti elementi:

- AddOn

- Privo RemoveOn

- Fire

- Sollevare

## <a name="rule-description"></a>Descrizione della regola
 Questa regola rileva i metodi che presentano nomi comunemente utilizzati per gli eventi. Gli eventi seguono il modello di progettazione Observer o Publish-Subscribe; vengono usati quando una modifica di stato in un oggetto deve essere comunicata ad altri oggetti. Se un metodo viene chiamato in risposta a una modifica di stato chiaramente definita, il metodo deve essere richiamato da un gestore eventi. Gli oggetti che chiamano il metodo devono generare eventi anziché chiamare direttamente il metodo.

 Alcuni esempi comuni di eventi sono disponibili nelle applicazioni dell'interfaccia utente, in cui un'azione dell'utente, ad esempio il clic su un pulsante, comporta l'esecuzione di un segmento di codice. Il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modello di eventi non è limitato alle interfacce utente. deve essere usato ovunque sia necessario comunicare le modifiche di stato a uno o più oggetti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Se il metodo viene chiamato quando viene modificato lo stato di un oggetto, è consigliabile modificare la progettazione per utilizzare il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modello di eventi.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola se il metodo non funziona con il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modello di eventi.
