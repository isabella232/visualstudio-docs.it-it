---
title: Intercettazione di comandi del servizio di linguaggio legacy | Microsoft Docs
description: Informazioni su come usare i filtri dei comandi in Visual Studio per intercettare i comandi dei servizi di linguaggio legacy e aggiungere un comportamento specifico della lingua.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8d7af9ff4a8f04382cff4999b8c57549f3da3db7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074678"
---
# <a name="intercepting-legacy-language-service-commands"></a>Intercettazione dei comandi dei servizi di linguaggio legacy
Con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , è possibile fare in modo che il servizio di linguaggio possa intercettare i comandi che la visualizzazione di testo altrimenti gestirebbe. Questa operazione è utile per comportamenti specifici della lingua non gestiti dalla visualizzazione di testo. È possibile intercettare questi comandi aggiungendo uno o più filtri di comando alla visualizzazione di testo dal servizio di linguaggio.

## <a name="getting-and-routing-the-command"></a>Recupero e routing del comando
 Un filtro di comando è un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oggetto che monitora determinate sequenze di caratteri o comandi chiave. È possibile associare più di un filtro di comando a una sola visualizzazione di testo. Ogni visualizzazione di testo gestisce una catena di filtri di comando. Dopo aver creato un nuovo filtro dei comandi, aggiungere il filtro alla catena per la visualizzazione di testo appropriata.

 Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo sull'oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per aggiungere il filtro del comando alla catena. Quando si chiama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> , [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] restituisce un altro filtro di comando a cui è possibile passare i comandi non gestiti dal filtro dei comandi.

 Per la gestione dei comandi sono disponibili le opzioni seguenti:

- Gestire il comando e quindi passare il comando al filtro del comando successivo nella catena.

- Gestire il comando e non passare il comando al filtro del comando successivo.

- Non gestire il comando, ma passare il comando al filtro del comando successivo.

- Ignorare il comando. Non gestirla nel filtro corrente e non passarla al filtro successivo.

  Per informazioni sui comandi che il servizio di linguaggio deve gestire, vedere [comandi importanti per i filtri dei servizi di linguaggio](../../extensibility/internals/important-commands-for-language-service-filters.md).
