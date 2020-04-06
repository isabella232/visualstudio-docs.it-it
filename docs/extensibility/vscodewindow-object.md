---
title: 'Oggetto VSCodeWindow : Documenti Microsoft'
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
ms.openlocfilehash: 55739b1ef577123ac0395b4c5cfb1e3c5dbc779f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697962"
---
# <a name="vscodewindow-object"></a>Oggetto VSCodeWindow
Una finestra del codice è una finestra di documento specializzata che può includere una o più visualizzazioni di testo, in genere l'oggetto. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>

 Dal punto di vista dell'architettura, la finestra del codice è una finestra del documento che si trova all'interno di una cornice della finestra. Funzionalmente, la finestra del codice è semplicemente una finestra del documento con funzionalità aggiuntive. In modalità interfaccia a documenti multipli (MDI), la finestra del codice è il frame figlio MDI. Per ulteriori informazioni, vedere Personalizzazione delle finestre di [codice tramite l'API legacy](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015).

 La tabella seguente include le <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> interfacce nell'oggetto.

|Metodo|Descrizione|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fornisce un meccanismo di accesso generico per individuare un servizio identificato da un identificatore univoco globale (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Rappresenta un elemento figlio MDI (Multiple Document Interface) contenente una o più visualizzazioni codice.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Riempie una cornice della finestra.|

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Modifica delle figure](https://www.microsoft.com/download/details.aspx?id=55984)
