---
title: Esportare e salvare mappe codice
ms.date: 05/16/2018
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 991773953338e38331bad45bfa1149aeb27c748b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670799"
---
# <a name="share-code-maps"></a>Condividere le mappe codice

È possibile salvare le mappe codice come parte di un progetto di Visual Studio, come un'immagine o come file XPS.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Condividere una mappa codice con altri utenti di Visual Studio

Usare il menu **File** per salvare la mappa.

oppure

Per salvare la mappa come parte di un progetto specifico, sulla barra degli strumenti della mappa scegliere **condividi**  > **Sposta \<CodeMapName >. dgml in**, quindi scegliere il progetto in cui si desidera salvare la mappa.

![Spostare una mappa in un altro progetto](../modeling/media/codemapsmovemapmenu.png)

Visual Studio salva la mappa come file con estensione *DGML* che è possibile condividere con altri utenti Visual Studio Enterprise e Visual Studio Professional.

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

1. Nella barra degli strumenti della mappa codice scegliere **condividi**  > **email come immagine** o **Copia immagine**.

2. Incollare l'immagine in un'altra applicazione.

## <a name="export-the-map-as-an-xps-file"></a>Esportare la mappa come file XPS

Quando si esporta una mappa codice come file XPS, è possibile visualizzarla in visualizzatori XAML o XML come Internet Explorer.

1. Nella barra degli strumenti della mappa codice scegliere **condividi**  > **messaggio di posta elettronica come** portabile XPS o **Salva come Portable XPS**.

2. Scegliere la posizione in cui salvare il file.

3. Assegnare un nome alla mappa codice. Assicurarsi che la casella **Salva come** sia impostata su **file XPS (\*. Xps)** . Scegliere **Salva**.

## <a name="see-also"></a>Vedere anche

- [Eseguire il mapping delle dipendenze con le mappe codice](../modeling/map-dependencies-across-your-solutions.md)