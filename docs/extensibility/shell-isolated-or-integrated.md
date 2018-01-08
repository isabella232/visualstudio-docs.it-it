---
redirect_url: shell/shell-isolated-or-integrated
title: Shell (isolato o integrato) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 787fd7c6980df9809fed9582f4ec8da81de8f862
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="shell-isolated-or-integrated"></a>Shell (isolato o integrato)
È possibile creare la propria applicazione basata su Visual Studio in modalità integrata o isolata. In modalità integrata, molte funzionalità di Visual Studio sono disponibili oltre l'applicazione. In modalità isolata, si sceglie un sottoinsieme di funzionalità di Visual Studio che si desidera distribuire insieme a un'estensione personalizzata.  
  
## <a name="integrated-mode"></a>Modalità integrata  
 La modalità integrata consente agli utenti di usare le funzionalità standard di Visual Studio con gli strumenti personalizzati. La shell integrata è destinata principalmente per l'hosting di linguaggi di programmazione e gli strumenti di sviluppo software.  
  
 Gli strumenti personalizzati che vengono compilati automaticamente su shell integrata di tipo merge con qualsiasi altra edizione di Visual Studio è installato nello stesso computer. Se Visual Studio non è già installato, è possibile fornire una versione ridistribuibile di shell di Visual Studio integrato.  
  
 La versione ridistribuibile di shell di Visual Studio integrated non include linguaggi di programmazione e le funzionalità che supportano i relativi sistemi di progetto.  
  
> [!NOTE]
>  La modalità integrata di Visual Studio shell può essere installata insieme a tutte le edizioni di Visual Studio, ad eccezione di Express.  
  
 Per ulteriori informazioni, vedere [Visual Studio Shell (modalità integrata)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Modalità isolata  
 Modalità isolata consente di creare strumenti personalizzati in grado di eseguire side-by-side con altre versioni di Visual Studio. Serve principalmente per gli strumenti che possono accedere ai servizi di Visual Studio senza a seconda di tutte le funzionalità standard di Visual Studio. È possibile personalizzare l'aspetto di applicazioni basate su shell isolata di Visual Studio. Facilmente, è possibile disattivare le funzionalità e i gruppi di comandi di menu che non si desidera visualizzare insieme all'applicazione.  
  
 Per ulteriori informazioni, vedere [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>La distribuzione dell'applicazione Shell isolata o integrata  
 Per distribuire l'applicazione shell isolata o integrata, è necessario includere l'applicazione, una speciale integrata o isolata shell ridistribuibile e un programma di installazione. Per ulteriori informazioni sull'installazione e distribuzione, vedere [la distribuzione di applicazioni isolate Shell](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  Il [il contratto di licenza utente finale (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552) per integrato e isolata di Visual Studio Shell include una sezione raccolta dati (**sezione 3. Dati**).  Descrive i dati di utilizzo di clienti che possono essere raccolti da Microsoft da utenti di entrambi il software di shell integrata o isolato compilare nell'applicazione. Per ulteriori informazioni, vedere [Visual Studio del prodotto della famiglia informativa sulla Privacy Microsoft](https://www.visualstudio.com/en-us/dn948229).  
>   
>  Se si raccolgono dati di utilizzo separati da parte dei clienti tramite l'applicazione, è necessario fornire preavviso appropriato per gli utenti dell'applicazione di è raccogliere.  Quando si distribuisce il software di shell isolata o integrata come parte dell'applicazione, in base alla licenza di Visual Studio SDK, è necessario includere uno dei valori seguenti:  
>   
>  -   il contratto di licenza come parte della licenza dell'applicazione  
> -   proprio contratto di licenza che richiede agli utenti di accettare le condizioni che la protezione di Visual Studio integrated o almeno molto shell isolata di come le condizioni di licenza utente finale di Microsoft per il software di shell  
  
## <a name="additional-resources"></a>Risorse aggiuntive  
 Per ulteriori informazioni sui pacchetti ridistribuibili, vedere il [download di Visual Studio Extensibility](http://go.microsoft.com/fwlink/?LinkID=119298) sito Web.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione delle estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)