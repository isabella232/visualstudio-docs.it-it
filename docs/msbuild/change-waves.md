---
title: Flussi di modifiche
description: Informazioni su come abilitare o disabilitare le funzionalità di MSBuild potenzialmente problematiche.
ms.date: 11/10/2020
ms.topic: conceptual
helpviewer_keywords:
- Change waves [MSBuild]
- MSBuildDisableFeaturesFromVersion environment variable
author: ghogen
ms.author: ghogen
manager: jmartens
monikerRange: '>=vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 77f93b4741ee987bac871e619ccbe58e2d4d4000
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939526"
---
# <a name="change-waves"></a>Flussi di modifiche

Un' *onda di modifica* è un set di modifiche del comportamento in MSBuild che è possibile rifiutare esplicitamente specificando un flag particolare come variabile di ambiente. Lo scopo è quello di avvisare l'utente di modifiche potenzialmente dannose, in modo da ottenere flessibilità nell'adattarsi a queste modifiche prima che diventino funzionalità standard. Tutte le funzionalità di un'onda di modifica specifica possono essere abilitate o disabilitate solo insieme, non singolarmente.

Quando si esegue l'aggiornamento a una nuova versione di MSBuild, le modifiche potenzialmente interrotte sono abilitate per impostazione predefinita, ma se una funzionalità influisce negativamente sulla compilazione, è possibile disabilitare facilmente tale Wave delle modifiche. Ogni Wave di modifica è identificato da un numero di versione di MSBuild (ad esempio, 16,8), ma l'impostazione dell'onda di modifica controlla solo alcune funzionalità che possono influire sul processo di compilazione e non tutte le modifiche apportate alla versione di MSBuild. [Più avanti in questo articolo](#change-waves-and-associated-features)viene visualizzato un elenco delle funzionalità di ogni Wave di modifica. La disabilitazione di un'ondata di modifica Disabilita anche le fluttuazioni delle versioni successive.

## <a name="opt-out-of-change-wave-features"></a>Rifiutare esplicitamente le funzionalità di Wave Change

Per disabilitare le funzionalità in un'ondata, impostare la variabile di ambiente sull' `MSBuildDisableFeaturesFromVersion` Wave di modifica (o la versione di MSBuild) che contiene la funzionalità che si desidera disabilitare. Si tratta della versione di MSBuild per la quale sono state sviluppate le funzionalità. Vedere il mapping delle modifiche Wave alle funzionalità seguenti.

### <a name="msbuilddisablefeaturesfromversion-values"></a>Valori MSBuildDisableFeaturesFromVersion

Si riceverà un avviso e/o l'impostazione predefinita su un'onda specifica se non si imposta `MSBuildDisableFeaturesFromVersion` su un'onda di modifica valida. Nella tabella seguente vengono illustrate le possibili impostazioni:

| Valore di `MSBuildDisableFeaturesFromVersion`                         | Risultato        | Ricevere un avviso? |
| :-------------                                                    | :----------   | :----------: |
| Unset                                                             | Abilitare tutte le onde di modifica, ovvero tutte le funzionalità dietro ogni Wave di modifica sono abilitate.               | No   |
| Qualsiasi onda di modifica valida e corrente (ad esempio, `16.8` )                      | Disabilitare tutte le funzionalità associate a Change Wave `16.8` **e versioni successive**.                                           | No   |
| Valore non valido (ad esempio, `16.9` quando le onde valide sono `16.8` e `16.10` )| Impostazione predefinita sul valore valido più vicino (crescente). Ad esempio, l'impostazione `16.9` predefinita sarà `16.10` .               | No   |
| Fuori dalla rotazione (ad esempio, `17.1` quando l'onda più alta è `17.0` )      | Clamp sul valore valido più vicino. Ad esempio, `17.1` morsetti `17.0` e `16.5` morsetti a `16.8`                    | Sì  |
| Formato non valido (ad esempio,,, `16x8` `17_0` `garbage` )                    | Abilitare tutte le onde di modifica, ovvero tutte le funzionalità dietro ogni Wave di modifica sono abilitate.               | Sì  |

## <a name="change-waves-and-associated-features"></a>Modificare le onde e le funzionalità associate

I collegamenti nell'elenco seguente passano alla richiesta pull di GitHub per la funzionalità.

### <a name="168"></a>16,8

- [Abilita nowarn](https://github.com/dotnet/msbuild/pull/5671)
- [Tronca la destinazione/attività ignora i messaggi di log a 1024 caratteri](https://github.com/dotnet/msbuild/pull/5553)
- [Non espandere i glob di unità completa con la condizione falsa](https://github.com/dotnet/msbuild/pull/5669)

### <a name="1610"></a>16.10

- [Errore durante l'espansione di una proprietà in una condizione con spazi vuoti](https://github.com/dotnet/msbuild/pull/5672)

### <a name="170"></a>17.0

Non sono ancora presenti voci in questa Wave di modifica.

## <a name="change-waves-that-are-out-of-rotation"></a>Modificare le onde fuori dalla rotazione

Al momento non sono presenti onde di modifica della rotazione.

## <a name="faq"></a>Domande frequenti

**Perché usare ogni altra versione per ruotare le fluttuazioni delle modifiche?**

Si ritiene che questo sia un tempo sufficiente per discutere con le persone interessate e contribuire ad adattarsi alle modifiche.

**Perché una variabile di ambiente e non una proprietà del progetto?**

Esistono scenari in cui si vuole inserire una funzionalità in un'onda di modifica prima che MSBuild abbia caricato il progetto. Per questo motivo, è necessario usare le variabili di ambiente per le modifiche.

**Perché rifiutare esplicitamente il consenso esplicito?**

Il rifiuto esplicito è un approccio migliore, altrimenti è probabile che si ottengano Commenti limitati quando una funzionalità influisca sulle compilazioni dei clienti.

## <a name="see-also"></a>Vedi anche

- [MSBuild](msbuild.md)
- [Novità di MSBuild 16](whats-new-msbuild-16-0.md)
