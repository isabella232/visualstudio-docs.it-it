---
title: 'Procedura: installare un visualizzatore | Microsoft Docs'
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
ms.openlocfilehash: 2b7dfd28d70b80fd2d0f854b7db3550862b32814
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404365"
---
# <a name="how-to-install-a-visualizer"></a>Procedura: Installare un visualizzatore
Dopo avere creato un visualizzatore, è necessario installarlo in modo da renderlo disponibile in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per installare un visualizzatore è sufficiente seguire una semplice procedura.

> [!NOTE]
> Nelle app UWP sono supportati solo i visualizzatori di testo, HTML, XML e JSON standard. Non sono supportati i visualizzatori personalizzati (creati dall'utente).

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Per installare un visualizzatore per Visual Studio 2019
  
1. Individuare la DLL che contiene il Visualizzatore compilato.

2. Copiare la dll del [lato debugger](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (e le eventuali dll da cui dipende) in uno dei percorsi seguenti:

    - `\Common7\Packages\Debugger\Visualizers` *VisualStudioInstallPath*

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Copiare la dll del lato oggetto del [debug](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) in uno dei percorsi seguenti:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\` *Framework* di `\Visualizers\` *VisualStudioVersion*

    dove *Framework* è uno dei seguenti:
    - `net2.0` per i debug che eseguono il runtime di `.NET Framework`.
    - `netstandard2.0` per i debug utilizzando un runtime che supporta `netstandard 2.0` (`.NET Framework v4.6.1+` o `.NET Core 2.0+`).
    - `netcoreapp` per i debug che eseguono il runtime di `.NET Core`. (supporta `.NET Core 2.0+`)

4. Riavviare la sessione di debug.

> [!NOTE]
> La procedura è diversa in Visual Studio 2017 e versioni precedenti. Vedere la [versione precedente](how-to-install-a-visualizer.md?view=vs-2017) di questo articolo.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Per installare un visualizzatore per Visual Studio 2017 e versioni precedenti

> [!IMPORTANT]
> Solo i visualizzatori .NET Framework sono supportati in Visual Studio 2017 e versioni precedenti.

1. Individuare la DLL contenente il visualizzatore compilato.

2. Copiare la DLL in uno dei seguenti percorsi:

    - `\Common7\Packages\Debugger\Visualizers` *VisualStudioInstallPath*

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Riavviare la sessione di debug.

> [!NOTE]
> Se si desidera usare un visualizzatore gestito per il debug remoto, copiare la DLL nello stesso percorso nel computer remoto.
::: moniker-end

## <a name="see-also"></a>Vedere anche
- [Creazione di visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)
- [Procedura: Scrivere un visualizzatore](create-custom-visualizers-of-data.md)
