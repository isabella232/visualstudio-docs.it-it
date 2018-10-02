---
title: 'Procedura: applicare automaticamente i codici Product Key durante la distribuzione di Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 11
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 45ed6a059c0a9cf9ae5063e538ec9b9c87698ef1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531582"
---
# <a name="how-to-automatically-apply-product-keys-when-deploying-visual-studio"></a>Procedura: Applicare automaticamente i codici Product Key durante la distribuzione di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio 2017, vedere [applicare automaticamente i codici Product Key durante la distribuzione di Visual Studio](https://docs.microsoft.com/en-us/visualstudio/install/automatically-apply-product-keys-when-deploying-visual-studio).

È possibile applicare il codice product key a livello di programmazione come parte di uno script usato per automatizzare la distribuzione di Visual Studio 2015. I codici Product Key possono essere impostati su un dispositivo a livello di programmazione durante l'installazione di Visual Studio o al termine dell'installazione.  
  
## <a name="apply-the-license-during-installation"></a>Applicare la licenza durante l'installazione  
 Usare il parametro /ProductKey per applicare un codice Product Key durante la procedura di installazione di Visual Studio. Questo parametro di installazione può essere usato con il parametro /Silent per installare Visual Studio in uno stato già concesso in licenza per un utente finale. Per usare il parametro /ProductKey aprire un prompt dei comandi. Eseguire il programma di installazione (ad esempio, vs_enterprise.exe o vs_professional.exe) e impostare il parametro /ProductKey con un codice Product Key (25 caratteri) senza trattini:  
  
 Questo è un comando di esempio per l'installazione di Visual Studio 2015 Enterprise con il codice Product Key AAAAABBBBBCCCCCDDDDDEEEEEEE:  
  
 `vs_enterprise.exe [any other setup parameters] /ProductKey AAAAABBBBBCCCCCDDDDDDEEEEEE`  
  
## <a name="apply-the-license-after-installation"></a>Applicare la licenza dopo l'installazione  
 È possibile attivare una versione installata di Visual Studio con un codice Product Key tramite l'utilità storePID.exe nei computer di destinazione in modalità invisibile all'utente. StorePID.exe è un'utilità che viene installato con Visual Studio  **\<unità >:\\\Programmi file (x86) \Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe**.  
  
 Eseguire storePID.exe con privilegi elevati, usando un agente System Center o un prompt dei comandi con privilegi elevati, seguito dal codice Product Key (con i trattini) e il codice Microsoft Product Code (MPC). Assicurarsi di includere i trattini nel codice Product Key.  
  
 `StorePID.exe [product key including the dashes] [MPC]`  
  
 Questa è una riga di comando di esempio per l'installazione di Visual Studio 2015 Enterprise, con MPC uguale a 07060 e un codice Product Key "AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE":  
  
 `C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 07060`  
  
 La tabella seguente riporta i codici MPC per ogni edizione di Visual Studio:  
  
|Edizione di Visual Studio|MPC|  
|---------------------------|---------|  
|Visual Studio Enterprise 2015|07060|  
|Visual Studio Professional 2015|07062|  
|Visual Studio Test Professional 2015|07066|  
|Visual Studio Ultimate 2013|06181|  
|Visual Studio Premium 2013|06191|  
|Visual Studio Professional 2013|06177|  
|Visual Studio Test Professional 2013|06194|  
  
 Per altre informazioni su come ottenere un codice product key, vedere [procedura: individuare il codice Product Key di Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md).  
  
 Se StorePID.exe ha applicato correttamente il codice Product Key, verrà restituito 0. Se si verificano errori, verrà restituito un numero compreso tra 1 e 6.  
  
## <a name="see-also"></a>Vedere anche  
 [Installare Visual Studio](../install/install-visual-studio-2015.md)