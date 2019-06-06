---
title: 'CA1030: Usare eventi dove appropriato'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9a3d2ef30018c7fe57f1e7d728ba1dd152f56f5
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714288"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Usare eventi dove appropriato

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un nome di metodo inizia con uno dei seguenti:

- AddOn
- RemoveOn
- Incendi
- Raise

Per impostazione predefinita, questa regola cerca solo a metodi visibili esternamente, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Questa regola rileva i metodi che presentano nomi comunemente utilizzati per gli eventi. Gli eventi di seguono lo schema progettuale osservatore o Publish-Subscribe; vengono utilizzati quando una modifica dello stato in un oggetto deve essere comunicata ad altri oggetti. Se un metodo viene chiamato in risposta a una modifica dello stato chiaramente definita, il metodo deve essere richiamato da un gestore eventi. Gli oggetti che chiamano il metodo devono generare eventi anziché chiamare direttamente il metodo.

Alcuni esempi comuni di eventi si trovano in applicazioni con interfaccia utente in cui un'azione dell'utente, ad esempio facendo clic su un pulsante fa sì che un segmento di codice da eseguire. Il modello di eventi .NET non è limitato alle interfacce utente. Deve essere usata ovunque che è necessario comunicare lo stato passa a uno o più oggetti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Se il metodo viene chiamato quando cambia lo stato di un oggetto, provare a modificare la progettazione per utilizzare il modello di eventi .NET.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Eliminare un avviso da questa regola se il metodo non funziona con il modello di eventi .NET.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```ini
dotnet_code_quality.ca1030.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).
