---
title: 'Procedura: Aggiornare la barra di stato | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f1ba62fc5147eb679e6d6a64685b367aafacae4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324786"
---
# <a name="how-to-update-the-status-bar"></a>Procedura: Aggiornare la barra di stato
Il **sulla barra di stato** una barra di controllo si trova nella parte inferiore di molte finestre dell'applicazione che contiene uno o più righe di testo di stato o indicatori.

## <a name="to-update-the-status-bar"></a>Per aggiornare la barra di stato

1. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> su ogni oggetto di visualizzazione (DocView) che fornisce un editor, ad esempio una visualizzazione form e una visualizzazione del codice.

2. Quando l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, aggiornare le informazioni contenute nel **sulla barra di stato** chiamando i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.

    > [!NOTE]
    > Le chiamate IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> solo quando la finestra del documento viene inizialmente attivata. Nella parte restante del tempo che la finestra del documento è attiva, è necessario aggiornare il **sulla barra di stato** informazioni come lo stato delle modifiche dell'editor.

## <a name="robust-programming"></a>Programmazione efficiente
 Oggetto **sulla barra di stato** contiene quattro campi separati:

- Testo stato

- Indicatore di stato

- Icona animata

- Informazioni relative all'editor

  Per altre informazioni, vedere [barre di stato](/cpp/mfc/status-bars).

  Chiama automaticamente l'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodo del <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> implementazione quando viene attivata la finestra del documento.

  Il responsabile dell'implementazione di VSPackage è responsabile dell'aggiornamento del testo di stato nella barra di stato. L'IDE Reimposta questa stringa per "Pronto" se il campo di testo di stato è impostato su text vuota ("") in fase di inattività.

## <a name="see-also"></a>Vedere anche
- [Barre di stato](/cpp/mfc/status-bars)