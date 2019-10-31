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
ms.openlocfilehash: 494287c6691d27eb636f92eff324eecf49daf5fa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187585"
---
# <a name="how-to-install-a-visualizer"></a>Procedura: installare un visualizzatore
Dopo avere creato un visualizzatore, è necessario installarlo in modo da renderlo disponibile in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per installare un visualizzatore è sufficiente seguire una semplice procedura.

> [!NOTE]
> Nelle app UWP sono supportati solo i visualizzatori di testo, HTML, XML e JSON standard. Non sono supportati i visualizzatori personalizzati (creati dall'utente).

### <a name="to-install-a-visualizer"></a>Per installare un visualizzatore

1. Individuare la DLL contenente il visualizzatore compilato.

2. Copiare la DLL in uno dei seguenti percorsi:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Se si desidera usare un visualizzatore gestito per il debug remoto, copiare la DLL nello stesso percorso nel computer remoto.

4. Riavviare la sessione di debug.

## <a name="see-also"></a>Vedere anche
- [Creazione di visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)
- [Procedura: Scrivere un visualizzatore](create-custom-visualizers-of-data.md)