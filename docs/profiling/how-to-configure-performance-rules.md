---
title: Configurare le regole di prestazioni | Microsoft Docs
description: Prestare attenzione agli avvisi del Visual Studio Strumenti di profilatura, che possono portare a metodi di raccolta migliori. Sono disponibili nella finestra Elenco errori.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 810b3c02e0fa248b760da5c5684eabd4fce5d73123d4262bd58bbd71d048b701
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410749"
---
# <a name="how-to-configure-performance-rules"></a>Procedura: Configurare le regole per le prestazioni
Gli avvisi relativi alle prestazioni del Visual Studio Strumenti di profilatura indicano problemi in un'applicazione profilata che possono rallentare l'esecuzione del programma. Gli avvisi possono anche indicare che potrebbe essere necessario modificare i metodi di raccolta per raccogliere dati più utili. Gli avvisi di prestazioni vengono generati automaticamente in una sessione di profilatura e visualizzati nella finestra **Elenco errori** quando un file di dati di profilatura viene aperto in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Alcuni avvisi potrebbero non essere applicabili agli scenari desiderati, mentre altri potrebbero essere generati in modo non corretto. È possibile configurare gli avvisi di prestazioni per mostrare o nascondere avvisi specifici.

### <a name="to-configure-profiler-performance-warnings"></a>Per configurare gli avvisi di prestazioni del profiler

1. Scegliere **Opzioni** dal menu **Strumenti**.

2. Espandere **Strumenti per le prestazioni** e quindi fare clic su **Regole**.

3. Per abilitare o disabilitare un avviso, selezionare o deselezionare la casella di controllo accanto all'**ID** e al nome dell'avviso.

4. Per specificare il livello di avviso di una regola, fare clic sulla cella **Azione** accanto alla regola e quindi fare clic sul livello di avviso.

    - **Disabilitato**: disabilita la regola ed equivale a deselezionare la casella di controllo accanto all'ID della regola.

    - **Avviso**: visualizza la regola come avviso.

    - **Errore**: interrompe l'esecuzione della profilatura e visualizza la regola come errore.

    - **Informazioni**: visualizza la regola solo a scopo informativo.
