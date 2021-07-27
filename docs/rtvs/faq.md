---
title: Domande frequenti su R Tools per Visual Studio
description: Domande frequenti su R in Visual Studio.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: acfd103e3839115c795de57c8e3359058885b7a6
ms.sourcegitcommit: fdba1b294b94e1f6a8e897810646873422393fff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2021
ms.locfileid: "114679992"
---
# <a name="frequently-asked-questions"></a>Domande frequenti

## <a name="visual-studio-support"></a>Supporto di Visual Studio

**D. RTVS funziona in OS X o Linux?**

A. RTVS è attualmente basato su Visual Studio, un'implementazione solo per Windows. Microsoft sta valutando il supporto in Visual Studio Code e Visual Studio per Mac. Fare riferimento al [problema 1295 di RTVS](https://github.com/Microsoft/RTVS/issues/1295).

**D. RTVS funziona con Visual Studio Express edizioni?**

R. No.

**D. È possibile usare Visual Studio con RTVS?**

A. Assolutamente sì. Di seguito sono elencate alcune estensioni usate di frequente dagli utenti che utilizzano R.

- [VsVim per tasti di scelta rapida Vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Editor markdown con anteprima in tempo reale](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Per altre informazioni, vedere [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

**D. Poiché RTVS è in Visual Studio, significa che R può essere usato facilmente con C#, C++ e altri linguaggi Microsoft?**

R. No. RTVS è uno strumento per lo sviluppo di codice R e usa gli interpreti R nativi standard. L'interoperabilità tra R e altri linguaggi non è al momento supportata.

**D. RTVS funziona con impostazioni locali diverse dall'inglese?**

A. La versione 1.0 di RTVS è solo in lingua inglese. La versione 1.1 sarà localizzata per lo stesso set di lingue di Visual Studio. Nel frattempo, usare [Visual Studio 2015 Language Pack](https://www.microsoft.com/download/details.aspx?id=48157) o, in Visual Studio 2017, eseguire il programma di installazione e selezionare Inglese nella scheda **Language Pack**.

![Impostazioni internazionali per Visual Studio 2017](media/FAQ-international-settings.png)

**D. Mi piace molto le impostazioni Visual Studio, ma voglio provare le nuove impostazioni di data science. Cosa dovrei fare?**

A. Salvare le impostazioni Visual Studio impostazioni **correnti** usando Strumenti importa ed esporta Impostazioni e quindi  >  passare alle impostazioni di data science. Per ripristinare le impostazioni salvate, usare di nuovo il comando **Importa/Esporta impostazioni**.

**D. È possibile archiviare il Visual Studio progetto in una condivisione di rete?**

A. No, Visual Studio non supporta il caricamento di progetti da una condivisione di rete.

## <a name="r-interpretersintegration"></a>Interpreti/integrazione di R

**D. Con quali interpreti R funziona RTVS?**

A. [CRAN R](https://cran.r-project.org/), [Microsoft R Client e Microsoft Machine Learning Server](/machine-learning-server/)

**D. Dove è possibile scaricare questi interpreti?**

A. Vedere l'argomento [Installation](installing-r-tools-for-visual-studio.md) (Installazione).

D. **Che cos'è Microsoft R Server?**

A. R Server è il nome precedente di [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**D. RTVS funziona con le edizioni a 32 bit di R?**

A. No, RTVS supporta soltanto edizioni di R a 64 bit in esecuzione su edizioni di Windows a 64 bit.

**D. RTVS funziona con il sistema di controllo del codice sorgente?**

A. Sì, è possibile usare qualsiasi sistema di controllo del codice sorgente integrato in Visual Studio.

**D. Quali sono le impostazioni *consigliate per gitignore* per un progetto RTVS?**

A. GitHub un repository di file *gitignore* consigliati. È possibile visualizzarlo qui: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Servizi remoti

Q. **Cosa sono i servizi remoti in Visual Studio?**

A. I servizi R remoti per Visual Studio consentono di configurare un computer Windows o Linux e quindi di connettersi a tale computer da RTVS. Vedere [Impostare aree di lavoro remote](setting-up-remote-r-workspaces.md).

Q. **RTVS può connettersi a Microsoft Machine Learning Server?**

A. No, in quanto Microsoft ML Server è una tecnologia diversa e non offre lo stesso meccanismo di connettività richiesto da RTVS.

Q. **RTVS può connettersi a una macchina virtuale creata usando l'immagine di macchina virtuale data science in Azure?**

A. Sì. Nell'immagine [Data Science Virtual Machine - Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) sono preinstallati i servizi R remoti per Visual Studio.

D. **RTVS può connettersi a un computer remoto con R installato?**

Per eseguire codice R in un computer remoto deve esistere un servizio che si pone in ascolto delle richieste, riceve il codice e restituisce i risultati al computer client. Queste sono le funzionalità dei servizi R remoti per Visual Studio. Vedere [Impostare aree di lavoro remote](setting-up-remote-r-workspaces.md).

Q. **Che cos'è una sessione remota?**

A. Vedere l'articolo [Execute on remote server](/machine-learning-server/r/how-to-execute-code-remotely) (Eseguire in un server remoto) nella documentazione di Machine Learning Server.

## <a name="rtvs-development-and-features"></a>Sviluppo e funzionalità di RTVS

**D. La funzionalità X è mancante, ma RStudio lo ha.**

A. RStudio è un IDE per R avanzato e maturo il cui sviluppo è in corso da diversi anni. RTVS tenta di offrire tutte le funzionalità critiche necessarie agli utenti. Contribuire a classificare in ordine di priorità il lavoro futuro tramite la presentazione di [problemi GitHub](https://github.com/Microsoft/RTVS/issues/).

**D. È possibile contribuire a RTVS?**

A. Assolutamente sì. Il codice sorgente è disponibile su [GitHub](https://github.com/microsoft/RTVS). Usare la funzionalità di gestione dei problemi per segnalare bug e commentare quelli già registrati.

È anche possibile contribuire a questa documentazione semplicemente selezionare il &mdash; **comando** Modifica in alto a destra in qualsiasi pagina. Sono inoltre benvenuti i commenti sulla documentazione, da aggiungere nella parte inferiore della pagina.
