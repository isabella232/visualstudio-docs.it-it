---
title: Rapporto marcatori | Microsoft Docs
description: Informazioni su come il report marcatori elenca i marcatori nell'intervallo di tempo visualizzato e su come la panoramica o lo zoom potrebbe causare la visualizzazione o la scomparsa dei marcatori.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a2a406279d8e9123d342cd63d648206fd35c7b5f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033317"
---
# <a name="markers-report"></a>Rapporto marcatori
Il rapporto Marcatori elenca i marcatori nell'intervallo di tempo visualizzato.  La panoramica o lo zoom così come le corsie nascoste potrebbero far comparire o scomparire i marcatori. Il rapporto contiene le informazioni seguenti per ogni marcatore:

- L'ora in cui è stato avviato, rispetto all'inizio della traccia.

- La durata. La durata è zero per i flag e i messaggi poiché rappresentano un istante.

- L'ID del thread che lo ha generato.

- Il provider ETW (Event Tracking for Windows) che lo ha generato.

- La serie di marcatori da cui è stato scritto.

- La categoria di eventi a cui appartiene.

- Il livello di importanza.

- Il tipo (intervallo, flag o messaggio).

- Una descrizione dettagliata di cosa rappresenta.

  Scegliere il pulsante **Esporta** per salvare il rapporto Marcatori come file con estensione csv. È possibile usare i dati nel file con estensione csv con altre app o strumenti.

> [!NOTE]
> Il rapporto Marcatori può visualizzare 1000 marcatori. Per visualizzare tutti i marcatori, esportare il rapporto completo in un file con estensione csv.