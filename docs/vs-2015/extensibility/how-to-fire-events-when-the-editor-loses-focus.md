---
title: "Procedura: Generare gli eventi quando l'Editor perde lo stato attivo | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ebca733798636ca32787b88b8874c31a2ffffdb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050259"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Procedura: Generare gli eventi quando l'Editor perde lo stato attivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In alcuni casi è necessario sapere quando un editor perde lo stato attivo nella cornice della finestra. Ad esempio, si potrebbe essere necessario estrarre codice da una finestra del codice dopo che l'editor non è più è incentrato su di esso. La seguente procedura fornisce i passaggi da seguire per ricevere la notifica dell'editor perde lo stato attivo.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Per attivare un evento in risposta a un editor perde lo stato attivo  
  
1. Monitorare gli eventi di selezione ottenendo un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> dall'oggetto <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> e fornire il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> oggetto.  
  
3. Nella chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, cercare `elementid==SEID_WindowFrame`.  
  
4. Test di `varValueNew` parametro per due motivi:  
  
    1. La cornice della finestra che si sta cercando.  
  
    2. Il punto in corrispondenza del quale il programma perde la selezione del frame della finestra.
