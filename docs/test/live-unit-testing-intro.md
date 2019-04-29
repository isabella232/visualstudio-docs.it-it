---
title: Introduzione a Live Unit Testing
description: Informazioni sui vantaggi di Live Unit Testing e su come usarlo quando si esegue il testing unità dei progetti.
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: a5acf1857309236727cd0bab4d9d981d814292b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786081"
---
# <a name="live-unit-testing-introduction"></a>Introduzione a Live Unit Testing

Live Unit Testing è una tecnologia introdotta in Visual Studio 2017. Esegue automaticamente gli unit test in tempo reale mentre si apportano modifiche al codice.

Live Unit Testing:

- Consente di eseguire il refactoring e di modificare il codice in modo più sicuro. Live Unit Testing esegue automaticamente tutti i test pertinenti quando si modifica il codice per garantire che le modifiche non interrompano i test.

- Indica se gli unit test coprono il codice in modo adeguato e visualizza il codice non coperto dai test. Live Unit Testing illustra graficamente il code coverage in tempo reale, in modo da visualizzare a colpo d'occhio sia il numero di test che coprono ogni riga di codice sia le righe non coperte da alcun test.

Se si ha una soluzione che include uno o più progetti di unit test, è possibile abilitare Live Unit Testing selezionando **Test** > **Live Unit Testing** > **Avvia** dal menu di primo livello di Visual Studio.

> [!NOTE]
> Live Unit Testing è disponibile solo in Visual Studio Enterprise Edition.

Per altre informazioni su Live Unit Testing:

- Vedere l'esercitazione introduttiva, [Introduzione a Live Unit Testing](live-unit-testing-start.md).

- Leggere la documentazione dettagliata in [Usare Live Unit Testing in Visual Studio Enterprise Edition](live-unit-testing.md).

- Leggere le [Domande frequenti su Live Unit Testing](live-unit-testing-faq.md) per informazioni sulle novità, nonché per suggerimenti e tecniche.

- Guardare il video di Channel 9 per una panoramica di Live Unit Testing e delle relative funzionalità. </p>

   > [!VIDEO https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105/player]

## <a name="related-resources"></a>Risorse correlate

- [Strumenti di test del codice](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Eseguire unit test del codice](unit-test-your-code.md)
