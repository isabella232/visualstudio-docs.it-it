---
title: Oggetto VSCodeWindow | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e674077ba3b26ea4b0cbc3bf19e2f526e381f72d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959788"
---
# <a name="vscodewindow-object"></a>Oggetto VSCodeWindow
Una finestra del codice è una finestra del documento specializzata che può includere uno o più visualizzazioni di testo, in genere il <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> oggetto.  
  
 A livello di architettura, la finestra del codice è una finestra del documento che si trova all'interno di una cornice di finestra. A livello funzionale, la finestra del codice è semplicemente una finestra del documento con funzionalità aggiuntive. Nella modalità interfaccia a documenti multipli (MDI), la finestra del codice è la cornice figlio MDI. Per altre informazioni, vedere [personalizzazione delle finestre del codice tramite l'API legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 La tabella seguente include le interfacce di <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> oggetto.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fornisce un meccanismo di accesso generici per individuare un servizio che identifica un identificatore univoco globale (GUID).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Rappresenta un elemento figlio MDI (interfaccia) di documento più contenente una o più visualizzazioni codice.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Riempie una cornice di finestra.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Modifica di figure](https://www.microsoft.com/download/details.aspx?id=55984)