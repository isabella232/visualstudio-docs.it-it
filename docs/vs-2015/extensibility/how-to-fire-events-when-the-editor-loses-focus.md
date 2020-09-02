---
title: "Procedura: generare eventi quando l'editor perde lo stato attivo | Microsoft Docs"
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204198"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Procedura: Generare eventi quando l'editor perde lo stato attivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Talvolta è necessario stabilire quando un editor perde lo stato attivo sulla cornice della finestra. Ad esempio, potrebbe essere necessario estrarre il codice da una finestra del codice dopo che l'editor non è più incentrato su di esso. Nella procedura riportata di seguito vengono illustrati i passaggi da seguire per ricevere la notifica dell'editor che perde lo stato attivo.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Per generare un evento in risposta a un editor che perde lo stato attivo  
  
1. Consente di monitorare gli eventi di selezione ottenendo un <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> oggetto da <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> .  
  
2. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> e fornire il proprio <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> oggetto.  
  
3. Nella chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> cercare `elementid==SEID_WindowFrame` .  
  
4. Testare il `varValueNew` parametro per due elementi:  
  
    1. La cornice della finestra che si sta cercando.  
  
    2. Punto in cui il programma perde la selezione nel frame della finestra.
