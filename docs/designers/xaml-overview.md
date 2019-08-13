---
title: Panoramica di XAML
ms.date: 07/31/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a9b04012e2f0b046b3fd31058c9838740e833281
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2019
ms.locfileid: "68823917"
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