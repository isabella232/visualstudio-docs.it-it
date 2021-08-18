---
title: Specificare opzioni di strumentazione aggiuntive | Microsoft Docs
description: Informazioni su come instrumentare i file binari usando l'IDE Visual Studio o gli strumenti da riga di comando.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c62f001f2714a90b250f34e43cd3a582d1f5f099
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150131"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Procedura: Specificare opzioni di strumentazione aggiuntive

È possibile instrumentare i file binari tramite l'IDE di Visual Studio o usando gli strumenti da riga di comando. Se si instrumenta un file binario dall'IDE, è possibile controllare il volume dei dati raccolti durante la strumentazione specificando opzioni di strumentazione aggiuntive per lo strumento [VSInstr](../profiling/vsinstr.md). Queste opzioni sono disponibili a livello di sessione o di destinazione. Ad esempio, per includere o escludere funzioni specifiche durante il processo di strumentazione, è possibile usare l'opzione di strumentazione aggiuntiva a livello di destinazione.

> [!IMPORTANT]
> Ogni probe inserito modifica leggermente il comportamento del programma originale, causando un sovraccarico in fase di analisi. Benché venga sottratta un'approssimazione di questo sovraccarico, si verificano comunque effetti minimi in termini di tempo sulle applicazioni con multithreading. Le opzioni dello strumento [VSInstr](../profiling/vsinstr.md) consentono di controllare la raccolta dei dati durante la profilatura.

## <a name="to-specify-additional-instrumentation-option"></a>Per specificare un'opzione di strumentazione aggiuntiva

1. In **Esplora prestazioni** selezionare **Sessione prestazioni** e quindi fare clic con il pulsante destro del mouse e selezionare **Proprietà**.

2. In **Pagine delle proprietà** fare clic sulle proprietà di **Avanzate**.

3. Digitare le opzioni nella casella **Opzioni di strumentazione aggiuntive**.

     Ad esempio, usare /CONTROL:THREAD per specificare il livello di profilatura. Per un elenco completo di opzioni, vedere [VSInstr](../profiling/vsinstr.md).

4. Fare clic su **OK**.

## <a name="see-also"></a>Vedi anche

[Configurare le sessioni di prestazioni](../profiling/configuring-performance-sessions.md) 
 [Profilare dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)
