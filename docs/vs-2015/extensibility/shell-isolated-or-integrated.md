---
title: Shell (isolata o integrata) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0db0ab2c2a97f7cedde5b9b3a5ab925467a25146
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300489"
---
# <a name="shell-isolated-or-integrated"></a>Shell (Isolated o Integrated)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile creare un'applicazione personalizzata basata su Visual Studio in modalità integrata o isolata. In modalità integrata sono disponibili molte funzionalità di Visual Studio, oltre all'applicazione. In modalità isolata è possibile scegliere un subset di funzionalità di Visual Studio che si desidera distribuire insieme all'estensione.  
  
## <a name="integrated-mode"></a>Modalità integrata  
 La modalità integrata consente agli utenti di usare le funzionalità standard di Visual Studio insieme agli strumenti personalizzati. La shell integrata è progettata principalmente per ospitare i linguaggi di programmazione e gli strumenti di sviluppo software.  
  
 Gli strumenti personalizzati basati sulla shell integrata si uniscono automaticamente a qualsiasi altra edizione di Visual Studio installata nello stesso computer. È possibile fornire una versione ridistribuibile di Visual Studio Integrated Shell se Visual Studio non è già installato.  
  
 La versione ridistribuibile di Visual Studio Integrated Shell non include i linguaggi di programmazione e le funzionalità che supportano i rispettivi sistemi di progetto.  
  
> [!NOTE]
> La modalità integrata della shell di Visual Studio può essere installata insieme a tutte le edizioni di Visual Studio eccetto le edizioni Express.  
  
 Per ulteriori informazioni, vedere [Visual Studio Shell (Integrated)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Modalità isolata  
 La modalità isolata consente di creare strumenti personalizzati che vengono eseguiti side-by-side con altre versioni di Visual Studio. È destinato principalmente a strumenti che possono accedere ai servizi di Visual Studio senza dipendere da tutte le funzionalità standard di Visual Studio. È possibile personalizzare l'aspetto delle applicazioni basate sulla shell isolata di Visual Studio. È possibile disattivare facilmente le funzionalità e i gruppi di comandi di menu che non si desidera visualizzare insieme all'applicazione.  
  
 Per altre informazioni, vedere [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Distribuzione dell'applicazione shell integrata o isolata  
 Per distribuire l'applicazione shell integrata o isolata, è necessario includere l'applicazione, una speciale shell ridistribuibile integrata o isolata e un programma di installazione. Per ulteriori informazioni sulla distribuzione e sull'installazione, vedere [distribuzione di applicazioni shell isolate](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
> Il [contratto di licenza con l'utente finale (EULA)](https://www.visualstudio.com/support/legal/mt171552) per le shell integrate e isolate di Visual Studio include una sezione sulla raccolta di dati (**sezione 3. Dati**).  Vengono descritti i dati di utilizzo dei clienti che possono essere raccolti da Microsoft dagli utenti del software Shell integrato o isolato compilato nell'applicazione. Per ulteriori informazioni, vedere [Microsoft Visual Studio informativa sulla privacy della famiglia di prodotti](https://www.visualstudio.com/dn948229).  
> 
> Se si raccolgono dati di utilizzo distinti dai clienti attraverso l'applicazione, è necessario fornire l'avviso appropriato agli utenti dell'applicazione degli elementi raccolti.  Quando si distribuisce il software Shell isolato o integrato come parte dell'applicazione, in base alla licenza di Visual Studio Software Development Kit, è necessario includere uno degli elementi seguenti:  
> 
> - il contratto di licenza con l'utente finale come parte della licenza dell'applicazione  
> - il contratto di licenza che richiede ai clienti di accettare le condizioni che proteggono la shell integrata o isolata di Visual Studio almeno quanto le condizioni di licenza dell'utente finale Microsoft per il software della shell  
  
## <a name="additional-resources"></a>Risorse aggiuntive  
 Per ulteriori informazioni sui pacchetti ridistribuibili, vedere il sito Web relativo ai [download di estendibilità di Visual Studio](https://go.microsoft.com/fwlink/?LinkID=119298) .  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione delle estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
