---
title: 'Procedura: Eseguire il debug di codice inserito | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b7b411574dcf65bdd1ec64c1fc51bd1813f09abb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432334"
---
# <a name="how-to-debug-injected-code"></a>Procedura: Eseguire il debug di codice inserito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Il ricorso agli attributi può semplificare notevolmente la programmazione in C++. Per altre informazioni, vedere [concetti](http://msdn.microsoft.com/library/563e7e7c-65e1-44f4-b0b2-da04a6c1bc9e). Alcuni attributi sono interpretati direttamente dal compilatore. Con altri attributi è invece possibile inserire codice nell'origine del programma, il quale verrà quindi compilato dal compilatore. Questo codice inserito rende più semplice la programmazione perché riduce la quantità di codice che è necessario scrivere. A volte, tuttavia, può accadere che un bug arresti l'applicazione mentre è in esecuzione il codice inserito. Quando ciò accade, può essere utile esaminare tale codice e Visual Studio prevede due metodi per farlo:  
  
- Visualizzare il codice inserito nella finestra **Disassembly**.  
  
- Creare, tramite [/Fx](http://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560), un file di origine unito contenente il codice originale e il codice inserito.  
  
  Nella finestra **Disassembly** vengono visualizzate le istruzioni in linguaggio assembly che corrispondono al codice sorgente e al codice inserito da attributi. Nella finestra **Disassembly** sono riportate anche le annotazioni del codice sorgente.  
  
### <a name="to-turn-on-source-annotation"></a>Per attivare l'annotazione del codice sorgente  
  
- Fare clic con il pulsante destro del mouse sulla finestra **Disassembly** e scegliere **Mostra codice sorgente** dal menu di scelta rapida.  
  
     Se si conosce la posizione di un attributo in una finestra di origine, sarà possibile usare il menu di scelta rapida per trovare il codice inserito nella finestra **Disassembly**.  
  
### <a name="to-view-injected-code"></a>Per visualizzare il codice inserito  
  
1. Il debugger deve essere in modalità di interruzione.  
  
2. In una finestra di codice sorgente, portare il cursore davanti all'attributo di cui si desidera visualizzare il codice inserito.  
  
3. Fare clic con il pulsante destro del mouse e scegliere **Vai a disassembly** dal menu di scelta rapida.  
  
     Se l'attributo si trova vicino al punto di esecuzione corrente, sarà possibile scegliere la finestra **Disassembly** dal menu **Debug**.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Per visualizzare il codice disassembly al punto di esecuzione corrente  
  
1. Il debugger deve essere in modalità di interruzione.  
  
2. Scegliere **Finestre** dal menu **Debug** e fare clic su **Disassembly**.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)
