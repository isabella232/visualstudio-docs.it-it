---
title: Modello di un servizio di linguaggio legacy | Microsoft Docs
description: Usare questo modello di servizio di linguaggio minimo per l Visual Studio editor principale come guida per la creazione di un servizio di linguaggio personalizzato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3d0fd5f82e3696e2783116a6f9d35ea124e5ade8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094776"
---
# <a name="model-of-a-legacy-language-service"></a>Modello di un servizio di linguaggio legacy
Un servizio di linguaggio definisce gli elementi e le funzionalità per un linguaggio specifico e viene usato per fornire all'editor informazioni specifiche di tale linguaggio. Ad esempio, l'editor deve conoscere gli elementi e le parole chiave del linguaggio per supportare la colorazione della sintassi.

 Il servizio di linguaggio funziona a stretto contatto con il buffer di testo gestito dall'editor e con la visualizzazione che contiene l'editor. L'opzione Informazioni rapide **di** Microsoft IntelliSense è un esempio di funzionalità fornita da un servizio di linguaggio.

## <a name="a-minimal-language-service"></a>Un servizio di linguaggio minimo
 Il servizio di linguaggio di base contiene i due oggetti seguenti:

- Il *servizio di linguaggio* implementa l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> . Un servizio di linguaggio include informazioni sul linguaggio, tra cui nome, estensioni di file, gestione della finestra del codice e colorizer.

- Il *colorista implementa* l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> .

  Il disegno concettuale seguente illustra un modello di un servizio di linguaggio di base.

  ![Immagine del modello di servizio di linguaggio](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Modello di servizio di linguaggio di base

  La finestra del documento ospita *la visualizzazione documento* dell'editor, in questo caso l'editor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] principale. La visualizzazione documento e il buffer di testo sono di proprietà dell'editor. Questi oggetti funzionano tramite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] una finestra del documento specializzata denominata finestra del *codice.* La finestra del codice è contenuta in <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> un oggetto creato e controllato dall'IDE.

  Quando viene caricato un file con una determinata estensione, l'editor individua il servizio di linguaggio associato a tale estensione e vi passa la finestra del codice chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metodo . Il servizio di linguaggio restituisce un *gestore della finestra del codice* che implementa l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> .

  Nella tabella seguente viene fornita una panoramica degli oggetti nel modello.

| Componente | Oggetto | Funzione |
|------------------| - | - |
| Buffer di testo | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Flusso di testo di lettura/scrittura Unicode. È possibile che il testo usi altre codifiche. |
| Finestra del codice | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Finestra del documento che contiene una o più visualizzazioni di testo. Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è in modalità MDI (Multiple Document Interface), la finestra del codice è un elemento figlio MDI. |
| Visualizzazione Testo | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Finestra che consente all'utente di spostarsi e visualizzare il testo usando la tastiera e il mouse. Una visualizzazione di testo viene visualizzata all'utente come editor. È possibile usare le visualizzazioni testo nelle normali finestre dell'editor, nella finestra Output e nella finestra Controllo immediato. È anche possibile configurare una o più visualizzazioni di testo all'interno di una finestra del codice. |
| Gestione testo | Gestito dal <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> servizio, da cui si ottiene un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> puntatore | Componente che gestisce le informazioni comuni condivise da tutti i componenti descritti in precedenza. |
| Servizio di linguaggio | Dipendente dall'implementazione; Implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Oggetto che fornisce all'editor informazioni specifiche del linguaggio, ad esempio l'evidenziazione della sintassi, il completamento delle istruzioni e la corrispondenza delle parentesi graffe. |

## <a name="see-also"></a>Vedi anche
- [Dati documento e visualizzazione documento negli editor personalizzati](../../extensibility/document-data-and-document-view-in-custom-editors.md)
