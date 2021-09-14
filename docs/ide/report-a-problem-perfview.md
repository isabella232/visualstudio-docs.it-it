---
description: PerfView è uno strumento che crea file ETL (log di traccia eventi) basati su Event Tracing for Windows) che possono essere utili per la risoluzione di alcuni tipi di problemi con Visual Studio.
title: Raccogliere una traccia ETL con PerfView
ms.date: 09/27/2019
ms.topic: how-to
helpviewer_keywords:
- perfview
- ETL Trace
author: corob-msft
ms.author: corob
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: e68b8ab22ea4c045c54195381502458f915c3008
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628530"
---
# <a name="collect-an-etl-trace-with-perfview"></a>Raccogliere una traccia ETL con PerfView

PerfView è uno strumento che consente di creare file ETL (log di traccia eventi) basati su [Event Tracing for Windows](/windows/desktop/ETW/event-tracing-portal) che possono essere utili per la risoluzione di alcuni tipi di problemi con Visual Studio. In alcuni casi quando si segnala un problema, il team del prodotto potrebbe richiedere di eseguire PerfView per raccogliere informazioni aggiuntive.

## <a name="install-perfview"></a>Installare PerfView

Scaricare PerfView da [GitHub](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md).

## <a name="run-perfview"></a>Eseguire PerfView

1. Fare clic con il pulsante destro del mouse su **PerfView.exe** in Esplora risorse e scegliere **Esegui come amministratore**.
1. Scegliere **Collect** (Raccogli) dal menu Collect (Raccogli).
1. Selezionare **Zip**, **Merge** (Unisci) e **Thread Time** (Tempo thread).
1. Aumentare **Circular MB** (MB circolari) a 1000.
1. Modificare **Current Dir** (Dir corrente) per salvare le tracce ETL in una cartella specificata e Data File (File di dati) se si prevede di eseguire la raccolta più volte.
1. Per avviare la registrazione dei dati, scegliere il pulsante **Start Collection** (Avvia raccolta).
1. Per interrompere la registrazione dei dati, scegliere il pulsante **Stop Collection** (Arresta raccolta). Il file PrefView.etl.zip verrà salvato nella directory specificata.

PerfView può archiviare solo i dati più recenti che rientrano nel buffer. Provare quindi ad arrestare la raccolta il prima possibile quando Visual Studio inizia a bloccarsi o a rallentare. Non proseguire la raccolta per più di 30 secondi dopo aver riscontrato un problema.

Per altre informazioni, vedere l'[esercitazione di PerfView su Channel 9](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).
