---
title: Menu di scelta rapida | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9baab8ef64fa1952eff138165f608e25960c8cfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184273"
---
# <a name="context-menus"></a>Menu di scelta rapida
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I menu di scelta rapida vengono visualizzati quando un utente fa clic con il pulsante destro del mouse in un'area attiva dell'area client e cancella quando viene rilasciato il pulsante destro del mouse.  
  
## <a name="editor-context-menus"></a>Editor - Menu di scelta rapida  
 Tramite l'intercettazione `ECMD_SHOWCONTEXTMENU` , il servizio di linguaggio può controllare i menu di scelta rapida che vengono visualizzati nell'editor. Per visualizzare un menu di scelta rapida personalizzato, gestire questo comando quando viene passato al chiamando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> . Se non si gestisce questo comando, l'IDE Visualizza un menu di scelta rapida standard fornito per l'editor. È anche possibile controllare il contenuto del menu di scelta rapida in base al marcatore. Per altre informazioni, vedere uso di [marcatori di testo con l'API legacy](../extensibility/using-text-markers-with-the-legacy-api.md) e [intercettazione dei comandi del servizio di linguaggio legacy](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un servizio di linguaggio legacy](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)
