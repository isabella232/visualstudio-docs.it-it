---
title: Panoramica di XAML
ms.date: 06/23/2020
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e14e23f9820301374bd435484ba784edf50294bb
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331950"
---
# <a name="overview-of-xaml"></a>Panoramica di XAML

XAML (Extensible Application Markup Language) è un linguaggio dichiarativo basato su XML. Viene ampiamente usato nei tipi di applicazioni seguenti per creare interfacce utente:

- [App WPF (Windows Presentation Foundation)](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [App piattaforma UWP (Universal Windows Platform) (UWP)](/windows/uwp/xaml-platform/xaml-overview)
- [App Xamarin.Forms](/xamarin/xamarin-forms/xaml/)

Il codice XAML seguente definisce un semplice pulsante.

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

XAML viene inoltre usato per definire i flussi di lavoro nelle [app WF (Windows WorkFlow Foundation)](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml).

## <a name="xaml-code-editor"></a>Editor di codice XAML

L' [editor di codice XAML](xaml-code-editor.md) nell'IDE di Visual Studio include tutti gli strumenti necessari per creare app WPF e UWP per la piattaforma Windows e per Novell. Forms. Sebbene l'IDE (Integrated Development Environment) in Visual Studio includa numerose funzionalità che è possibile usare per sviluppare app per altre piattaforme, dispone anche di alcune funzionalità univoche per XAML.

## <a name="xaml-designer"></a>XAML Designer

Visual Studio e Blend per Visual Studio forniscono una [finestra di progettazione XAML](creating-a-ui-by-using-xaml-designer-in-visual-studio.md) che consente di creare interfacce utente (UI) per le app WPF, UWP e Novell. Forms. È possibile trascinare i controlli dalla casella degli strumenti o dalla finestra Asset e impostare le proprietà nella finestra Proprietà. Quando si esegue questa operazione, Visual Studio e Blend per Visual Studio creano il codice XAML corrispondente. Se si preferisce, è anche possibile modificare il codice XAML direttamente.

## <a name="whats-new"></a>Novità

Per informazioni aggiornate, fare riferimento alle risorse seguenti:

- Il post di Blog relativo ai miglioramenti apportati **[agli strumenti XAML in Visual Studio 2019 versione 16,7 Preview 1](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/)**
- Post **[di Blog sulle novità di strumenti di sviluppo XAML in Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/)**
- **[Nuove funzionalità XAML nel video di Visual Studio](https://youtu.be/yI9OyA4ZM2E)** su YouTube

## <a name="see-also"></a>Vedi anche

- [XAML in all WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML in all UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML in app Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
