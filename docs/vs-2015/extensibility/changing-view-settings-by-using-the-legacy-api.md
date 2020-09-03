---
title: Modifica delle impostazioni di visualizzazione tramite l'API legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7d58d1477b9d7f58242f8cb4db7c3c360c248b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184471"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Modifica delle impostazioni di visualizzazione tramite l'API legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le impostazioni per le funzionalità dell'editor principale, ad esempio il ritorno a capo automatico, il margine di selezione e lo spazio virtuale, possono essere modificate dall'utente per mezzo della finestra di dialogo **Opzioni** . Tuttavia, è anche possibile modificare queste impostazioni a livello di codice.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Modifica delle impostazioni usando l'API legacy  
 L' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaccia espone un set di proprietà dell'editor di testo. La visualizzazione di testo contiene una categoria di proprietà (GUID_EditPropCategory_View_MasterSettings) che rappresenta il gruppo di impostazioni modificate a livello di codice per la visualizzazione di testo. Una volta modificate le impostazioni di visualizzazione in questo modo, non è possibile modificarle nella finestra di dialogo **Opzioni** fino a quando non vengono reimpostate.  
  
 Di seguito è riportato il processo tipico per modificare le impostazioni di visualizzazione per un'istanza dell'editor principale.  
  
1. Chiamare `QueryInterface` sul ( <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> ) per l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaccia.  
  
2. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metodo, specificando il valore GUID_EditPropCategory_View_MasterSettings per il `rguidCategory` parametro.  
  
     Questa operazione restituisce un puntatore all' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaccia che contiene il set di proprietà forzate per la visualizzazione. Tutte le impostazioni di questo gruppo vengono forzate in modo permanente. Se un'impostazione non è presente in questo gruppo, seguirà le opzioni specificate nella finestra di dialogo **Opzioni** o nei comandi dell'utente.  
  
3. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> metodo, specificando il valore delle impostazioni appropriato nel `idprop` parametro.  
  
     Ad esempio, per forzare il ritorno a capo automatico, chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> e specificare un valore di VSEDITPROPID_ViewLangOpt_WordWrap `vt` per il `idprop` parametro. In questa chiamata, `vt` è una variante di tipo VT_BOOL ed `vt.boolVal` è VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Reimpostazione delle impostazioni di visualizzazione modificate  
 Per reimpostare le impostazioni di visualizzazione modificate per un'istanza dell'editor principale, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> metodo e specificare il valore di impostazione appropriato nel `idprop` parametro.  
  
 Ad esempio, per consentire a ritorno a capo automatico di fluttuare liberamente, è necessario rimuoverlo dalla categoria di proprietà chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> e specificando il valore VSEDITPROPID_ViewLangOpt_WordWrap per il `idprop` parametro.  
  
 Per rimuovere tutte le impostazioni modificate per l'editor principale in una sola volta, specificare il valore VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, VT per il `idprop` parametro. In questa chiamata, VT è una variante di tipo VT_BOOL e VT. boolVal è VARIANT_TRUE.  
  
## <a name="see-also"></a>Vedere anche  
 [All'interno dell'editor principale](../extensibility/inside-the-core-editor.md)   
 [Accesso alla vista theText tramite l'API legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Finestra di dialogo Opzioni](../ide/reference/options-dialog-box-visual-studio.md)
