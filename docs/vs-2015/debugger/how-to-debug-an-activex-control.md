---
title: 'Procedura: Debug an ActiveX Control | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f8dea98b05f5350f581128f18f38ec5f095505a5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105671"
---
# <a name="how-to-debug-an-activex-control"></a>Procedura: Eseguire il debug di un controllo ActiveX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Per effettuare il debug di un controllo ActiveX, è necessario specificare un contenitore (eseguibile) in cui elaborare il controllo stesso.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Per specificare un contenitore per la sessione di debug  
  
1. Selezionare il progetto in Esplora soluzioni.  
  
2. Dal **View** menu, scegliere **pagine delle proprietà**.  
  
3. Nella finestra di dialogo **Pagine delle proprietà del progetto** aprire la cartella **Proprietà di configurazione** e selezionare **Debug**.  
  
4. Nella categoria **Debug** individuare la proprietà **Command**.  
  
5. Specificare il percorso del contenitore. Ad esempio, C:\Programmi\Internet Explorer\IEXPLORE.EXE.  
  
6. Se si specifica Internet Explorer come contenitore ed è attivata la modalità Active Desktop, digitare `/new` nella casella **Argomenti del comando**.  
  
7. Fare clic su **OK**.  
  
     Se non si specifica alcun contenitore nella finestra di dialogo **Project Property Pages** (Pagine delle proprietà del progetto), sarà possibile specificarlo all'avvio del debug. Quando si seleziona un comando per avviare il debug, viene visualizzata la finestra di dialogo [Eseguibile per la sessione di debug](../debugger/executable-for-debugging-session-dialog-box.md). Nella finestra di dialogo specificare il nome percorso del contenitore.  
  
## <a name="see-also"></a>Vedere anche  
 [Controlli ActiveX](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [Test di proprietà ed eventi con Test Container](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [Debug di COM e ActiveX](../debugger/com-and-activex-debugging.md)   
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)
