---
title: Intercettazione dei comandi del servizio di linguaggio Legacy Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5206bced8b4bfae32498434765e5c3f61801b386
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707443"
---
# <a name="intercepting-legacy-language-service-commands"></a>Intercettazione dei comandi dei servizi di linguaggio legacy
Con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è possibile fare in modo che i comandi di intercettazione del servizio di linguaggio che la visualizzazione di testo sarebbe altrimenti gestire. Ciò è utile per il comportamento specifico della lingua che la visualizzazione di testo non gestisce. È possibile intercettare questi comandi aggiungendo uno o più filtri di comando alla visualizzazione di testo dal servizio di linguaggio.

## <a name="getting-and-routing-the-command"></a>Ottenere e instradare il comando
 Un filtro di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> comando è un oggetto che monitora determinate sequenze di caratteri o comandi da tastiera. È possibile associare più di un filtro di comando a una singola visualizzazione di testo. Ogni visualizzazione di testo mantiene una catena di filtri di comando. Dopo aver creato un nuovo filtro di comando, aggiungere il filtro alla catena per la visualizzazione di testo appropriata.

 Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> su per aggiungere il filtro di comando alla catena. Quando si <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chiama , restituisce un altro filtro di comando a cui è possibile passare i comandi non gestiti dal filtro comandi.

 Sono disponibili le seguenti opzioni per la gestione dei comandi:

- Gestire il comando e quindi passare il comando al filtro di comando successivo nella catena.

- Gestire il comando e non passare il comando al filtro di comando successivo.

- Non gestire il comando, ma passare il comando al filtro di comando successivo.

- Ignorare il comando. Non gestirlo nel filtro corrente e non passarlo al filtro successivo.

  Per informazioni sui comandi che il servizio di linguaggio deve gestire, vedere Comandi importanti per i filtri del servizio di [linguaggio](../../extensibility/internals/important-commands-for-language-service-filters.md).
