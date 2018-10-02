---
title: 'Procedura: Debug an ActiveX Control | Microsoft Docs'
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
- vc.controls.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc47ba913ba9da1ecfe8e0df34894c31545e1734
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526569"
---
# <a name="how-to-debug-an-activex-control"></a>Procedura: eseguire il debug di un controllo ActiveX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: Debug an ActiveX Control](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-an-activex-control).  
  
NOTA]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Per effettuare il debug di un controllo ActiveX, è necessario specificare un contenitore (eseguibile) in cui elaborare il controllo stesso.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Per specificare un contenitore per la sessione di debug  
  
1.  Selezionare il progetto in Esplora soluzioni.  
  
2.  Dal **View** menu, scegliere **pagine delle proprietà**.  
  
3.  Nel **pagine delle proprietà del progetto** finestra di dialogo, aprire il **le proprietà di configurazione** cartella e selezionare **debug**.  
  
4.  Sotto il **Debugging** categoria, individuare il **comando** proprietà.  
  
5.  Specificare il percorso del contenitore. Ad esempio, C:\Programmi\Internet Explorer\IEXPLORE.EXE.  
  
6.  Se si specifica Internet Explorer come contenitore e si usa Desktop attivo, digitare `/new` nella **gli argomenti del comando** casella.  
  
7.  Fare clic su **OK**.  
  
     Se non si specifica un contenitore nel **pagine delle proprietà del progetto** nella finestra di dialogo è possibile specificare il contenitore quando si inizia il debug. Quando si seleziona un comando per avviare il debug, il [eseguibile per la finestra di dialogo di sessione di debug](../debugger/executable-for-debugging-session-dialog-box.md) viene visualizzata. Nella finestra di dialogo specificare il nome percorso del contenitore.  
  
## <a name="see-also"></a>Vedere anche  
 [Controlli ActiveX](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [Test di proprietà ed eventi con Test Container](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [Debug di COM e ActiveX](../debugger/com-and-activex-debugging.md)   
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)



