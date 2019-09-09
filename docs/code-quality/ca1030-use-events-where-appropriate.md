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
ms.openlocfilehash: ad0659241e75c862b3d82c64a7e8b2ad3ccada21
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547668"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Usare eventi dove appropriato

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Category|Microsoft.Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa

Il nome di un metodo inizia con uno dei seguenti:

- AddOn
- Privo RemoveOn
- Fuoco
- Sollevare

Per impostazione predefinita, questa regola esamina solo i metodi visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Questa regola rileva i metodi che presentano nomi comunemente utilizzati per gli eventi. Gli eventi seguono il modello di progettazione Observer o Publish-Subscribe; vengono usati quando una modifica di stato in un oggetto deve essere comunicata ad altri oggetti. Se un metodo viene chiamato in risposta a una modifica di stato chiaramente definita, il metodo deve essere richiamato da un gestore eventi. Gli oggetti che chiamano il metodo devono generare eventi anziché chiamare direttamente il metodo.

Alcuni esempi comuni di eventi sono disponibili nelle applicazioni dell'interfaccia utente, in cui un'azione dell'utente, ad esempio il clic su un pulsante, comporta l'esecuzione di un segmento di codice. Il modello di eventi .NET non è limitato alle interfacce utente. Deve essere usato ovunque sia necessario comunicare le modifiche di stato a uno o più oggetti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Se il metodo viene chiamato quando viene modificato lo stato di un oggetto, provare a modificare la progettazione per usare il modello di eventi .NET.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Eliminare un avviso da questa regola se il metodo non funziona con il modello di eventi .NET.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1030.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).
