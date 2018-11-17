---
title: 'Procedura: installare un visualizzatore | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: d5b2c77bd5f9d32b3bb4a0954017b7abdee1947c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731464"
---
# <a name="how-to-install-a-visualizer"></a>Procedura: installare un visualizzatore
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dopo avere creato un visualizzatore, è necessario installarlo in modo da renderlo disponibile in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per installare un visualizzatore è sufficiente seguire una semplice procedura.  
  
> [!NOTE]
>  Nelle **Store** le app, solo il testo standard, i visualizzatori HTML, XML e JSON sono supportati. Non sono supportati i visualizzatori personalizzati (creati dall'utente).  
  
### <a name="to-install-a-visualizer"></a>Per installare un visualizzatore  
  
1.  Individuare la DLL contenente il visualizzatore compilato.  
  
2.  Copiare la DLL in uno dei seguenti percorsi:  
  
    -   *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\` *VisualStudioVersion* `\Visualizers`  
  
3.  Se si desidera usare un visualizzatore gestito per il debug remoto, copiare la DLL nello stesso percorso nel computer remoto.  
  
4.  Riavviare la sessione di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)   
 [Procedura: Scrivere un visualizzatore](../debugger/how-to-write-a-visualizer.md)



