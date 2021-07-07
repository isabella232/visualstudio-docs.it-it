---
title: Installare un visualizzatore | Microsoft Docs
description: Informazioni su come installare un visualizzatore in modo che sia disponibile per l'uso del debug in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 611347acfe48e561653d644097d56d029b6a4fa6
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298257"
---
# <a name="how-to-install-a-visualizer"></a>Procedura: installare un visualizzatore
Dopo avere creato un visualizzatore, è necessario installarlo in modo da renderlo disponibile in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per installare un visualizzatore è sufficiente seguire una semplice procedura.

> [!NOTE]
> Nelle app UWP sono supportati solo i visualizzatori di testo standard, HTML, XML e JSON. Non sono supportati i visualizzatori personalizzati (creati dall'utente).

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Per installare un visualizzatore per Visual Studio 2019

1. Individuare la DLL che contiene il visualizzatore compilato.

   In genere, è meglio se sia la DLL sul lato debugger che la DLL sul lato oggetto del debug **specificano Qualsiasi CPU** come piattaforma di destinazione. La DLL sul lato debugger deve essere **Qualsiasi CPU** o **a 32 bit.** La piattaforma di destinazione per la DLL sul lato oggetto del debug deve corrispondere al processo dell'oggetto del debug.

   >[!NOTE]
   > Il visualizzatore lato debugger viene caricato nel processo Visual Studio, quindi deve essere una DLL .NET Framework debugger. Il lato oggetto del debug può essere .NET Framework o .NET Standard a seconda del processo di cui viene Visual Studio.

2. Copiare la DLL [lato debugger](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (ed eventuali DLL da cui dipende) in uno dei percorsi seguenti:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Copiare la DLL [lato oggetto del](create-custom-visualizers-of-data.md#to-create-the-visualizer-object-source-for-the-debuggee-side) debug in uno dei percorsi seguenti:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\`*VisualStudioVersion* `\Visualizers\` *Framework*

    dove *Framework* è:
    - `net2.0` per gli oggetti di debug che eseguono il `.NET Framework` runtime.
    - `netstandard2.0` per gli oggetti di debug che usano un runtime che supporta `netstandard 2.0` ( `.NET Framework v4.6.1+` o `.NET Core 2.0+` ).
    - `netcoreapp` per gli oggetti di debug che eseguono il `.NET Core` runtime. (supporta `.NET Core 2.0+` )

   Una DLL lato oggetto del debug è necessaria se si vuole creare un visualizzatore autonomo. Questa DLL contiene il codice per l'oggetto dati, che può implementare metodi di <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> .

   Se si ha più destinazione del codice sul lato oggetto del debug, la DLL sul lato oggetto del debug deve essere inserita nella cartella per TFM con supporto minimo.

4. Riavviare la sessione di debug.

> [!NOTE]
> La procedura è diversa in Visual Studio 2017 e versioni precedenti. Vedere la [versione precedente](how-to-install-a-visualizer.md?view=vs-2017&preserve-view=true) di questo articolo.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Per installare un visualizzatore per Visual Studio 2017 e versioni precedenti

> [!IMPORTANT]
> Solo .NET Framework visualizzatori sono supportati in Visual Studio 2017 e versioni precedenti.

1. Individuare la DLL contenente il visualizzatore compilato.

2. Copiare la DLL in uno dei seguenti percorsi:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Riavviare la sessione di debug.

> [!NOTE]
> Se si desidera usare un visualizzatore gestito per il debug remoto, copiare la DLL nello stesso percorso nel computer remoto.
::: moniker-end

## <a name="see-also"></a>Vedi anche
- [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)
- [Procedura: scrivere un visualizzatore](create-custom-visualizers-of-data.md)
