---
title: Le mappe codice sono lente
description: Informazioni su come migliorare le prestazioni della mappa codice e su come ridurre al minimo il tempo necessario per completare il rendering.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: c877554685a3a8111d529fab0fa58be4e4f00f4d8a86716a716391cbc97ac55e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121411250"
---
# <a name="improve-performance-for-code-maps"></a>Migliorare le prestazioni per le mappe codice

Quando si genera una mappa per la prima volta, Visual Studio indicizza tutte le dipendenze trovate. Questo processo potrebbe richiedere tempo, soprattutto per soluzioni di grandi dimensioni, ma migliora le prestazioni successive. Se il codice viene modificato, Visual Studio reindicizza solo il codice aggiornato. Per ridurre al minimo il tempo impiegato per completare il rendering della mappa, prendere in considerazione i suggerimenti seguenti:

- Eseguire il mapping solo delle dipendenze che interessano.

- Prima di generare la mappa per un'intera soluzione, ridurre l'ambito della soluzione.

- Disattivare la compilazione automatica per la soluzione selezionando Ignora compilazione **sulla barra** degli strumenti della mappa codice.

- Disattivare l'aggiunta automatica di elementi padre selezionando **Includi elementi padre sulla** barra degli strumenti della mappa codice.

   ![Ignorare i pulsanti Compila e Includi padri](../modeling/media/codemapsfilterskipbuildicons.png)

- Modificare il file della mappa codice per rimuovere i nodi e i collegamenti non necessari. La modifica della mappa non influisce in alcun modo sul codice sottostante. Vedere [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

La creazione di mappe o l'aggiunta di elementi a una mappa da **Esplora soluzioni** quando la proprietà Copia nella directory di **output** di un elemento di progetto è impostata su **Copia sempre**. Per aumentare le prestazioni, impostare questa proprietà su **Copia se più recente** o su `PreserveNewest`. Vedere [Compilazioni incrementali.](../msbuild/incremental-builds.md)

La mappa completata mostra le dipendenze solo per il codice compilato correttamente. Se si verificano errori di compilazione per determinati componenti, tali errori vengono visualizzati nella mappa. Assicurarsi quindi che un componente venga effettivamente compilato e contenga le dipendenze prima di prendere decisioni a livello di architettura in base alla mappa.
