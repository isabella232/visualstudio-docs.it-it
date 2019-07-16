---
title: 'Procedura: Ospitare un Editor in un altro Editor | Microsoft Docs'
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204165"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Procedura: Ospitare un editor in un altro editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio è possibile ospitare un editor all'interno di un altro, specificando la finestra di hosting come finestra padre. A tale scopo, impostare i parametri <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> nella cornice della finestra figlio.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Per configurare la cornice della finestra per ospitare un editor  
  
1. Designare un editor come editor ospitato tramite la creazione di un riquadro della finestra figlio.  
  
     Questo riquadro si trova in cui verrà salvato il testo dell'editor.  
  
2. Creare l'editor di hosting usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> (metodo).  
  
3. Impostare il <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> delle proprietà nell'implementazione di cornice della finestra dell'editor ospitato mediante il passaggio di queste proprietà dei parametri per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> metodo, rispettivamente.  
  
     Se si vuole recuperare questi parametri, passare queste proprietà per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> (metodo).  
  
4. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodo per l'editor di contenuto.  
  
     Nel riquadro dell'editor che contiene hosted viene visualizzato l'editor.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Il **Application Designer** in Visual Studio Team Edition for Architects è riportato un esempio di una cornice della finestra dell'editor che ospita un altro editor. Il **Application Designer** ospita altre finestre di progettazione nel relativo riquadro a destra. Un pannello della finestra di progettazione (o **proprietà** pagina) per ognuna delle finestre di progettazione contenute è aggiunto alla cornice della finestra che lo contiene.
