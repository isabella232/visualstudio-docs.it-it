---
title: Menu di scelta rapida | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5534d0895e35e252364b491858a694a1f5b726a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341726"
---
# <a name="context-menus"></a>Menu di scelta rapida
Menu di scelta rapida vengono visualizzati quando un utente fa clic in un'area attiva dell'area client e cancellare quando viene rilasciato il pulsante destro del mouse.

## <a name="editor-context-menus"></a>Menu di scelta rapida editor
 Mediante l'intercettazione `ECMD_SHOWCONTEXTMENU`, il servizio di linguaggio può controllare il menu di scelta rapida verrà visualizzato nell'editor. Per visualizzare il proprio menu di scelta rapida, la gestione di questo comando quando viene passato il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Se non si gestisce questo comando, l'IDE visualizza un menu di scelta rapida standard fornito per l'editor. È inoltre possibile controllare il contenuto del menu di scelta rapida in base al marcatore. Per altre informazioni, vedere [usare i marcatori di testo con l'API legacy](../extensibility/using-text-markers-with-the-legacy-api.md) e [intercettare i comandi del servizio di linguaggio legacy](../extensibility/internals/intercepting-legacy-language-service-commands.md).

## <a name="see-also"></a>Vedere anche
- [Sviluppare un servizio di linguaggio legacy](../extensibility/internals/developing-a-legacy-language-service.md)
- [Estendere i menu e comandi](../extensibility/extending-menus-and-commands.md)