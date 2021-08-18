---
title: Panoramica di XAML
description: Informazioni di base su XAML e sull'editor di codice XAML e finestra di progettazione XAML strumenti in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/23/2020
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: c2bdb5fad308bfcb1f4ec843b88baa937ca77e3c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045606"
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

## <a name="xaml-code-editor"></a>Editor di codice XAML

[L'editor di](xaml-code-editor.md) codice XAML nell'IDE di Visual Studio include tutti gli strumenti necessari per creare app WPF e UWP per la piattaforma Windows e per Xamarin.Forms. Sebbene l'IDE (ambiente di sviluppo integrato) in Visual Studio abbia molte funzionalità che è possibile usare per sviluppare app per altre piattaforme, include anche alcune funzionalità specifiche di XAML.

## <a name="xaml-designer"></a>XAML Designer

Visual Studio e Blend per Visual Studio un [finestra di progettazione XAML](creating-a-ui-by-using-xaml-designer-in-visual-studio.md) che consente di creare interfacce utente per le app WPF, UWP e Xamarin.Forms. È possibile trascinare i controlli dalla casella degli strumenti o dalla finestra Asset e impostare le proprietà nella finestra Proprietà. In questo caso, Visual Studio e Blend per Visual Studio il codice XAML corrispondente. Se si preferisce, è anche possibile modificare il codice XAML direttamente.

## <a name="whats-new"></a>Novità

Per le informazioni più recenti, vedere le risorse seguenti:

- Post di blog **[Improvements to XAML tooling in Visual Studio 2019 version 16.7 Preview 1 (Miglioramenti agli strumenti XAML in Visual Studio 2019 versione 16.7 Preview 1)](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/)**
- Post di blog **[What's new in XAML developer tools in Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/)** (Novità degli strumenti di sviluppo XAML in Visual Studio 2019)
- Nuove **[funzionalità XAML in Visual Studio](https://youtu.be/yI9OyA4ZM2E)** video su YouTube

## <a name="see-also"></a>Vedi anche

- [XAML in all WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML in all UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML in app Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
