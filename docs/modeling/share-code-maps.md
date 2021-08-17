---
title: Esportare e salvare mappe codice
description: Informazioni su come salvare le mappe codice come parte di un Visual Studio, come immagine o come file XPS.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: d6efe3f860749ac24e35af944122ec8a9d121f6039270117e7eb52eb57fcf6f7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410938"
---
# <a name="share-code-maps"></a>Condividere le mappe codice

È possibile salvare le mappe codice come parte di un Visual Studio, come immagine o come file XPS.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Condividere una mappa del codice con altri Visual Studio utenti

Usare il menu **File** per salvare la mappa.

-oppure-

Per salvare la mappa come parte di un progetto specifico, sulla barra degli strumenti della mappa scegliere Condividi Sposta  >  **\<CodeMapName> .dgml in** e quindi scegliere il progetto in cui si vuole salvare la mappa.

![Spostare una mappa in un altro progetto](../modeling/media/codemapsmovemapmenu.png)

Visual Studio salva la mappa come file con estensione *dgml* che è possibile condividere con altri utenti di Visual Studio Enterprise e Visual Studio Professional.

> [!NOTE]
> Prima di condividere una mappa con gli utenti che usano Visual Studio Professional, assicurarsi di espandere tutti i gruppi, visualizzare i nodi nascosti e i collegamenti tra gruppi e recuperare tutti i nodi eliminati che si vuole vengano visualizzati da altri nella mappa. In caso contrario, altri utenti non saranno in grado di visualizzare questi elementi.
>
> Quando si salva una mappa che è contenuta in un progetto di modellazione o che è stata copiata da un progetto di modellazione in un altro percorso potrebbe verificarsi l'errore seguente:
>
> "Impossibile salvare *nomeFile* all'esterno della directory del progetto. Gli elementi collegati non sono supportati."
>
> In Visual Studio viene visualizzato l'errore, ma viene comunque creata la versione salvata. Per evitare l'errore, creare la mappa all'esterno del progetto di modellazione. Sarà quindi possibile salvarlo quindi nel percorso desiderato. Il semplice tentativo di copiare il file in un altro percorso della soluzione e salvarlo non produrrà alcun effetto.

## <a name="export-a-code-map-as-an-image"></a>Esportare una mappa codice come immagine

Quando si esporta una mappa codice come immagine, è possibile copiarla in altre applicazioni, ad esempio Microsoft Word o PowerPoint.

1. Sulla barra degli strumenti della mappa codice scegliere **Condividi**  >  **messaggio di posta elettronica come immagine** o **Copia immagine**.

2. Incollare l'immagine in un'altra applicazione.

## <a name="export-the-map-as-an-xps-file"></a>Esportare la mappa come file XPS

Quando si esporta una mappa codice come file XPS, è possibile visualizzarla in visualizzatori XML o XAML come Internet Explorer.

1. Sulla barra degli strumenti della mappa codice scegliere **Condividi**  >  **messaggio di posta elettronica come XPS portabile** o **Salva come XPS portabile**.

2. Scegliere la posizione in cui salvare il file.

3. Assegnare un nome alla mappa codice. Assicurarsi che la **casella Tipo file** sia impostata su File **XPS \* (con estensione xps).** Scegliere **Salva**.

## <a name="see-also"></a>Vedi anche

- [Eseguire il mapping delle dipendenze con mappe codice](../modeling/map-dependencies-across-your-solutions.md)
