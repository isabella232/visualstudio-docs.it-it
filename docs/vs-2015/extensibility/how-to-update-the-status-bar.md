---
title: 'Procedura: aggiornare la barra di stato | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d48b07dd5e4fc1fe745e3669041884c1b8eacd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703152"
---
# <a name="how-to-update-the-status-bar"></a>Procedura: Aggiornare la barra di stato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La **barra di stato** è una barra di controllo che si trova nella parte inferiore di molte finestre delle applicazioni che contengono uno o più indicatori o righe di testo di stato.  
  
### <a name="to-update-the-status-bar"></a>Per aggiornare la barra di stato  
  
1. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> in ogni singolo oggetto visualizzazione (DocView) fornito dall'editor, ad esempio una visualizzazione form e una visualizzazione codice.  
  
2. Quando l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> , aggiornare le informazioni nella **barra di stato** chiamando i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> .  
  
    > [!NOTE]
    > L'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> solo quando viene attivata inizialmente la finestra del documento. Per il resto del tempo in cui è attiva la finestra del documento, è necessario aggiornare le informazioni sulla **barra di stato** quando lo stato dell'editor cambia.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Una **barra di stato** contiene quattro campi distinti:  
  
- Testo Stato  
  
- Barra di stato  
  
- Icona animata  
  
- Informazioni dell'editor  
  
  Per ulteriori informazioni, vedere [barre di stato](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e).  
  
  L'IDE chiama automaticamente il <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodo dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> implementazione quando la finestra del documento è attivata.  
  
  L'implementatore VSPackage è responsabile dell'aggiornamento del testo di stato nella barra di stato. L'IDE Reimposta questa stringa su "READY" Se il campo di testo stato è impostato su testo vuoto ("") in fase di inattività.  
  
## <a name="see-also"></a>Vedere anche  
 [Barre di stato](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)
