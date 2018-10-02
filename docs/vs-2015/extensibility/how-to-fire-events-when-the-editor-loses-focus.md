---
title: "Procedura: generare eventi quando l'Editor perde lo stato attivo | Microsoft Docs"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2462e41470b72c63f5c96a69d2776af2a640c372
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526411"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Procedura: generare eventi quando l'Editor perde lo stato attivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: Fire eventi quando l'Editor perde lo stato attivo](https://docs.microsoft.com/visualstudio/extensibility/how-to-fire-events-when-the-editor-loses-focus).  
  
In alcuni casi è necessario sapere quando un editor perde lo stato attivo nella cornice della finestra. Ad esempio, si potrebbe essere necessario estrarre codice da una finestra del codice dopo che l'editor non è più è incentrato su di esso. La seguente procedura fornisce i passaggi da seguire per ricevere la notifica dell'editor perde lo stato attivo.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Per attivare un evento in risposta a un editor perde lo stato attivo  
  
1.  Monitorare gli eventi di selezione ottenendo un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> dall'oggetto <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> e fornire il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> oggetto.  
  
3.  Nella chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, cercare `elementid==SEID_WindowFrame`.  
  
4.  Test di `varValueNew` parametro per due motivi:  
  
    1.  La cornice della finestra che si sta cercando.  
  
    2.  Il punto in corrispondenza del quale il programma perde la selezione del frame della finestra.

