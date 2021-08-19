---
title: Oggetto VSCodeWindow | Microsoft Docs
description: Informazioni sulle finestre di codice, ovvero finestre di documento specializzate che possono includere una o più visualizzazioni di testo, in genere l'oggetto VsTextView.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d9ce7cdc11fe44f2148f2c268e1cab554da6bffd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049220"
---
# <a name="vscodewindow-object"></a>Oggetto VSCodeWindow
Una finestra del codice è una finestra di documento specializzata che può includere una o più visualizzazioni di testo, in genere <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> l'oggetto .

 Dal punto di vista dell'architettura, la finestra del codice è una finestra del documento all'interno di una cornice di finestra. Dal punto di vista funzionale, la finestra del codice è semplicemente una finestra del documento con funzionalità aggiuntive. Nella modalità MDI (Multiple Document Interface) la finestra del codice è il frame figlio MDI. Per altre informazioni, vedere [Personalizzazione delle finestre del codice tramite l'API legacy](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

 La tabella seguente include le interfacce <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> nell'oggetto .

|Metodo|Descrizione|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fornisce un meccanismo di accesso generico per individuare un servizio identificato da un GUID (Globally Unique Identifier).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Rappresenta un elemento figlio MDI (Multiple Document Interface) contenente una o più visualizzazioni codice.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Riempie una cornice della finestra.|

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Modifica delle figure](https://www.microsoft.com/download/details.aspx?id=55984)