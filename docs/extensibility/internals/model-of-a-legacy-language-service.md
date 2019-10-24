---
title: Modello di un servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b87106060d3fd66b3659f5d49159ebbb9be9ef6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726383"
---
# <a name="model-of-a-legacy-language-service"></a>Modello di un servizio di linguaggio legacy
Un servizio di linguaggio definisce gli elementi e le funzionalità per una lingua specifica e viene usato per fornire all'editor le informazioni specifiche di tale lingua. È ad esempio necessario che l'editor conosca gli elementi e le parole chiave del linguaggio per supportare la colorazione della sintassi.

 Il servizio di linguaggio opera a stretto contatto con il buffer di testo gestito dall'editor e con la visualizzazione che contiene l'editor. L'opzione Microsoft IntelliSense **Quick Info** è un esempio di funzionalità fornita da un servizio di linguaggio.

## <a name="a-minimal-language-service"></a>Un servizio di linguaggio minimo
 Il servizio di linguaggio più semplice contiene i due oggetti seguenti:

- Il *servizio di linguaggio* implementa l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>. Un servizio di linguaggio dispone di informazioni sulla lingua, tra cui il nome, le estensioni di file, il gestore della finestra del codice e il colorante.

- Il *coloratore* implementa l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.

  Il disegno concettuale seguente mostra un modello di servizio di linguaggio di base.

  ![Rappresentazione grafica del modello del servizio di linguaggio](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Modello di servizio del linguaggio di base

  La finestra del documento ospita la *visualizzazione documento* dell'editor, in questo caso l'editor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] core. La visualizzazione del documento e il buffer di testo sono di proprietà dell'editor. Questi oggetti funzionano con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tramite una finestra di documento specializzata denominata *finestra del codice*. La finestra del codice è contenuta in un oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> creato e controllato dall'IDE.

  Quando viene caricato un file con una determinata estensione, l'editor individua il servizio di linguaggio associato all'estensione e lo passa alla finestra del codice chiamando il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>. Il servizio di linguaggio restituisce una *Gestione finestre di codice*che implementa l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>.

  Nella tabella seguente viene fornita una panoramica degli oggetti nel modello.

| Componente | Oggetto | Funzione |
|------------------| - | - |
| Buffer di testo | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Flusso di testo in lettura/scrittura Unicode. È possibile che il testo usi altre codifiche. |
| Finestra del codice | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Finestra del documento che contiene una o più visualizzazioni di testo. Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è in modalità interfaccia a documenti multipli (MDI), la finestra del codice è un elemento figlio MDI. |
| Visualizzazione testo | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Finestra che consente all'utente di spostarsi e visualizzare il testo utilizzando la tastiera e il mouse. Una visualizzazione di testo viene visualizzata all'utente come editor. È possibile utilizzare le visualizzazioni di testo nelle finestre dell'editor normali, nella finestra di output e nella finestra di controllo immediato. Inoltre, è possibile configurare una o più visualizzazioni di testo all'interno di una finestra del codice. |
| Gestione testo | Gestito dal servizio <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>, da cui si ottiene un puntatore <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> | Componente che mantiene le informazioni comuni condivise da tutti i componenti descritti in precedenza. |
| Servizio di linguaggio | Dipendente dall'implementazione; implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Oggetto che fornisce all'editor le informazioni specifiche della lingua, ad esempio l'evidenziazione della sintassi, il completamento delle istruzioni e la corrispondenza delle parentesi graffe. |

## <a name="see-also"></a>Vedere anche
- [Dati documento e visualizzazione documento negli editor personalizzati](../../extensibility/document-data-and-document-view-in-custom-editors.md)