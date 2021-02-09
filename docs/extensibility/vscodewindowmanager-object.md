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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e353070c780f69ea05c1c67986f7a40f34d0659c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925850"
---
# <a name="vscodewindowmanager-object"></a>Oggetto VSCodeWindowManager

Il servizio di linguaggio implementa gestione finestre del codice ed è responsabile della gestione delle aree di controllo (ad esempio, la barra a discesa). Per altre informazioni, vedere [personalizzazione delle finestre di codice tramite l'API legacy](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

Nella tabella seguente vengono illustrate le interfacce dell' `VSCodeWindowManager` oggetto.

|Interfaccia|Descrizione|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Consente l'aggiunta o la rimozione di aree di strumenti, ad esempio barre a discesa, da una finestra del codice.|