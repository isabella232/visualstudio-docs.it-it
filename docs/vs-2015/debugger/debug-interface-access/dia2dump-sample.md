---
title: Esempio Dia2dump | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 410d4e8cf2a63c7d01058e501391f02543b1eee7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529572"
---
# <a name="dia2dump-sample"></a>Esempio Dia2dump
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [esempio Dia2dump](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/dia2dump-sample).  
  
Esempio Dia2dump viene installato con Visual Studio e contiene il database di origine dia2dump.cpp. Il file eseguibile compilato viene eseguito dalla riga di comando e visualizza il contenuto di un file di database (con estensione pdb) intero programma.  
  
### <a name="to-install-the-sample"></a>Per installare l'esempio  
  
1.  Verificare che il sistema soddisfi tutti i requisiti di installazione descritti nella pagina di avvio installazione di Visual Studio.  
  
2.  Installare Visual Studio e seguire tutte le istruzioni di installazione e configurazione per gli esempi inclusi.  
  
#### <a name="to-build-the-sample"></a>Per compilare l'esempio  
  
1.  Aprire il file Dia2dump.sln in Visual Studio. (Se necessario, Visual Studio verrà prima di tutto informazioni utili per aggiornare il progetto Dia2dump.)  
  
2.  Nelle pagine delle proprietà di progetto, nelle **C/C++** &#124; **generali** &#124; **directory di inclusione aggiuntive** proprietà, specificare il `..\DIA SDK\include` directory. In questo modo si garantisce che il compilatore possa trovare il file dia2.h.  
  
3.  Nel **compilare** menu, fare clic su **Ricompila soluzione**.  
  
4.  Chiudere Visual Studio.  
  
#### <a name="to-run-the-sample"></a>Per eseguire l'esempio  
  
1.  Aprire un prompt dei comandi e digitare quanto segue:  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Origine Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Procedura: Risolvere i problemi relativi agli aggiornamenti di progetti Visual Studio con esito negativo](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)


