---
title: Oggetto VSCodeWindow | Microsoft Docs
description: Informazioni sulle finestre del codice, ovvero finestre di documenti specializzate che possono includere una o più visualizzazioni testo, in genere l'oggetto VsTextView.
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
ms.openlocfilehash: 7225345da6cda366a41e39be98209c1fdf12569751400a587d58bd1fc6e632e0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121413505"
---
# <a name="vscodewindow-object"></a>Oggetto VSCodeWindow
Una finestra del codice è una finestra di documento specializzata che può includere una o più visualizzazioni di testo, in genere <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> l'oggetto .

 Dal punto di vista dell'architettura, la finestra del codice è una finestra del documento all'interno di una cornice di finestra. Dal punto di vista funzionale, la finestra del codice è semplicemente una finestra del documento con funzionalità aggiuntive. Nella modalità MDI (Multiple Document Interface), la finestra del codice è il frame figlio MDI. Per altre informazioni, vedere [Personalizzazione delle finestre del codice tramite l'API legacy.](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015)

 Nella tabella seguente sono incluse le interfacce <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> nell'oggetto .

|Metodo|Descrizione|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fornisce un meccanismo di accesso generico per individuare un servizio identificato da un identificatore univoco globale (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Rappresenta un elemento figlio dell'interfaccia a documenti multipli (MDI) contenente una o più visualizzazioni codice.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Riempie una cornice di finestra.|

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Modifica delle figure](https://www.microsoft.com/download/details.aspx?id=55984)