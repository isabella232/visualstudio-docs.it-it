---
title: DA0006 - Eseguire l'override di Equals() per i tipi | Microsoft Docs
description: Le chiamate al metodo Equals o agli operatori di uguaglianza di un tipo valore pubblico rappresentano una percentuale significativa dei dati di profilatura.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0abdfb412d4adada9f4e41fd98258abfa1cb88e1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107888"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Eseguire l'override di Equals() per i tipi di valore

|Elemento|valore|
|-|-|
|ID regola|DA0006|
|Category|Uso di .NET Framework|
|Metodi di profilatura|campionamento|
|Message|Eseguire l'override di Equals e dell'operatore di uguaglianza sui tipi di valore.|
|Tipo di messaggio|Avviso|

## <a name="cause"></a>Causa
 Le chiamate al metodo Equals o agli operatori di uguaglianza di un tipo valore pubblico rappresentano una percentuale significativa dei dati di profilatura. Considerare la possibilità di implementare un metodo più efficiente.

## <a name="rule-description"></a>Descrizione della regola
 Per i tipi di valore, l'implementazione ereditata di Equals usa la libreria <xref:System.Reflection> e confronta il contenuto di tutti i campi del tipo. La libreria Reflection è onerosa dal punto di vista del calcolo, inoltre il confronto di ogni campo per determinarne l'uguaglianza potrebbe essere superfluo. Se si prevede che gli utenti confrontino o ordinino le istanze oppure le usino come chiavi di tabelle hash, il tipo di valore deve implementare Equals. Se il linguaggio di programmazione in uso supporta l'overload degli operatori, è necessario specificare anche un'implementazione degli operatori di uguaglianza e disuguaglianza.

 Per altre informazioni su come eseguire l'override del metodo Equals e degli operatori di uguaglianza, vedere [Linee guida per l'implementazione del metodo Equals e dell'operatore di uguaglianza (==)](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to-investigate-a-warning"></a>Come esaminare un avviso
 Per un esempio di implementazione di Equals e degli operatori di uguaglianza, vedere la regola di analisi del codice [CA1815: Eseguire l'override di Equals e dell'operatore " uguale a" sui tipi di valore](/dotnet/fundamentals/code-analysis/quality-rules/ca1815)
