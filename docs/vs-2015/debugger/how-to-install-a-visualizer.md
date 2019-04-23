---
title: 'Procedura: Installare un visualizzatore | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e223831b30f784094a2affa5cebb314cc6e997f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059708"
---
# <a name="how-to-install-a-visualizer"></a>Procedura: Installare un visualizzatore
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dopo avere creato un visualizzatore, è necessario installarlo in modo da renderlo disponibile in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per installare un visualizzatore è sufficiente seguire una semplice procedura.  
  
> [!NOTE]
>  Nelle **Store** le app, solo il testo standard, i visualizzatori HTML, XML e JSON sono supportati. Non sono supportati i visualizzatori personalizzati (creati dall'utente).  
  
### <a name="to-install-a-visualizer"></a>Per installare un visualizzatore  
  
1. Individuare la DLL contenente il visualizzatore compilato.  
  
2. Copiare la DLL in uno dei seguenti percorsi:  
  
    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`  
  
    - `My Documents\` *VisualStudioVersion* `\Visualizers`  
  
3. Se si desidera usare un visualizzatore gestito per il debug remoto, copiare la DLL nello stesso percorso nel computer remoto.  
  
4. Riavviare la sessione di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)   
 [Procedura: Scrivere un visualizzatore](../debugger/how-to-write-a-visualizer.md)
