---
title: 'Procedura: Raccogliere i dati dei contatori CPU | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae991730caf5e83e9632d7b9a871a62778463098
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928568"
---
# <a name="how-to-collect-cpu-counter-data"></a>Procedura: Raccogliere i dati dei contatori CPU

Un contatore di eventi CPU viene usato per raccogliere i dati relativi alle prestazioni dell'hardware. Questo articolo illustra come raccogliere i dati del contatore degli eventi quando si usa il metodo di profilatura della strumentazione.

Si verificano due tipi di eventi del contatore CPU:

- Eventi portabili: eventi della CPU che possono essere raccolti indipendentemente dal tipo di CPU.

- Eventi piattaforma: eventi della CPU associati a un particolare tipo di CPU.

  Gli eventi portabili includono eventi generali, ad esempio le istruzioni ritirate e i cicli non interrotti, eventi del buffer della CPU, eventi di diramazione ed eventi della cache L2. I contatori degli eventi piattaforma disponibili sono determinati dal produttore del processore.

  Le categorie di eventi possono essere condivise tra contatori portabili e di piattaforma. Ad esempio, le categorie di dati seguenti sono spesso comuni a entrambi i tipi:

- Eventi memoria.

- Eventi front-end.

- Eventi di diramazione.

  Nel profiler è possibile raccogliere i dati del contatore di prestazioni in due modi:

- Raccogliere i dati da uno o più contatori quando si esegue la profilatura tramite strumentazione.

- Specificare un evento di contatore come intervallo di campionamento quando si esegue la profilatura mediante campionamento. Per altre informazioni, vedere [Procedura: Scegliere eventi di campionamento](../profiling/how-to-choose-sampling-events.md).

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Per raccogliere i dati dei contatori di prestazioni CPU quando si esegue la profilatura tramite strumentazione

1. In **Pagine delle proprietà** per la sessione di prestazioni fare clic su **Contatori CPU**.

2. Selezionare la casella di controllo **Raccogli contatori CPU**.

3. Espandere l'albero **Contatori di prestazioni disponibili** fino a individuare gli eventi di campionamento da raccogliere.

4. Per ogni evento di cui si vogliono raccogliere i dati, selezionare l'evento e quindi fare clic sulla freccia DESTRA per aggiungere l'evento all'elenco **Contatori selezionati**.

    > [!NOTE]
    > L'opzione **Contatori di prestazioni disponibili** è abilitata solo se si seleziona la casella di controllo **Raccogli contatori CPU**.

## <a name="see-also"></a>Vedere anche

[Configurare le sessioni di prestazioni](../profiling/configuring-performance-sessions.md)  
[Proprietà della sessione di prestazioni](../profiling/performance-session-properties.md)  
[Contatori CPU e Windows](../profiling/cpu-and-windows-counters.md)  
[Procedura: Scegliere eventi di campionamento](../profiling/how-to-choose-sampling-events.md)