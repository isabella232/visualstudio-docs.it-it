---
title: Intercetta comandi del servizio di linguaggio Legacy | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45f0084d060e9727f30ba39233ec5b92818d9205
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829885"
---
# <a name="intercepting-legacy-language-service-commands"></a>Intercettazione dei comandi dei servizi di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], è possibile avere language service intercetta comandi in caso contrario, è necessario gestire la visualizzazione di testo. Ciò è utile per il comportamento specifico del linguaggio che non gestisce la visualizzazione di testo. È possibile intercettare questi comandi mediante l'aggiunta di uno o più filtri di comando per la visualizzazione di testo dal servizio di linguaggio.  
  
## <a name="getting-and-routing-the-command"></a>Recupero e il Routing di comandi  
 Un filtro di comando è un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oggetto che consente di monitorare determinate sequenze di caratteri o i comandi. È possibile associare più di un filtro di comando con una visualizzazione di testo singola. Ogni visualizzazione di testo mantiene una catena di filtri di comando. Dopo aver creato un nuovo filtro di comando, si aggiunge il filtro alla catena per la visualizzazione di testo appropriato.  
  
 Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo su di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per aggiungere il filtro di comando alla catena. Quando si chiama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] restituisce un altro filtro di comando a cui è possibile passare i comandi che non consente di gestire il filtro di comando.  
  
 Sono disponibili le opzioni seguenti per la gestione dei comandi:  
  
- Gestire il comando e passare quindi il comando al filtro comando successivo nella catena.  
  
- Gestire il comando e non si passa il comando al filtro successivo comando.  
  
- Non gestire il comando, ma passare il comando al filtro successivo comando.  
  
- Ignora il comando. Non viene gestito il filtro corrente e non passarla al filtro successivo.  
  
  Per informazioni sulle quali comandi deve gestire il servizio di linguaggio, vedere [comandi importanti per i filtri dei servizi di linguaggio](../../extensibility/internals/important-commands-for-language-service-filters.md).

