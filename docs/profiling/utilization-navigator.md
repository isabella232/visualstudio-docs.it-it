---
title: Strumento di spostamento di utilizzo | Documenti di Microsoft
description: Informazioni su come usare lo strumento di navigazione utilizzo nel visualizzatore di concorrenza per selezionare un intervallo di tempo in una traccia.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.utilizationnavigator
ms.assetid: 522a981a-37ef-4cdd-a04c-f1e7525a2aab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6c7dbf162ad3325d99556b97c761d34358175041
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710160"
---
# <a name="utilization-navigator"></a>Strumento di spostamento di utilizzo
È possibile usare lo strumento di spostamento di utilizzo nel visualizzatore di concorrenza per selezionare un intervallo di tempo in una traccia. Il visualizzatore di concorrenza mostra l'utilizzo dei core della CPU da parte del processo di destinazione nel tempo. Questo rende più semplice esaminare i modelli di utilizzo della CPU e consente inoltre il confronto tra i dati di utilizzo e i dati in altre visualizzazioni. Lo strumento di spostamento di utilizzo è disponibile nella parte superiore di ogni visualizzazione nel visualizzatore di concorrenza. Nella figura seguente è illustrato lo strumento di spostamento di utilizzo.

 ![Strumento di navigazione utilizzo che mostra l'intervallo di tempo selezionato](../profiling/media/cvutilizationnavigator.png "CVUtilizationNavigator") Strumento di navigazione utilizzo e un intervallo di tempo selezionato

 Nell'illustrazione, l'intervallo selezionato è definito da un rettangolo rosso, denominato *controllo thumb*.

 Ecco come usare lo strumento di spostamento di utilizzo per modificare l'intervallo di tempo visualizzato:

- È possibile eseguire una panoramica trascinando il controllo thumb verso sinistra o destra. Da tastiera: spostare lo stato attivo sul controllo thumb, quindi premere il tasto freccia SINISTRA o DESTRA.

- È possibile modificare l'estensione dell'intervallo trascinando uno dei quadratini di ridimensionamento. Da tastiera: spostare lo stato attivo sul quadratino di ridimensionamento, quindi premere il tasto freccia DESTRA o SINISTRA.

  Se si modifica l'intervallo usando un altro controllo zoom del visualizzatore di concorrenza, lo strumento di spostamento di utilizzo viene aggiornato per riflettere la modifica.