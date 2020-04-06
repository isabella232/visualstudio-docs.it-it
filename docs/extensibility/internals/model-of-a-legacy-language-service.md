---
title: Modello di un servizio di linguaggio Legacy Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f024a02641902843f673ce3ff8583a4bce3b135
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707041"
---
# <a name="model-of-a-legacy-language-service"></a>Modello di un servizio di linguaggio legacy
Un servizio di linguaggio definisce gli elementi e le funzionalità per un linguaggio specifico e viene utilizzato per fornire all'editor informazioni specifiche per tale linguaggio. Ad esempio, l'editor deve conoscere gli elementi e le parole chiave del linguaggio per supportare la colorazione della sintassi.

 Il servizio di linguaggio funziona a stretto contatto con il buffer di testo gestito dall'editor e la visualizzazione che contiene l'editor. L'opzione **Informazioni rapide** di Microsoft IntelliSense è un esempio di funzionalità fornita da un servizio di linguaggio.

## <a name="a-minimal-language-service"></a>Un servizio di linguaggio minimo
 Il servizio di linguaggio di base contiene i due oggetti seguenti:The most basic language service contains the following two objects:

- Il servizio di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> *linguaggio* implementa l'interfaccia. Un servizio di linguaggio contiene informazioni sulla lingua, inclusi il nome, le estensioni di file, il gestore della finestra del codice e il colorizer.

- Il *colorizer* <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> implementa l'interfaccia.

  Il disegno concettuale seguente mostra un modello di un servizio di linguaggio di base.

  ![Rappresentazione grafica del modello di servizio di linguaggio](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel (modello)") Modello di servizio linguistico di baseBasic language service model

  La finestra del documento ospita la *visualizzazione* del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] documento dell'editor, in questo caso l'editor principale. La visualizzazione del documento e il buffer di testo sono di proprietà dell'editor. Questi oggetti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funzionano con una finestra di documento specializzata denominata *finestra del codice*. La finestra del codice <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> è contenuta in un oggetto creato e controllato dall'IDE.

  Quando viene caricato un file con una determinata estensione, l'editor individua il servizio di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> linguaggio associato a tale estensione e gli passa la finestra del codice chiamando il metodo . Il servizio di linguaggio restituisce <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> un *gestore della finestra*del codice , che implementa l'interfaccia .

  Nella tabella seguente viene fornita una panoramica degli oggetti nel modello.

| Componente | Oggetto | Funzione |
|------------------| - | - |
| Buffer di testo | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Flusso di testo di lettura/scrittura Unicode.A Unicode read/write text stream. È possibile che il testo utilizzi altre codifiche. |
| Finestra del codice | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Finestra del documento che contiene una o più visualizzazioni di testo. Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è in modalità interfaccia a documenti multipli (MDI), la finestra del codice è un figlio MDI. |
| Visualizzazione testo | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Finestra che consente all'utente di spostarsi e visualizzare il testo utilizzando la tastiera e il mouse. Una visualizzazione di testo viene visualizzata all'utente come un editor. È possibile utilizzare le visualizzazioni di testo nelle normali finestre dell'editor, nella finestra Output e nella finestra immediata. Inoltre, è possibile configurare una o più visualizzazioni di testo all'interno di una finestra del codice. |
| Gestore di testo | Gestito dal <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> servizio, da cui <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> si ottiene un puntatore | Componente che gestisce le informazioni comuni condivise da tutti i componenti descritti in precedenza. |
| Servizio linguistico | Dipendente dall'implementazione; Implementa<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Oggetto che fornisce all'editor informazioni specifiche del linguaggio, ad esempio l'evidenziazione della sintassi, il completamento delle istruzioni e la corrispondenza tra parentesi graffe. |

## <a name="see-also"></a>Vedere anche
- [Dati documento e visualizzazione documento negli editor personalizzati](../../extensibility/document-data-and-document-view-in-custom-editors.md)
