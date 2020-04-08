---
title: 'Procedura: Installare un visualizzatore Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 499d644cc8374b070cedaf058b0e4dc17d155bdc
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880260"
---
# <a name="how-to-install-a-visualizer"></a>Procedura: installare un visualizzatore
Dopo avere creato un visualizzatore, è necessario installarlo in modo da renderlo disponibile in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per installare un visualizzatore è sufficiente seguire una semplice procedura.

> [!NOTE]
> Nelle app UWP sono supportati solo i visualizzatori standard di testo, HTML, XML e JSON. Non sono supportati i visualizzatori personalizzati (creati dall'utente).

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Per installare un visualizzatore per Visual Studio 2019To install a visualizer for Visual Studio 2019
  
1. Individuare la DLL che contiene il visualizzatore compilato.

   In genere, è consigliabile se sia la DLL lato debugger che la DLL sul lato oggetto del debug specificano **Qualsiasi CPU** come piattaforma di destinazione. La DLL lato debugger deve essere **Qualsiasi CPU** o **32 bit.** La piattaforma di destinazione per la DLL sul lato oggetto del debug deve corrispondere al processo oggetto del debug.

2. Copiare la DLL [lato debugger](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (e le DLL da cui dipende) in una delle seguenti posizioni:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Copiare la DLL [sul lato Debuggee](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) in una delle seguenti posizioni:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\`*Framework VisualStudioVersion* `\Visualizers\` *Framework*

    dove *Framework* è:
    - `net2.0`per i debug che `.NET Framework` eseguono il runtime.
    - `netstandard2.0`per i debug utilizzando un runtime `netstandard 2.0` `.NET Framework v4.6.1+` che `.NET Core 2.0+`supporta ( o ).
    - `netcoreapp`per i debug che `.NET Core` eseguono il runtime. (supporti `.NET Core 2.0+`)

4. Riavviare la sessione di debug.

> [!NOTE]
> La procedura è diversa in Visual Studio 2017 e versioni precedenti. Vedere la [versione precedente](how-to-install-a-visualizer.md?view=vs-2017) di questo articolo.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Per installare un visualizzatore per Visual Studio 2017 e versioni precedentiTo install a visualizer for Visual Studio 2017 and older

> [!IMPORTANT]
> Solo i visualizzatori di .NET Framework sono supportati in Visual Studio 2017 e versioni precedenti.

1. Individuare la DLL contenente il visualizzatore compilato.

2. Copiare la DLL in uno dei seguenti percorsi:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Riavviare la sessione di debug.

> [!NOTE]
> Se si desidera usare un visualizzatore gestito per il debug remoto, copiare la DLL nello stesso percorso nel computer remoto.
::: moniker-end

## <a name="see-also"></a>Vedere anche
- [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)
- [Procedura: scrivere un visualizzatore](create-custom-visualizers-of-data.md)
