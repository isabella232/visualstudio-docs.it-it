---
title: Oggetto VSCodeWindow | Microsoft Docs
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
ms.openlocfilehash: 1711b1409e42d431ad34badf82cff68e5a9bad75
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966837"
---
# <a name="vscodewindow-object"></a>Oggetto VSCodeWindow
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una finestra del codice è una finestra del documento specializzata che può includere uno o più visualizzazioni di testo, in genere il <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> oggetto.  
  
 A livello di architettura, la finestra del codice è una finestra del documento che si trova all'interno di una cornice di finestra. A livello funzionale, la finestra del codice è semplicemente una finestra del documento con funzionalità aggiuntive. Nella modalità interfaccia a documenti multipli (MDI), la finestra del codice è la cornice figlio MDI. Per altre informazioni, vedere [personalizzazione di Windows di codice usando l'API Legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 La tabella seguente include le interfacce di <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> oggetto.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fornisce un meccanismo di accesso generici per individuare un servizio che identifica un identificatore univoco globale (GUID).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Rappresenta un elemento figlio MDI (interfaccia) di documento più contenente una o più visualizzazioni codice.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Riempie una cornice di finestra.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Modifica di figure](http://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
