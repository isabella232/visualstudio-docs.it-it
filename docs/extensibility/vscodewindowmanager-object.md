---
title: Oggetto VSCodeWindowManager | Microsoft Docs
description: Informazioni sull'oggetto VSCodeWindowManager, responsabile della gestione delle aree di controllo, ad esempio la barra a discesa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a5c602a1cf46382e5a8b5c688501b2406e4a6d0
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863993"
---
# <a name="vscodewindowmanager-object"></a>Oggetto VSCodeWindowManager

Il servizio di linguaggio implementa gestione finestre del codice ed è responsabile della gestione delle aree di controllo (ad esempio, la barra a discesa). Per altre informazioni, vedere [personalizzazione delle finestre di codice tramite l'API legacy](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

Nella tabella seguente vengono illustrate le interfacce dell' `VSCodeWindowManager` oggetto.

|Interfaccia|Descrizione|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Consente l'aggiunta o la rimozione di aree di strumenti, ad esempio barre a discesa, da una finestra del codice.|