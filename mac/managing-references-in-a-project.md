---
title: Gestione dei riferimenti in un progetto
description: Questo articolo descrive come gestire i riferimenti in un progetto in Visual Studio per Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: 79d96ac61bcec198c899d709677df775332db383
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224174"
---
# <a name="managing-references-in-a-project"></a>Gestione dei riferimenti in un progetto

Visual Studio per Mac offre due modi per aggiungere ulteriori riferimenti al progetto:

![Riferimenti al progetto](media/projects-and-solutions-image10.png)

Questi sono:

* Riferimenti
* Pacchetti NuGet (aggiunti tramite la cartella Pacchetti)

A qualsiasi progetto è anche possibile aggiungere riferimenti Web e riferimenti nativi.

## <a name="assembly-references"></a>Riferimenti ad assembly

Ogni framework in Xamarin include più di una dozzina di assembly. Non a tutti i pacchetti di assembly viene fatto riferimento nel progetto per impostazione predefinita. 

Per modificare i pacchetti a cui viene fatto riferimento nel progetto, usare la finestra di dialogo _Modifica riferimenti_, che è possibile visualizzare facendo doppio clic sulla cartella Riferimenti oppure scegliendo Modifica riferimenti tra le azioni del menu di scelta rapida:

![Finestra di dialogo dei riferimenti ad assembly](media/projects-and-solutions-image11.png)

Per informazioni sugli assembly disponibili per ogni framework Xamarin, vedere la guida agli [assembly disponibili](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/).

## <a name="nuget"></a>NuGet

NuGet è il più diffuso strumento di gestione pacchetti per lo sviluppo .NET. Il supporto di NuGet di Visual Studio per Mac consente di cercare i pacchetti da aggiungere al progetto.

A tale scopo, fare clic con il pulsante destro del mouse sulla cartella **Pacchetto** nel riquadro della soluzione e scegliere Aggiungi pacchetti.

Per altre informazioni sull'uso di un pacchetto NuGet, vedere la procedura guidata [Inserimento di un pacchetto NuGet nel progetto](nuget-walkthrough.md).
