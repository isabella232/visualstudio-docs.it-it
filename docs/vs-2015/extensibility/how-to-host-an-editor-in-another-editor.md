---
title: 'Procedura: ospitare un editor in un altro editor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d4b4ff425feb22b5057a8d1a76b7f73b8932d9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204165"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Procedura: Ospitare un editor in un altro editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio è possibile ospitare un editor all'interno di un'altra specificando la finestra di hosting come finestra padre. A tale scopo, impostare i parametri <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> sulla cornice della finestra figlio.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Per configurare la cornice della finestra per ospitare un editor  
  
1. Designare un editor come editor ospitato creando un riquadro della finestra figlio.  
  
     Questo riquadro è il punto in cui verrà inserito il testo dell'editor.  
  
2. Creare l'editor di hosting usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> metodo o.  
  
3. Impostare le <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> proprietà e nell'implementazione della cornice della finestra dell'editor ospitato passando tali proprietà rispettivamente come parametri al <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> metodo.  
  
     Se è necessario recuperare questi parametri, passare queste proprietà al <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodo.  
  
4. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodo per l'Editor contenuto.  
  
     L'editor viene visualizzato nel riquadro ospitato dell'editor che lo contiene.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Il **Progettazione applicazioni** in Visual Studio Team Edition for Architects è un esempio di frame della finestra Editor che ospita un altro editor. Il **Progettazione applicazioni** ospita altre finestre di progettazione nel riquadro di destra. Un pannello della finestra di progettazione (o una pagina delle **Proprietà** ) per ogni finestra di progettazione contenuta viene aggiunto al frame della finestra contenitore.
