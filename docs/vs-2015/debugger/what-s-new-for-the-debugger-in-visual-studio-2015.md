---
title: Quali sono le novità relative al Debugger di Visual Studio 2015 | Microsoft Docs
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
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
caps.latest.revision: 86
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 743875ef4ab7582bd4c1a254c82f168b96ba8208
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188617"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2015"></a>Novità relative al debugger di Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per informazioni sulle novità relative al debug ed alla diagnostica di Visual Studio 2015 Update 1, vedere le [note sulla versione di Visual Studio 2015 Update 1](https://www.visualstudio.com/news/vs2015-update1-vs#debug).  
  
 Per informazioni sulle novità relative al debug ed alla diagnostica di Visual Studio 2015 RTM, vedere le [note sulla versione di Visual Studio 2015](https://www.visualstudio.com/news/vs2015-vs#debug).  
  
## <a name="visual-studio-2015-update-1-changes"></a>Modifiche apportate in Visual Studio 2015 Update 1  
 L'opzione Modifica e continuazione per C++ supporta più funzionalità. Per altre informazioni, vedere [modifica e continuazione (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
 Per il debug delle violazioni di accesso Visual C++, una nuova finestra di dialogo di eccezione specifica il puntatore che ha causato l'eccezione. Per altre informazioni, vedere [How Can I Debug an Access Violation?](../debugger/how-can-i-debug-an-access-violation-q.md) e l'articolo sul [miglioramento nel debug delle violazioni di accesso C++ in Visual Studio 2015 Update 1](http://blogs.msdn.com/b/visualstudioalm/archive/2015/10/29/improvement-to-debugging-c-access-violations-in-visual-studio-2015-update-1.aspx)  
  
## <a name="visual-studio-2015-rtm-debugger-ui-and-hotkey-changes"></a>Modifiche apportate all'interfaccia utente e ai tasti di scelta rapida del debugger di Visual Studio 2015 RTM  
 Modifiche significative di interfaccia utente sono state eseguite nelle eccezioni e nei punti di interruzione.  
  
### <a name="breakpoints"></a>Punti di interruzione  
 In Visual Studio 2015 esiste un nuovo modo per configurare i punti di interruzione, vale a dire la finestra **Impostazioni del punto di interruzione** .  
  
 Di seguito sono riepilogate le finestre e i tasti di scelta rapida principali di Punti di interruzione:  
  
|Funzionalità|Percorso del menu|Tasto di scelta rapida|  
|-------------|-------------------|------------|  
|Nuovo punto di interruzione, attiva/disattiva punto di interruzione|**Eseguire il debug / attiva/disattiva punto di interruzione**<br /><br /> menu di scelta rapida nell'editor/ **Inserisci punto di interruzione**<br /><br /> fare clic sul margine sinistro|F9|  
|Nuovo punto di interruzione della funzione|**Eseguire il debug / nuovo punto di interruzione / punto di interruzione di funzione**|In Visual Studio 2015 RTM (con nessun aggiornamento), usare ALT+F9, B<br /><br /> In Visual Studio 2015 Update 1 e versioni successive, usare CTRL + B|  
|Finestra**Punti di interruzione** |**Eseguire il debug / Windows / punti di interruzione**|CTRL + ALT + B|  
|**Impostazioni del punto di interruzione**, **Condizioni**|menu di scelta rapida del punto di interruzione/ **Condizioni**|ALT + F9, B|  
|**Impostazioni del punto di interruzione**, **Azioni**|menu di scelta rapida del punto di interruzione/ **Azioni**|Nessun tasto di scelta rapida|  
  
 Per altre informazioni, vedere i seguenti articoli:  
  
1.  [Uso di punti di interruzione](../debugger/using-breakpoints.md)  
  
2.  [Nuova esperienza di configurazione di punti di interruzione](http://blogs.msdn.com/b/visualstudioalm/archive/2014/10/06/new-breakpoint-configuration-experience.aspx)  
  
3.  [Esperienza di configurazione di punti di interruzione](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711)  
  
### <a name="exception-settings"></a>Impostazioni eccezioni  
 La nuova finestra **Impostazioni eccezioni** consente di specificare il tipo di gestione delle eccezioni desiderato per le singole eccezioni o categorie di eccezioni.  
  
|Funzionalità|Percorso del menu|Tasto di scelta rapida|  
|-------------|-------------------|------------|  
|Finestra**Impostazioni eccezioni** |**Eseguire il debug / Windows / impostazioni eccezioni**|CTRL + ALT + E|  
  
 Per altre informazioni, vedere i seguenti articoli:  
  
1.  [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)  
  
2.  [La nuova finestra eccezioni](http://blogs.msdn.com/b/visualstudioalm/archive/2015/02/23/the-new-exception-settings-window-in-visual-studio-2015.aspx)  
  
### <a name="edit-and-continue"></a>Modifica e continuazione  
 In Visual Studio 2015, è possibile impostare Modifica e continuazione nella pagina **Strumenti/Opzioni/Debug/Generale** . Nelle versioni precedenti, queste impostazioni si trovavano in una categoria di opzioni separate.  
  
### <a name="attach-to-process"></a>Connetti a processo  
 In Visual Studio 2015 il comando Connetti a processo è disponibile solo nel menu Debug. Nella versione precedente era disponibile anche nel menu Strumenti. Il tasto di scelta rapida CTRL+ALT+P funziona in tutte le versioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)



