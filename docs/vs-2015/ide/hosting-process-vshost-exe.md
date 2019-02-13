---
title: Processo di hosting (vshost.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3b5ce753b0e3e7523f7c88eac3ad20afc7b0c953
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788134"
---
# <a name="hosting-process-vshostexe"></a>Processo di hosting (vshost.exe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il processo di hosting è una funzionalità di Visual Studio che migliora le prestazioni del debugger, abilita il debug in contesti di attendibilità parziale e la valutazione delle espressioni nella fase di progettazione. I file del processo di hosting contengono vshost nel nome del file e vengono inseriti nella cartella di output del progetto. Per altre informazioni, vedere [Debug e processo di hosting](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
>  I file del processo di hosting (.vshost.exe) vengono usati da Visual Studio e non devono essere eseguiti direttamente o distribuiti con l'applicazione.  
  
## <a name="improved-debugging-performance"></a>Prestazioni di debug migliorate  
 Il processo di hosting crea un dominio dell'applicazione e associa il debugger all'applicazione. L'esecuzione di queste attività può causare un notevole ritardo tra l'inizio del debug e l'avvio dell'applicazione. Il processo di hosting consente di migliorare le prestazioni creando il dominio dell'applicazione, associando il debugger in background e salvando il dominio dell'applicazione e lo stato del debugger tra le esecuzioni dell'applicazione. Per altre informazioni sui domini dell'applicazione, vedere [Domini dell'applicazione](http://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8).  
  
## <a name="partial-trust-debugging"></a>Debug parzialmente attendibile  
 Un'applicazione può essere specificata come applicazione parzialmente attendibile nella [pagina di sicurezza](../ide/reference/security-page-project-designer.md) della **Creazione progetti**. Il debug di un'applicazione parzialmente attendibile richiede un'inizializzazione speciale del dominio dell'applicazione. Tale inizializzazione viene gestita dal processo di hosting.  
  
## <a name="design-time-expression-evaluation"></a>Valutazione delle espressioni per la fase di progettazione  
 La valutazione delle espressioni in fase di progettazione consente di testare il codice dalla finestra di **controllo immediato** senza dover eseguire l'applicazione. Il processo di hosting esegue questo codice durante la valutazione dell'espressione di progettazione. Per altre informazioni, vedere [Finestra di controllo immediato](../ide/reference/immediate-window.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug e processo di hosting](../debugger/debugging-and-the-hosting-process.md)   
 [Procedura: Disabilitare il processo di hosting](../ide/how-to-disable-the-hosting-process.md)   
 [Finestra di controllo immediato](../ide/reference/immediate-window.md)   
 [Domini dell'applicazione](http://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8)
