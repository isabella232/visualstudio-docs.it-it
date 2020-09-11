---
title: Oggetto oggetto VsCodeWindow. | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d319dfd0f44646f911a01a157a92fc2e5596e492
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012399"
---
# <a name="vscodewindow-object"></a>Oggetto oggetto VsCodeWindow.
Una finestra del codice è una finestra di documento specializzata che può includere una o più visualizzazioni di testo, in genere l' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> oggetto.

 In architettura, la finestra del codice è una finestra del documento che si trova all'interno di una cornice della finestra. Dal punto di vista funzionale, la finestra del codice è semplicemente una finestra del documento con funzionalità aggiuntive. Nella modalità interfaccia a documenti multipli (MDI) la finestra del codice è il frame figlio MDI. Per altre informazioni, vedere [personalizzazione delle finestre di codice tramite l'API legacy](../vs-2015/extensibility/customizing-code-windows-by-using-the-legacy-api.md?view=vs-2015).

 Nella tabella seguente sono incluse le interfacce dell' <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> oggetto.

|Metodo|Descrizione|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fornisce un meccanismo di accesso generico per individuare un servizio identificato da un identificatore univoco globale (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Rappresenta un'interfaccia a documenti multipli (MDI) che contiene una o più visualizzazioni di codice.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Riempie una cornice della finestra.|

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Modifica figure](https://www.microsoft.com/download/details.aspx?id=55984)