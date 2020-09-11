---
title: Oggetto VSCodeWindowManager | Microsoft Docs
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
ms.openlocfilehash: fea97c8784402c55947c108f42f2f3153f322d9c
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012386"
---
# <a name="vscodewindowmanager-object"></a>Oggetto VSCodeWindowManager

Il servizio di linguaggio implementa gestione finestre del codice ed è responsabile della gestione delle aree di controllo (ad esempio, la barra a discesa). Per altre informazioni, vedere [personalizzazione delle finestre di codice tramite l'API legacy](../vs-2015/extensibility/customizing-code-windows-by-using-the-legacy-api.md?view=vs-2015).

Nella tabella seguente vengono illustrate le interfacce dell' `VSCodeWindowManager` oggetto.

|Interfaccia|Descrizione|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Consente l'aggiunta o la rimozione di aree di strumenti, ad esempio barre a discesa, da una finestra del codice.|