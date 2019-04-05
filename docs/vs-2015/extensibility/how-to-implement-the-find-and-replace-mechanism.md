---
title: 'Procedura: Implementare la ricerca e sostituzione meccanismo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a42df69a7c51b7eb7ef44cf137d8449cf1421ae2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967658"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Procedura: Implementare la ricerca e sostituzione meccanismo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio fornisce due modalità di implementazione Trova/Sostituisci. Uno consiste nel passare un'immagine di testo alla shell e lasciare che gestiscono la ricerca, l'evidenziazione e sostituendo il testo. Ciò consente agli utenti di specificare più intervalli di testo. In alternativa, il pacchetto VSPackage può controlla questa funzionalità se stesso. In entrambi i casi è necessario inviare una notifica della shell sulla destinazione corrente e gli obiettivi per tutti i documenti aperti.  
  
### <a name="to-implement-findreplace"></a>Per implementare Trova/Sostituisci  
  
1.  Implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> interfaccia in uno degli oggetti restituiti dalle proprietà del frame <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> o <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>. Se si sta creando un editor personalizzato, è necessario implementare questa interfaccia come parte della classe dell'editor personalizzato.  
  
2.  Usare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> metodo per specificare le opzioni che l'editor supporta e indicare se implementa la ricerca di immagini di testo.  
  
     Se l'editor supporta la ricerca di immagini di testo, implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     In caso contrario, implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.  
  
3.  Se si implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> metodi, è possibile semplificare le attività di ricerca chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
