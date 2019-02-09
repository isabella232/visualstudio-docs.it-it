---
title: Esportare e salvare le mappe codice
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70c4cd238b6e5d31eced6a35ff0c7d24ab85a280
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907893"
---
# <a name="share-code-maps"></a>Condividere le mappe codice

È possibile salvare mappe del codice come parte di un progetto di Visual Studio, come un'immagine o come file XPS.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Condividere una mappa codice con altri utenti di Visual Studio

Usare il menu **File** per salvare la mappa.

-oppure-

Per salvare la mappa come parte del progetto specifico, sulla barra degli strumenti della mappa, scegliere **Share** > **spostare \<nome mappa codice > DGML in**e quindi scegliere il progetto in cui si desidera salvare il eseguire il mapping.

![Spostare una mappa in un altro progetto](../modeling/media/codemapsmovemapmenu.png)

Visual Studio salva l'oggetto map come un *DGML* file che è possibile condividere con altri utenti di Visual Studio Enterprise e Visual Studio Professional.

> [!NOTE]
> Prima di condividere una mappa con gli utenti che usano Visual Studio Professional, assicurarsi di espandere tutti i gruppi, visualizzare i nodi nascosti e i collegamenti tra gruppi e recuperare tutti i nodi eliminati che si vuole vengano visualizzati da altri nella mappa. In caso contrario, altri utenti non saranno in grado di visualizzare questi elementi.
>
> Quando si salva una mappa che è contenuta in un progetto di modellazione o che è stata copiata da un progetto di modellazione in un altro percorso potrebbe verificarsi l'errore seguente:
>
> "Impossibile salvare *nomeFile* all'esterno della directory del progetto. Gli elementi collegati non sono supportati."
>
> In Visual Studio viene visualizzato l'errore, ma viene comunque creata la versione salvata. Per evitare l'errore, creare la mappa all'esterno del progetto di modellazione. Sarà quindi possibile salvarlo quindi nel percorso desiderato. Il semplice tentativo di copiare il file in un altro percorso della soluzione e salvarlo non produrrà alcun effetto.

## <a name="export-a-code-map-as-an-image"></a>Esportare una mappa del codice come immagine

Quando si esporta una mappa del codice come un'immagine, è possibile copiarlo in altre applicazioni, ad esempio Microsoft Word o PowerPoint.

1. Sulla barra degli strumenti della mappa del codice, scegliere **Share** > **messaggio di posta elettronica come immagine** oppure **Copia immagine**.

2. Incollare l'immagine in un'altra applicazione.

## <a name="export-the-map-as-an-xps-file"></a>Esportare la mappa come file XPS

Quando si esporta una mappa del codice come file XPS, è possibile visualizzarlo nei visualizzatori XAML o XML come Internet Explorer.

1. Sulla barra degli strumenti della mappa del codice, scegliere **Share** > **Invia come Portable XPS** oppure **Salva come Portable XPS**.

2. Scegliere la posizione in cui salvare il file.

3. Assegnare un nome alla mappa codice. Assicurarsi che il **Salva come tipo** casella viene impostata su **file XPS (\*XPS)**. Scegliere **Salva**.

## <a name="see-also"></a>Vedere anche

- [Mappare le dipendenze con le mappe codici](../modeling/map-dependencies-across-your-solutions.md)