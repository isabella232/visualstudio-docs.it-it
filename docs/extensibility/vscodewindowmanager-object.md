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
ms.openlocfilehash: e88885d339e55b7c3df1312b4a72c59d2959bbcc
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414345"
---
# <a name="vscodewindowmanager-object"></a>Oggetto VSCodeWindowManager

Il servizio di linguaggio implementa gestione finestre del codice ed è responsabile della gestione delle aree di controllo (ad esempio, la barra a discesa). Per altre informazioni, vedere [personalizzazione delle finestre di codice tramite l'API legacy](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

Nella tabella seguente vengono illustrate le interfacce dell' `VSCodeWindowManager` oggetto.

|Interfaccia|Descrizione|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Consente l'aggiunta o la rimozione di aree di strumenti, ad esempio barre a discesa, da una finestra del codice.|