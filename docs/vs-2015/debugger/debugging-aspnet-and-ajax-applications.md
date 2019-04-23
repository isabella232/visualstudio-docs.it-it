---
title: Debug di applicazioni ASP.NET e AJAX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- debugging ASP.NET Web applications
- debugging [ASP.NET], about ASP.NET debugging
- WCF, debugging
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2547c9edb501ac8536b06548ab23a5262515ca78
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116784"
---
# <a name="debugging-aspnet-and-ajax-applications"></a>Debug di applicazioni ASP.NET e AJAX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debug di applicazioni Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] è simile a quello di Windows Form o qualsiasi altra applicazione Windows poiché entrambi i tipi di applicazione impiegano controlli ed eventi. Tuttavia, esistono anche differenze sostanziali tra i due tipi di applicazioni:  
  
- Tenere traccia dello stato è un'operazione più complessa in un'applicazione Web.  
  
- In un'applicazione Windows, il codice di cui eseguire il debug si trova essenzialmente in un punto, mentre per un'applicazione Web il codice può essere sul client e sul server. Mentre il codice [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] è tutto sul server, il codice JavaScript o [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] potrebbe trovarsi anche sul client.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Preparazione al debug di ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 Vengono descritti i passaggi necessari per attivare il debug di applicazioni [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
 [Debug di applicazioni Web](../debugger/debugging-web-applications.md)  
 Viene discusso come eseguire il debug di un'applicazione [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], incluse le applicazioni script compatibili con AJAX.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)  
 Viene spiegato perché è necessario attivare l'opzione Just My Code per il debug di eccezioni [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
 [Debugging and Tracing Ajax Applications Overview](http://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)  
 Vengono illustrati alcuni strumenti e tecniche che possono agevolare il debug del codice AJAX.  
  
 [IntelliTrace](../debugger/intellitrace.md)  
 Eseguire il debug del codice più rapidamente utilizzando IntelliTrace per registrare e verificare la cronologia dello stato dell'applicazione senza riavviare l'applicazione con frequenza. È possibile visualizzare le informazioni sugli eventi e le chiamate che si verificano durante l'esecuzione dell'applicazione e avviare il debug da questi punti nel tempo. Richiede Visual Studio Ultimate.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug di script e applicazioni Web](../debugger/debugging-web-applications-and-script.md)   
 [Debugger Settings and Preparation](../debugger/debugger-settings-and-preparation.md)  (Impostazioni di debug e preparazione)  
 [Debugger Basics](../debugger/debugger-basics.md) (Nozioni di base sul debugger)
