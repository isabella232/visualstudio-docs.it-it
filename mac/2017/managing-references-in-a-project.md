---
title: Gestione dei riferimenti in un progetto
description: Questo articolo descrive come gestire i riferimenti in un progetto in Visual Studio per Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.topic: overview
ms.openlocfilehash: 3dfeea15e0d9003e3ae0e46b74c844016d298595
ms.sourcegitcommit: 879ba768364f3bfdaeb9004f740478489ab15c3a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2021
ms.locfileid: "114796190"
---
# <a name="managing-references-in-a-project"></a>Gestione dei riferimenti in un progetto

Visual Studio per Mac offre due modi per aggiungere ulteriori riferimenti al progetto:

![Riferimenti al progetto](media/projects-and-solutions-image10.png)

Si tratta di:

* Bibliografia
* Pacchetti NuGet (aggiunti tramite la cartella Pacchetti)

A qualsiasi progetto è anche possibile aggiungere riferimenti Web e riferimenti nativi.

## <a name="assembly-references"></a>Riferimenti ad assembly

Ogni framework in Xamarin include più di una dozzina di assembly. Non a tutti i pacchetti di assembly viene fatto riferimento nel progetto per impostazione predefinita.

Per modificare i pacchetti a cui viene fatto riferimento nel progetto, usare la finestra di dialogo **Modifica riferimenti**, che è possibile visualizzare facendo doppio clic sulla cartella Riferimenti oppure scegliendo **Modifica riferimenti** tra le azioni del menu di scelta rapida:

![Finestra di dialogo dei riferimenti ad assembly](media/projects-and-solutions-image11.png)

Per informazioni sugli assembly disponibili per ogni framework Xamarin, vedere la guida agli [assembly disponibili](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/).

## <a name="nuget"></a>NuGet

NuGet è il più diffuso strumento di gestione pacchetti per lo sviluppo .NET. Il supporto di NuGet di Visual Studio per Mac consente di cercare i pacchetti da aggiungere al progetto.

A tale scopo, fare clic con il pulsante destro del mouse sulla cartella **Pacchetto** nel riquadro della soluzione e scegliere Aggiungi pacchetti.

Per altre informazioni sull'uso di un pacchetto NuGet, vedere la procedura guidata [Inserimento di un pacchetto NuGet nel progetto](nuget-walkthrough.md).

## <a name="see-also"></a>Vedere anche

- [Gestire i riferimenti (Visual Studio in Windows)](/visualstudio/ide/managing-references-in-a-project)
- [NuGet sdk come riferimento al progetto](/visualstudio/extensibility/nuget-versus-sdk-references)
