---
title: Shell (isolata o integrata) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 364a45ea3ae66e3ba8962bfce1487cc04ba35397
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532179"
---
# <a name="shell-isolated-or-integrated"></a>Shell (isolata o integrata)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Shell (isolata o integrata)](https://docs.microsoft.com/visualstudio/extensibility/shell-isolated-or-integrated).  
  
È possibile creare la propria applicazione basata su Visual Studio in modalità integrata o isolata. In modalità integrata, molte funzionalità di Visual Studio sono disponibili oltre all'applicazione. In modalità isolata puoi scegliere un sottoinsieme delle funzionalità di Visual Studio che si desidera distribuire insieme all'estensione.  
  
## <a name="integrated-mode"></a>Modalità di integrazione  
 La modalità integrata consente agli utenti di usare le funzionalità standard di Visual Studio con gli strumenti personalizzati. Shell integrata è destinata principalmente per l'hosting di linguaggi di programmazione e strumenti di sviluppo software.  
  
 Gli strumenti personalizzati che vengono creati automaticamente nella shell integrata di tipo merge con qualsiasi altra edizione di Visual Studio che viene installato nello stesso computer. È possibile fornire una versione ridistribuibile di Visual Studio integrated shell se non è già installato Visual Studio.  
  
 La versione ridistribuibile di Visual Studio integrated shell non include linguaggi di programmazione e le funzionalità che supportano i relativi sistemi di progetto.  
  
> [!NOTE]
>  La modalità integrata di Visual Studio shell può essere installata insieme a tutte le edizioni di Visual Studio tranne le edizioni Express.  
  
 Per altre informazioni, vedere [Visual Studio Shell (Integrated)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Modalità isolata  
 Modalità isolata consente di creare strumenti personalizzati da eseguire side-by-side con altre versioni di Visual Studio. Si tratta principalmente per gli strumenti che possono accedere ai servizi di Visual Studio senza a seconda di tutte le funzionalità standard di Visual Studio. È possibile personalizzare l'aspetto delle applicazioni create su shell isolata di Visual Studio. È facilmente possibile disattivare le funzionalità e i gruppi di comandi di menu che non si desidera visualizzare insieme all'applicazione.  
  
 Per altre informazioni, vedere [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>La distribuzione dell'applicazione Shell isolata o integrata  
 Per distribuire l'applicazione shell isolata o integrata, è necessario includere l'applicazione, una speciale integrata o isolata shell redistributable e un programma di installazione. Per altre informazioni sulla distribuzione e l'installazione, vedere [distribuzione di applicazioni isolate Shell](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  Il [contratto di licenza utente finale (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552) for integrata e isolata di Visual Studio Shell incluso una sezione sulla raccolta dei dati (**sezione 3. Dati**).  Descrive i dati di utilizzo dei clienti che possono essere raccolti da Microsoft da utenti che il software di shell integrata o isolata che si compila l'applicazione. Per altre informazioni, vedere [informativa della famiglia di prodotti di Microsoft Visual Studio sulla Privacy](https://www.visualstudio.com/en-us/dn948229).  
>   
>  Se si raccolgono i dati di utilizzo separato dai tuoi clienti tramite l'applicazione, è necessario fornire preavviso appropriato per gli utenti dell'applicazione è raccogliere.  Quando si distribuisce il software di shell isolata o integrata come parte dell'applicazione, in base alla licenza di Visual Studio Software Development Kit, è necessario includere uno dei seguenti:  
>   
>  -   il contratto di licenza utente finale come parte della licenza dell'applicazione  
> -   il proprio contratto di licenza che richiede agli utenti di accettare le condizioni che la protezione di Visual Studio integrata o isolata shell almeno della quantità come condizioni di licenza Microsoft utente finale per il software della shell  
  
## <a name="additional-resources"></a>Risorse aggiuntive  
 Per altre informazioni sui pacchetti ridistribuibili, vedere la [download di Visual Studio Extensibility](http://go.microsoft.com/fwlink/?LinkID=119298) sito Web.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione delle estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
