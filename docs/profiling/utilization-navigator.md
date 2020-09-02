---
title: Strumento di spostamento di utilizzo | Documenti di Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.utilizationnavigator
ms.assetid: 522a981a-37ef-4cdd-a04c-f1e7525a2aab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94e2562e86af36d935679916c2bfb9669be1758d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62823485"
---
# <a name="utilization-navigator"></a>Strumento di spostamento di utilizzo
È possibile usare lo strumento di spostamento di utilizzo nel visualizzatore di concorrenza per selezionare un intervallo di tempo in una traccia. Il visualizzatore di concorrenza mostra l'utilizzo dei core della CPU da parte del processo di destinazione nel tempo. Questo rende più semplice esaminare i modelli di utilizzo della CPU e consente inoltre il confronto tra i dati di utilizzo e i dati in altre visualizzazioni. Lo strumento di spostamento di utilizzo è disponibile nella parte superiore di ogni visualizzazione nel visualizzatore di concorrenza. Nella figura seguente è illustrato lo strumento di spostamento di utilizzo.

 ![Strumento di spostamento di utilizzo che mostra l'intervallo](../profiling/media/cvutilizationnavigator.png "CVUtilizationNavigator") di tempo selezionato Strumento di spostamento di utilizzo e intervallo di tempo selezionato

 Nell'illustrazione, l'intervallo selezionato è definito da un rettangolo rosso, denominato *controllo thumb*.

 Ecco come usare lo strumento di spostamento di utilizzo per modificare l'intervallo di tempo visualizzato:

- È possibile eseguire una panoramica trascinando il controllo thumb verso sinistra o destra. Da tastiera: spostare lo stato attivo sul controllo thumb, quindi premere il tasto freccia SINISTRA o DESTRA.

- È possibile modificare l'estensione dell'intervallo trascinando uno dei quadratini di ridimensionamento. Da tastiera: spostare lo stato attivo sul quadratino di ridimensionamento, quindi premere il tasto freccia DESTRA o SINISTRA.

  Se si modifica l'intervallo usando un altro controllo zoom del visualizzatore di concorrenza, lo strumento di spostamento di utilizzo viene aggiornato per riflettere la modifica.