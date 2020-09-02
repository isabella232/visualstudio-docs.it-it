---
title: Oggetto oggetto VsCodeWindow. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 511c730ec3a11b02d46f5e9c9271c028bb4fa325
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690767"
---
# <a name="vscodewindow-object"></a>Oggetto VSCodeWindow
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una finestra del codice è una finestra di documento specializzata che può includere una o più visualizzazioni di testo, in genere l' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> oggetto.  
  
 In architettura, la finestra del codice è una finestra del documento che si trova all'interno di una cornice della finestra. Dal punto di vista funzionale, la finestra del codice è semplicemente una finestra del documento con funzionalità aggiuntive. Nella modalità interfaccia a documenti multipli (MDI) la finestra del codice è il frame figlio MDI. Per altre informazioni, vedere [personalizzazione delle finestre di codice tramite l'API legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 Nella tabella seguente sono incluse le interfacce dell' <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> oggetto.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fornisce un meccanismo di accesso generico per individuare un servizio identificato da un identificatore univoco globale (GUID).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Rappresenta un'interfaccia a documenti multipli (MDI) che contiene una o più visualizzazioni di codice.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Riempie una cornice della finestra.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Modifica figure](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
