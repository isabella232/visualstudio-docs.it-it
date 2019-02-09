---
title: Le mappe codici sono lente
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f53376d1cff79dd69b7fb17704c4ddae8803c46
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913184"
---
# <a name="improve-performance-for-code-maps"></a>Migliorare le prestazioni per le mappe codice

Quando si genera una mappa per la prima volta, Visual Studio indicizza tutte le dipendenze trovate. Questo processo potrebbe richiedere molto tempo, in particolare per soluzioni di grandi dimensioni, ma consente di migliorare le prestazioni successive. Se il codice viene modificato, Visual Studio reindicizza solo il codice aggiornato. Per ridurre al minimo il tempo impiegato per la mappa terminare il rendering, prendere in considerazione i suggerimenti seguenti:

- [Eseguire il mapping solo delle dipendenze che interessano.](#create-a-code-map-to-see-specific-dependencies)

- Prima di generare la mappa per un'intera soluzione, ridurre l'ambito della soluzione.

- Disattivare la compilazione automatica per la soluzione selezionando **Skip Build** sulla barra degli strumenti della mappa codice.

- Disattivare la compilazione automatica degli elementi padre selezionando **Includi padri** sulla barra degli strumenti della mappa codice.

   ![Ignorare i pulsanti Compila e Includi padri](../modeling/media/codemapsfilterskipbuildicons.png)

- Modificare il file della mappa codice per rimuovere i nodi e i collegamenti non necessari. La modifica della mappa non influisce in alcun modo sul codice sottostante. Vedere [Personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Potrebbe essere necessario più tempo alla creazione di mappe o aggiungere elementi a una mappa dal **Esplora soluzioni** quando un elemento di progetto **Copy to Output Directory** viene impostata su **Copia sempre**. Per aumentare le prestazioni, impostare questa proprietà su **Copia se più recente** o su `PreserveNewest`. Visualizzare [le compilazioni incrementali](../msbuild/incremental-builds.md).

La mappa completata Mostra le dipendenze solo per codice compilato correttamente. Se si verificano errori di compilazione per determinati componenti, tali errori vengono visualizzati nella mappa. Assicurarsi quindi che un componente venga effettivamente compilato e contenga le dipendenze prima di prendere decisioni a livello di architettura in base alla mappa.