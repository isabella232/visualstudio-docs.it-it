---
title: 'Procedura: eseguire il Debug di codice inserito | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.injected
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f283a8e526e343030636c62453e5eb03825a8f93
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528508"
---
# <a name="how-to-debug-injected-code"></a>Procedura: eseguire il debug di codice inserito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: eseguire il Debug del codice inserito](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-injected-code).  
  
NOTA]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Il ricorso agli attributi può semplificare notevolmente la programmazione in C++. Per altre informazioni, vedere [concetti](http://msdn.microsoft.com/library/563e7e7c-65e1-44f4-b0b2-da04a6c1bc9e). Alcuni attributi sono interpretati direttamente dal compilatore. Con altri attributi è invece possibile inserire codice nell'origine del programma, il quale verrà quindi compilato dal compilatore. Questo codice inserito rende più semplice la programmazione perché riduce la quantità di codice che è necessario scrivere. A volte, tuttavia, può accadere che un bug arresti l'applicazione mentre è in esecuzione il codice inserito. Quando ciò accade, può essere utile esaminare tale codice e Visual Studio prevede due metodi per farlo:  
  
-   È possibile visualizzare il codice inserito nel **Disassembly** finestra.  
  
-   Usando [/Fx](http://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560), è possibile creare un file di origine unito contenente il codice inserito e originale.  
  
 Il **Disassembly** finestra vengono visualizzate le istruzioni in linguaggio assembly che corrispondono a codice sorgente e il codice inserito dagli attributi. Inoltre, il **Disassembly** finestra possono essere visualizzate l'annotazione del codice sorgente.  
  
### <a name="to-turn-on-source-annotation"></a>Per attivare l'annotazione del codice sorgente  
  
-   Fare doppio clic il **Disassembly** finestra, scegliere **Mostra codice sorgente** dal menu di scelta rapida.  
  
     Se si conosce la posizione di un attributo in una finestra di origine, è possibile usare il menu di scelta rapida per trovare il codice inserito nel **Disassembly** finestra.  
  
### <a name="to-view-injected-code"></a>Per visualizzare il codice inserito  
  
1.  Il debugger deve essere in modalità di interruzione.  
  
2.  In una finestra di codice sorgente, portare il cursore davanti all'attributo di cui si desidera visualizzare il codice inserito.  
  
3.  Pulsante destro del mouse e selezionare **Vai a Disassembly** dal menu di scelta rapida.  
  
     Se la posizione dell'attributo è vicino al punto di esecuzione corrente, è possibile selezionare i **Disassembly** finestra dalle **Debug** menu.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Per visualizzare il codice disassembly al punto di esecuzione corrente  
  
1.  Il debugger deve essere in modalità di interruzione.  
  
2.  Dal **Debug** menu, scegliere **Windows**, fare clic su **Disassembly**.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)



