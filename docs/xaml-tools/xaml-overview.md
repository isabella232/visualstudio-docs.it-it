---
title: Panoramica di XAML
ms.date: 07/31/2019
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: af6ef98c5bffc4563cfa8fc8e0b29a910aeb85e8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601872"
---
# <a name="overview-of-xaml"></a>Panoramica di XAML

XAML (Extensible Application Markup Language) è un linguaggio dichiarativo basato su XML. Viene ampiamente usato nei tipi di applicazioni seguenti per creare interfacce utente:

- [App WPF (Windows Presentation Foundation)](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [App UWP (Universal Windows Platform)](/windows/uwp/xaml-platform/xaml-overview)
- [App Xamarin.Forms](/xamarin/xamarin-forms/xaml/)

Il codice XAML seguente definisce un semplice pulsante.

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

XAML viene inoltre usato per definire i flussi di lavoro nelle [app WF (Windows WorkFlow Foundation)](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml).

## <a name="xaml-designer"></a>XAML Designer

Visual Studio e Blend per Visual Studio forniscono una finestra di progettazione XAML che consente di creare interfacce utente per le app WPF, UWP e Xamarin.Forms. È possibile trascinare i controlli dalla casella degli strumenti o dalla finestra Asset e impostare le proprietà nella finestra Proprietà. Quando si eseguono queste azioni, Visual Studio e Blend per Visual Studio creano il codice XAML corrispondente. Se si preferisce, è anche possibile modificare il codice XAML direttamente.

Gli articoli di questo set di documentazione illustrano le finestra di progettazione XAML in Visual Studio e Blend per Visual Studio.

## <a name="see-also"></a>Vedere anche

- [XAML in all WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML in all UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML in app Xamarin.Forms](/xamarin/xamarin-forms/xaml/)