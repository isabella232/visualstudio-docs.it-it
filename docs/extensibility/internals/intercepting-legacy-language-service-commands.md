---
title: Intercettazione dei comandi legacy del servizio di linguaggio | Microsoft Docs
description: Informazioni su come usare i filtri comandi in Visual Studio intercettare i comandi del servizio di linguaggio legacy e aggiungere un comportamento specifico del linguaggio.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6f82e3cb15b39359c78f28a42e62d65665f34dba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049961"
---
# <a name="intercepting-legacy-language-service-commands"></a>Intercettazione dei comandi dei servizi di linguaggio legacy
Con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , è possibile fare in modo che il servizio di linguaggio intercetti i comandi che altrimenti verrebbero gestiti dalla visualizzazione testo. Ciò è utile per il comportamento specifico della lingua che la visualizzazione testo non gestisce. È possibile intercettare questi comandi aggiungendo uno o più filtri di comando alla visualizzazione testo dal servizio di linguaggio.

## <a name="getting-and-routing-the-command"></a>Recupero e routing del comando
 Un filtro comandi è un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oggetto che monitora determinate sequenze di caratteri o comandi chiave. È possibile associare più di un filtro comandi a una singola visualizzazione di testo. Ogni visualizzazione di testo mantiene una catena di filtri di comando. Dopo aver creato un nuovo filtro comandi, aggiungere il filtro alla catena per la visualizzazione di testo appropriata.

 Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo su per aggiungere il filtro di comando alla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> catena. Quando si chiama , restituisce un altro filtro di comando a cui è possibile passare i comandi non gestiti dal filtro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comandi.

 Per la gestione dei comandi sono disponibili le opzioni seguenti:

- Gestire il comando e quindi passare il comando al filtro di comando successivo nella catena.

- Gestire il comando e non passare il comando al filtro di comando successivo.

- Non gestire il comando, ma passare il comando al filtro di comando successivo.

- Ignorare il comando . Non gestirlo nel filtro corrente e non passarlo al filtro successivo.

  Per informazioni sui comandi che il servizio di linguaggio deve gestire, vedere [Comandi importanti per i filtri del servizio di linguaggio.](../../extensibility/internals/important-commands-for-language-service-filters.md)
