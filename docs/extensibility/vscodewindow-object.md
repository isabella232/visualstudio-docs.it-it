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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 165855fc6f8e63c6c7ad84cb8432419258b7ba4e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322369"
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
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Modifica di figure](https://www.microsoft.com/download/details.aspx?id=55984)