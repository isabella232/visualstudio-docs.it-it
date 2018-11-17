---
title: Menu di scelta rapida | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: efd4e1c80b9af2a0d73730f0bd7d741cd877fb07
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796844"
---
# <a name="context-menus"></a>Menu di scelta rapida
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Menu di scelta rapida vengono visualizzati quando un utente fa clic in un'area attiva dell'area client e cancellare quando viene rilasciato il pulsante destro del mouse.  
  
## <a name="editor-context-menus"></a>Editor - Menu di scelta rapida  
 Mediante l'intercettazione `ECMD_SHOWCONTEXTMENU`, il servizio di linguaggio può controllare il menu di scelta rapida verrà visualizzato nell'editor. Per visualizzare il proprio menu di scelta rapida, la gestione di questo comando quando viene passato il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Se non si gestisce questo comando, l'IDE visualizza un menu di scelta rapida standard fornito per l'editor. È inoltre possibile controllare il contenuto del menu di scelta rapida in base al marcatore. Per altre informazioni, vedere [usando i marcatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md) e [intercetta comandi del servizio di linguaggio Legacy](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un servizio di linguaggio Legacy](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)

