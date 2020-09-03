---
title: 'Procedura: installare un visualizzatore | Microsoft Docs'
ms.date: 06/10/2020
ms.topic: how-to
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
ms.openlocfilehash: b070eb361bcc3fbe4f72adfff10b5e7d19649087
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85349562"
---
# <a name="how-to-install-a-visualizer"></a>Procedura: installare un visualizzatore
Dopo avere creato un visualizzatore, è necessario installarlo in modo da renderlo disponibile in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per installare un visualizzatore è sufficiente seguire una semplice procedura.

> [!NOTE]
> Nelle app UWP sono supportati solo i visualizzatori di testo, HTML, XML e JSON standard. Non sono supportati i visualizzatori personalizzati (creati dall'utente).

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Per installare un visualizzatore per Visual Studio 2019
  
1. Individuare la DLL che contiene il Visualizzatore compilato.

   In genere, è preferibile che sia la DLL sul lato debugger che la DLL del lato oggetto del debug specifichino **qualsiasi CPU** come piattaforma di destinazione. La DLL sul lato debugger deve essere **qualsiasi CPU** o **a 32 bit**. La piattaforma di destinazione per la DLL lato oggetto del debug deve corrispondere al processo di debug.

2. Copiare la dll del [lato debugger](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (e le eventuali dll da cui dipende) in uno dei percorsi seguenti:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Copiare la dll del lato oggetto del [debug](create-custom-visualizers-of-data.md#to-create-the-visualizer-object-source-for-the-debuggee-side) in uno dei percorsi seguenti:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework* di

    - `My Documents\`*VisualStudioVersion* `\Visualizers\` *Framework* di

    dove *Framework* è uno dei seguenti:
    - `net2.0` per i debug che eseguono il `.NET Framework` Runtime.
    - `netstandard2.0` per i sottoposti a debug utilizzando un runtime che supporta `netstandard 2.0` ( `.NET Framework v4.6.1+` o `.NET Core 2.0+` ).
    - `netcoreapp` per i debug che eseguono il `.NET Core` Runtime. (supporta `.NET Core 2.0+` )

   Una DLL sul lato oggetto del debug è necessaria se si desidera creare un visualizzatore autonomo. Questa DLL contiene il codice per l'oggetto dati, che può implementare metodi di <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> .

   Se si utilizza il multitargeting del codice del lato oggetto del debug, la DLL sul lato oggetto del debug deve essere inserita nella cartella per la TFM supportata almeno.

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

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Riavviare la sessione di debug.

> [!NOTE]
> Se si desidera usare un visualizzatore gestito per il debug remoto, copiare la DLL nello stesso percorso nel computer remoto.
::: moniker-end

## <a name="see-also"></a>Vedere anche
- [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)
- [Procedura: scrivere un visualizzatore](create-custom-visualizers-of-data.md)
