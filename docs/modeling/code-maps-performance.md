---
title: Le mappe del codice sono particolarmente lunghi
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 2dece1e63fffdba67678422ad9241babc63b7abd
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34267699"
---
# <a name="improve-performance-for-code-maps"></a>Migliorare le prestazioni per le mappe del codice

Quando si genera una mappa per la prima volta, Visual Studio indicizza tutte le dipendenze trovate. Questo processo potrebbe richiedere del tempo, soprattutto per soluzioni di grandi dimensioni, ma migliora le prestazioni delle successive. Se il codice viene modificato, Visual Studio reindicizza solo il codice aggiornato. Per ridurre al minimo il tempo impiegato per la mappa terminare il rendering, prendere in considerazione i suggerimenti seguenti:

- [Eseguire il mapping di tutte le dipendenze che interessano.](#create-a-code-map-to-see-specific-dependencies)

- Prima di generare la mappa per un'intera soluzione, ridurre l'ambito della soluzione.

- Disattivare la compilazione automatica per la soluzione selezionando **Skip Build** sulla barra degli strumenti della mappa codice.

- Disattivare la compilazione automatica degli elementi padre selezionando **Includi padri** sulla barra degli strumenti della mappa codice.

   ![Ignorare i pulsanti Compila e Includi padri](../modeling/media/codemapsfilterskipbuildicons.png)

- Modificare il file della mappa codice per rimuovere i nodi e i collegamenti non necessari. La modifica della mappa non influisce in alcun modo sul codice sottostante. Vedere [Personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Potrebbe richiedere più tempo per creare mappe o aggiungere elementi a una mappa da **Esplora soluzioni** quando un elemento di progetto **copia in Directory di Output** è impostata su **Copia sempre**. Per aumentare le prestazioni, impostare questa proprietà su **Copia se più recente** o su `PreserveNewest`. Vedere [compilazioni incrementali](../msbuild/incremental-builds.md).

La mappa completata Mostra dipendenze solo per codice compilato correttamente. Se si verificano errori di compilazione per determinati componenti, tali errori vengono visualizzati nella mappa. Assicurarsi quindi che un componente venga effettivamente compilato e contenga le dipendenze prima di prendere decisioni a livello di architettura in base alla mappa.