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
ms.openlocfilehash: 3c9c2fa8a8fb300c3b7eb702ae3efd216e17141a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733100"
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
- [Procedura: Scrivere un visualizzatore](/visualstudio/debugger/create-custom-visualizers-of-data)