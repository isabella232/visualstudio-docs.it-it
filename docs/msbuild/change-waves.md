---
title: Flussi di modifiche
description: Informazioni su come abilitare o disabilitare le funzionalità in MSBuild potenzialmente dannose.
ms.date: 11/10/2020
ms.topic: conceptual
helpviewer_keywords:
- Change waves [MSBuild]
- MSBuildDisableFeaturesFromVersion environment variable
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
monikerRange: '>=vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 30d739c7a0cbdc80a82368128266960e1debca3a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108980"
---
# <a name="change-waves"></a>Flussi di modifiche

*Un'ondata* di modifiche è un set di modifiche del comportamento MSBuild cui è possibile rifiutare esplicitamente specificando un flag specifico come variabile di ambiente. Questo scopo è quello di avvisare l'utente di modifiche potenzialmente dannose, in modo da avere flessibilità nell'adattamento a queste modifiche prima che diventino funzionalità standard. Tutte le funzionalità di un'ondata di modifiche specifica possono essere abilitate o disabilitate solo insieme, non singolarmente.

Quando si esegue l'aggiornamento a una nuova versione di MSBuild, le modifiche potenzialmente di rilievo sono abilitate per impostazione predefinita, ma se una funzionalità influisce negativamente sulla compilazione, è possibile disabilitare facilmente tale ondata di modifiche. Ogni ondata di modifiche è identificata da un numero di versione MSBuild (ad esempio, 16.8), ma l'impostazione dell'ondata di modifiche controlla solo determinate funzionalità che possono influire sul processo di compilazione, non tutte le modifiche in tale versione MSBuild. Un elenco delle funzionalità in ogni ondata di modifica viene [visualizzato più avanti in questo articolo.](#change-waves-and-associated-features) La disabilitazione di un'ondata di modifiche disabilita anche le ondate di modifiche delle versioni superiori.

## <a name="opt-out-of-change-wave-features"></a>Rifiutare esplicitamente le funzionalità delle onde di modifica

Per disabilitare le funzionalità in un'ondata di modifiche, impostare la variabile di ambiente sull'ondata di modifica (o MSBuild versione) che contiene la funzionalità da `MSBuildDisableFeaturesFromVersion` **disabilitare.** Questa è la versione di MSBuild per cui sono state sviluppate le funzionalità. Vedere il mapping delle onde di modifica alle funzionalità di seguito.

### <a name="msbuilddisablefeaturesfromversion-values"></a>Valori di MSBuildDisableFeaturesFromVersion

Se non si imposta un'ondata di modifiche valida, si riceverà un avviso e/o un'ondata `MSBuildDisableFeaturesFromVersion` specifica. La tabella seguente illustra le possibili impostazioni:

| Valore di `MSBuildDisableFeaturesFromVersion`                         | Risultato        | Ricevere un avviso? |
| :-------------                                                    | :----------   | :----------: |
| Annullata                                                             | Abilitare tutte le onde di modifica, ovvero tutte le funzionalità dietro ogni ondata di modifica sono abilitate.               | No   |
| Qualsiasi ondata di modifica valida e corrente (ad esempio, `16.8` )                      | Disabilitare tutte le funzionalità dietro change wave `16.8` **e versioni successive.**                                           | No   |
| Valore non valido (ad esempio, `16.9` quando le onde valide sono e `16.8` `16.10` )| Il valore predefinito è il valore valido più vicino (crescente). Ad esempio, `16.9` l'impostazione predefinita sarà `16.10` .               | No   |
| Fuori rotazione (ad esempio, `17.1` quando l'onda più alta è `17.0` )      | Si avvicina al valore valido più vicino. Ad esempio, `17.1` le piascie `17.0` a e le `16.5` piass `16.8`                    | Sì  |
| Formato non valido (ad esempio, `16x8` `17_0` , , `garbage` )                    | Abilitare tutte le onde di modifica, ovvero tutte le funzionalità dietro ogni ondata di modifica sono abilitate.               | Sì  |

## <a name="change-waves-and-associated-features"></a>Modificare le onde e le funzionalità associate

I collegamenti nell'elenco seguente passano alla richiesta GitHub richiesta pull per la funzionalità.

### <a name="168"></a>16.8

- [Abilitare NoWarn](https://github.com/dotnet/msbuild/pull/5671)
- [Tronca messaggi di log di destinazione/attività ignorati a 1024 caratteri](https://github.com/dotnet/msbuild/pull/5553)
- [Non espandere i glob dell'unità completa con condizione false](https://github.com/dotnet/msbuild/pull/5669)

### <a name="1610"></a>16,10

- [Errore durante l'espansione di una proprietà in una condizione con spazi vuoti](https://github.com/dotnet/msbuild/pull/5672)

### <a name="170"></a>17.0

Non sono ancora presenti voci in questa modifica.

## <a name="change-waves-that-are-out-of-rotation"></a>Modificare le onde che non sono in rotazione

Al momento non sono presenti onde di modifica fuori rotazione.

## <a name="faq"></a>Domande frequenti

**Perché impostare come destinazione ogni altra versione per la rotazione delle onde di modifica?**

Si ritiene che questo sia sufficiente per discutere con gli interessati e agevolare l'adattamento alle modifiche.

**Perché una variabile di ambiente e non una proprietà di progetto?**

Esistono scenari in cui si vuole posizionare una funzionalità sotto un'ondata di modifiche prima MSBuild caricare il progetto. Per questo motivo, le onde di modifica richiedono l'uso di variabili di ambiente.

**Perché rifiutare esplicitamente il consenso esplicito?**

Il rifiuto esplicito è un approccio migliore per microsoft, altrimenti è probabile che si otterrà un feedback limitato quando una funzionalità influisce sulle compilazioni dei clienti.

## <a name="see-also"></a>Vedi anche

- [MSBuild](msbuild.md)
- [Novità di MSBuild 16](whats-new-msbuild-16-0.md)
