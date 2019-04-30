---
title: 'Procedura: Aggiornare una pagina iniziale personalizzata | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 78342ce6-36c8-485b-a5f6-760e7a420a26
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: abe1013d37db43114f3970f12b1a0d1f08b07a4e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446456"
---
# <a name="how-to-upgrade-a-visual-studio-custom-start-page"></a>Procedura: Aggiornare una pagina iniziale personalizzata di Visual Studio
La procedura illustrata di seguito consente di aggiornare una pagina iniziale personalizzata di Visual Studio 2010 o Visual Studio 2012 a Visual Studio 2015.

> [!WARNING]
> La pagina iniziale personalizzata aggiornata in questa routine è quella creata con il modello [Custom Start Page](http://visualstudiogallery.msdn.microsoft.com/f655a5dc-1a2d-4eca-b774-76c352c03b87) disponibile in Visual Studio Gallery. La pagina iniziale dell'utente potrebbe contenere altre funzionalità che occorre aggiornare.

### <a name="to-upgrade-a-custom-start-page-to-visual-studio-2015"></a>Per aggiornare una pagina iniziale personalizzata a Visual Studio 2015

1. Verificare che Visual Studio 2015 e Visual Studio 2015 SDK siano installati. È possibile scaricare l'SDK dalla pagina di [Microsoft Visual Studio 2013 SDK](https://my.visualstudio.com/Downloads?pid=1436).

2. Aprire il progetto di modello personalizzato. Verrà visualizzato un messaggio che informare che è necessario aggiornare il progetto. Fare clic su **OK** e attendere il completamento dell'aggiornamento.

3. Nelle proprietà di progetto sia del progetto di pagina iniziale che del progetto di controllo assicurarsi che il framework di destinazione sia almeno .NET Framework 4.5.

4. Nella categoria Debug delle proprietà di progetto per il progetto di pagina iniziale impostare il percorso per la versione Visual Studio 2015 di devenv.exe.

5. Nei riferimenti al progetto di entrambi i progetti rimuovere i riferimenti a Microsoft.VisualStudio.Shell.11.0 e aggiungere riferimenti a Microsoft.VisualStudio.Shell.14.0.

6. Aprire StartPage.xaml con l'editor XML e apportare le modifiche seguenti:

    1. Aggiornare gli spazi dei nomi. Modificare le righe seguenti:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"
        ```

         in:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.142.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.14.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        ```

7. Aprire MyControl.xaml e modificare il riferimento allo spazio dei nomi `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"` in `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"` .