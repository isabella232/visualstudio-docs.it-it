---
title: Modifica delle impostazioni di visualizzazione tramite l'API Legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc0dc26a01cdddb4b26dfa65acab2c497618a76e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106488"
---
# <a name="change-view-settings-by-using-the-legacy-api"></a>Modificare le impostazioni di visualizzazione tramite l'API legacy
Impostazioni per la funzionalità dell'editor principale, ad esempio a capo, margine di selezione e lo spazio virtuale, possono essere modificate dall'utente tramite il **opzioni** nella finestra di dialogo. Tuttavia, è anche possibile modificare queste impostazioni a livello di codice.

## <a name="change-settings-by-using-the-legacy-api"></a>Modificare le impostazioni utilizzando l'API legacy
 Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaccia espone un set di proprietà dell'editor di testo. La visualizzazione di testo contiene una categoria di proprietà (GUID_EditPropCategory_View_MasterSettings) che rappresenta il gruppo di impostazioni a livello di codice modificate per la visualizzazione di testo. Una volta Visualizza impostazioni sono state modificate in questo modo, non possono essere modificate nel **opzioni** nella finestra di dialogo fino a quando non vengono reimpostate.

 Di seguito è il processo tipico per la modifica delle impostazioni di visualizzazione per un'istanza dell'editor principale.

1. Chiamare `QueryInterface` di (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) per il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaccia.

2. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metodo, specificando il valore GUID_EditPropCategory_View_MasterSettings per il `rguidCategory` parametro.

     Questa operazione restituisce un puntatore al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaccia, che contiene il set di proprietà forzato per la visualizzazione. In modo permanente vengono forzate le impostazioni in questo gruppo. Se un'impostazione non è presente in questo gruppo, quindi seguirà le opzioni specificate nel **opzioni** nella finestra di dialogo o i comandi dell'utente.

3. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> metodo, specificando il valore di impostazioni appropriate nel `idprop` parametro.

     Ad esempio, per forzare il ritorno a capo automatico, chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> e specificare il valore, VSEDITPROPID_ViewLangOpt_WordWrap `vt` per il `idprop` parametro. In questa chiamata `vt` è una variante di tipo VT_BOOL e `vt.boolVal` è VARIANT_TRUE.

## <a name="reset-changed-view-settings"></a>Reimpostazione modificato le impostazioni di visualizzazione
 Per reimpostare qualsiasi visualizzazione modificata l'impostazione per un'istanza dell'editor principale, chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> metodo e specificare il valore dell'impostazione appropriata nel `idprop` parametro.

 Ad esempio, per consentire l'a capo spostata liberamente, si sarebbe rimuoverlo dalla categoria della proprietà chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> e specificando il valore VSEDITPROPID_ViewLangOpt_WordWrap per il `idprop` parametro.

 Per rimuovere le impostazioni di tutto questo è cambiate per l'editor principale in una sola volta, specificare il valore VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, vt per il `idprop` parametro. In questa chiamata, vt è una variante di tipo VT_BOOL e vt.boolVal è VARIANT_TRUE.

## <a name="see-also"></a>Vedere anche
- [All'interno dell'editor di base](../extensibility/inside-the-core-editor.md)
- [Visualizzazione di theText accesso usando l'API legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
- [Finestra di dialogo Opzioni](../ide/reference/options-dialog-box-visual-studio.md)