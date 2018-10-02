---
title: Modifica delle impostazioni di visualizzazione tramite l'API Legacy | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9c6ffd7796e0f90748ed46050d5d07ce2df210db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47541016"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Modifica delle impostazioni di visualizzazione tramite l'API Legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [modifica delle impostazioni di visualizzazione tramite l'API Legacy](https://docs.microsoft.com/visualstudio/extensibility/changing-view-settings-by-using-the-legacy-api).  
  
Impostazioni per la funzionalità dell'editor principale, ad esempio a capo, margine di selezione e lo spazio virtuale, possono essere modificate dall'utente tramite il **opzioni** nella finestra di dialogo. Tuttavia, è anche possibile modificare queste impostazioni a livello di codice.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Modifica delle impostazioni tramite l'API Legacy  
 Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaccia espone un set di proprietà dell'editor di testo. La visualizzazione di testo contiene una categoria di proprietà (GUID_EditPropCategory_View_MasterSettings) che rappresenta il gruppo di impostazioni a livello di codice modificate per la visualizzazione di testo. Una volta Visualizza impostazioni sono state modificate in questo modo, non possono essere modificate nel **opzioni** nella finestra di dialogo fino a quando non vengono reimpostate.  
  
 Di seguito è il processo tipico per la modifica delle impostazioni di visualizzazione per un'istanza dell'editor principale.  
  
1.  Chiamare `QueryInterface` di (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) per il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaccia.  
  
2.  Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metodo, specificando il valore GUID_EditPropCategory_View_MasterSettings per il `rguidCategory` parametro.  
  
     Questa operazione restituisce un puntatore al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaccia, che contiene il set di proprietà forzato per la visualizzazione. In modo permanente vengono forzate le impostazioni in questo gruppo. Se un'impostazione non è presente in questo gruppo, quindi seguirà le opzioni specificate nel **opzioni** nella finestra di dialogo o i comandi dell'utente.  
  
3.  Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> metodo, specificando il valore di impostazioni appropriate nel `idprop` parametro.  
  
     Ad esempio, per forzare il ritorno a capo automatico, chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> e specificare il valore, VSEDITPROPID_ViewLangOpt_WordWrap `vt` per il `idprop` parametro. In questa chiamata `vt` è una variante di tipo VT_BOOL e `vt.boolVal` è VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>La reimpostazione delle impostazioni di visualizzazione modificato  
 Per reimpostare qualsiasi visualizzazione modificata l'impostazione per un'istanza dell'editor principale, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> metodo e specificare il valore dell'impostazione appropriata nel `idprop` parametro.  
  
 Ad esempio, per consentire l'a capo spostata liberamente, si sarebbe rimuoverlo dalla categoria della proprietà chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> e specificando il valore VSEDITPROPID_ViewLangOpt_WordWrap per il `idprop` parametro.  
  
 Per rimuovere le impostazioni di tutto questo è cambiate per l'editor principale in una sola volta, specificare il valore VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, vt per il `idprop` parametro. In questa chiamata, vt è una variante di tipo VT_BOOL e vt.boolVal è VARIANT_TRUE.  
  
## <a name="see-also"></a>Vedere anche  
 [All'interno l'Editor principale](../extensibility/inside-the-core-editor.md)   
 [L'accesso a theText visualizzazione tramite l'API Legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Finestra di dialogo Opzioni](../ide/reference/options-dialog-box-visual-studio.md)

