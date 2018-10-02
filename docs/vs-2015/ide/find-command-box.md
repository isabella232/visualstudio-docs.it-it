---
title: Casella Trova/Comando | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 22ced396f8a18cf2a665ed7a1ba1016b16e44c8d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520072"
---
# <a name="findcommand-box"></a>Trova/Comando (casella)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [casella Trova / comando](https://docs.microsoft.com/visualstudio/ide/find-command-box).  
  
È possibile cercare testo ed eseguire i comandi di Visual Studio dalla casella **Trova/Comando**. La casella **Trova/Comando** è ancora disponibile nella barra degli strumenti, ma non è più visibile per impostazione predefinita. È possibile visualizzare la casella **Trova/Comando** scegliendo **Aggiungi o rimuovi pulsanti** nella barra degli strumenti **Standard** e scegliendo **Trova**.  
  
 Per eseguire un comando di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], anteporre il segno di maggiore di (>).  
  
 La casella **Trova/Comando** memorizza gli ultimi 20 elementi immessi e li visualizza in un elenco a discesa. È possibile spostarsi nell'elenco usando i tasti di direzione.  
  
 ![Casella Trova&#47;Comando](../ide/media/findcommandbox.png "FindCommandBox")  
Trova/Comando (casella)  
  
## <a name="searching-for-text"></a>Ricerca di testo  
 Per impostazione predefinita, quando si specifica il testo nella casella **Trova/Comando** e si preme il tasto INVIO, Visual Studio esegue la ricerca nella finestra del documento o dello strumento corrente usando le opzioni specificate nella finestra di dialogo **Cerca nei file**. Per altre informazioni, vedere [Finding and Replacing Text](../ide/finding-and-replacing-text.md).  
  
## <a name="entering-commands"></a>Immissione di comandi  
 Per usare la casella **Trova/Comando** per eseguire un singolo comando o alias di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] invece che per cercare il testo, immettere il comando di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] anteponendo il simbolo di maggiore di (>). Ad esempio:  
  
```  
>File.NewFile c:\temp\MyFile /t:"General\Text File"  
```  
  
 In alternativa, è anche possibile usare la finestra di comando per immettere ed eseguire comandi singoli o multipli. Alcuni comandi o alias possono essere immessi ed eseguiti da soli, mentre altri richiedono l'immissione di argomenti nella sintassi. Per un elenco di comandi con argomenti, vedere [Comandi di Visual Studio](../ide/reference/visual-studio-commands.md).  
  
## <a name="escape-characters"></a>Caratteri di escape  
 Un accento circonflesso (^) in una riga di comando indica che il carattere immediatamente successivo viene interpretato letteralmente e non come carattere di controllo. In questo modo, è possibile incorporare virgolette diritte ("), spazi, barre iniziali, accenti circonflessi o qualsiasi altro carattere letterale nel valore di un parametro o di un'opzione, ad eccezione dei nomi di opzioni. Ad esempio,  
  
```  
>Edit.Find ^^t /regex  
```  
  
 L'accento circonflesso presenta lo stesso funzionamento sia all'interno sia all'esterno delle virgolette. Se corrisponde all'ultimo carattere sulla riga, viene ignorato.  
  
## <a name="see-also"></a>Vedere anche  
 [Command Window](../ide/reference/command-window.md)  (Finestra di comando)  
 [Ricerca e sostituzione di testo](../ide/finding-and-replacing-text.md)



