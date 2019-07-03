---
title: Raccogliere una traccia ETL con PerfView
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- perfview
- ETL Trace
author: mikeblome
ms.author: mblome
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: baae89b7bf45a4848c571f75e37c6cc0d203d459
ms.sourcegitcommit: 6f7a740750b2cd17ea2275c3d046caebc9782917
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67518187"
---
# <a name="collect-an-etl-trace-with-perfview"></a>Raccogliere una traccia ETL con PerfView

PerfView è uno strumento che consente di creare file ETL (log di traccia eventi) basato su [Event Tracing for Windows](/windows/desktop/ETW/event-tracing-portal), che può essere utile per la risoluzione di alcuni tipi di problemi con Visual Studio. In alcuni casi quando si segnala un problema, il team del prodotto potrebbe richiedere di eseguire PerfView per raccogliere informazioni aggiuntive.

## <a name="install-perfview"></a>Installare PerfView

Scaricare PerfView dall'[Area download Microsoft](http://www.microsoft.com/download/details.aspx?id=28567).

## <a name="run-perfview"></a>Eseguire PerfView

1. Fare clic con il pulsante destro del mouse su **PerfView.exe** in Esplora risorse e scegliere **Esegui come amministratore**.
1. Scegliere **Collect** (Raccogli) dal menu Collect (Raccogli).
1. Selezionare **Zip**, **Merge** (Unisci) e **Thread Time** (Tempo thread).
1. Aumentare **Circular MB** (MB circolari) a 1000.
1. Modificare **Current Dir** (Dir corrente) per salvare le tracce ETL in una cartella specificata e Data File (File di dati) se si prevede di eseguire la raccolta più volte.
1. Per avviare la registrazione dei dati, scegliere il pulsante **Start Collection** (Avvia raccolta).
1. Per interrompere la registrazione dei dati, scegliere il pulsante **Stop Collection** (Arresta raccolta). Il file PrefView.etl.zip verrà salvato nella directory specificata.

PerfView può archiviare solo i dati più recenti che rientrano nel buffer. Provare quindi ad arrestare la raccolta il prima possibile quando Visual Studio inizia a bloccarsi o a rallentare. Non proseguire la raccolta per più di 30 secondi dopo aver riscontrato un problema.

Per altre informazioni, vedere l'[esercitazione di PerfView su Channel 9](http://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).
