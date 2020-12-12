---
title: Le mappe codice sono lente
description: Informazioni su come migliorare le prestazioni della mappa del codice e su come ridurre al minimo il tempo necessario per completare il rendering.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edcc12b5bd2cb741374acfe44f05c1f9043ebcaa
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363510"
---
# <a name="improve-performance-for-code-maps"></a>Migliorare le prestazioni per le mappe codice

Quando si genera una mappa per la prima volta, Visual Studio indicizza tutte le dipendenze trovate. Questo processo può richiedere del tempo, soprattutto per le soluzioni di grandi dimensioni, ma migliora le prestazioni successive. Se il codice viene modificato, Visual Studio reindicizza solo il codice aggiornato. Per ridurre al minimo il tempo impiegato per completare il rendering della mappa, tenere presenti i suggerimenti seguenti:

- Eseguire il mapping solo delle dipendenze che interessano.

- Prima di generare la mappa per un'intera soluzione, ridurre l'ambito della soluzione.

- Disattivare la compilazione automatica per la soluzione selezionando **Ignora compilazione** sulla barra degli strumenti della mappa codice.

- Disabilitare l'aggiunta automatica di elementi padre selezionando **Includi padri** nella barra degli strumenti della mappa codice.

   ![Ignorare i pulsanti Compila e Includi padri](../modeling/media/codemapsfilterskipbuildicons.png)

- Modificare il file della mappa codice per rimuovere i nodi e i collegamenti non necessari. La modifica della mappa non influisce in alcun modo sul codice sottostante. Vedere [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

La creazione di mappe o l'aggiunta di elementi a una mappa da **Esplora soluzioni** quando la proprietà **copia nella directory di output** di un elemento di progetto è impostata su **copia sempre**, potrebbe richiedere più tempo. Per aumentare le prestazioni, impostare questa proprietà su **Copia se più recente** o su `PreserveNewest`. Vedere [compilazioni incrementali](../msbuild/incremental-builds.md).

La mappa completata Mostra le dipendenze solo per il codice compilato correttamente. Se si verificano errori di compilazione per determinati componenti, tali errori vengono visualizzati nella mappa. Assicurarsi quindi che un componente venga effettivamente compilato e contenga le dipendenze prima di prendere decisioni a livello di architettura in base alla mappa.
