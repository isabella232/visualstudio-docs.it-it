---
title: Domande frequenti su R Tools per Visual Studio
description: Domande frequenti su R in Visual Studio.
ms.date: 12/04/2017
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 8c89f1d59405fb7475e827cac9624c6623d7041e
ms.sourcegitcommit: 1d74273a50ede5a90d9d64372d93aad357daef42
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "89365665"
---
# <a name="frequently-asked-questions"></a>Domande frequenti

## <a name="visual-studio-support"></a>Supporto di Visual Studio

**D. RTVS funziona in OS X o Linux?**

R. RTVS è attualmente basato su Visual Studio, un'implementazione solo per Windows. Microsoft sta valutando il supporto in Visual Studio Code e Visual Studio per Mac. Fare riferimento al [problema 1295 di RTVS](https://github.com/Microsoft/RTVS/issues/1295).

**D. RTVS funziona con Visual Studio Express edizioni?**

R. No.

**D. È possibile usare le estensioni di Visual Studio con RTVS?**

R. Assolutamente sì. Di seguito sono elencate alcune estensioni usate di frequente dagli utenti che utilizzano R.

- [VsVim per tasti di scelta rapida Vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Editor markdown con anteprima in tempo reale](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Per altre informazioni, vedere [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

**D. Poiché RTVS è in Visual Studio, significa che R può essere usato facilmente con C#, C++ e altri linguaggi Microsoft?**

R. No. RTVS è uno strumento per lo sviluppo di codice R e usa gli interpreti R nativi standard. L'interoperabilità tra R e altri linguaggi non è al momento supportata.

**D. RTVS funziona con impostazioni locali diverse dall'inglese?**

R. La versione 1.0 di RTVS è solo in lingua inglese. La versione 1.1 sarà localizzata per lo stesso set di lingue di Visual Studio. Nel frattempo, usare [Visual Studio 2015 Language Pack](https://www.microsoft.com/download/details.aspx?id=48157) o, in Visual Studio 2017, eseguire il programma di installazione e selezionare Inglese nella scheda **Language Pack**.

![Impostazioni internazionali per Visual Studio 2017](media/FAQ-international-settings.png)

**D. Sono molto apprezzato le impostazioni correnti di Visual Studio, ma voglio provare le nuove impostazioni di Data Science. Cosa dovrei fare?**

R. Salvare le impostazioni correnti di Visual Studio usando **gli strumenti**  >  **Importa/Esporta impostazioni**, quindi passare alle impostazioni di Data Science. Per ripristinare le impostazioni salvate, usare di nuovo il comando **Importa/Esporta impostazioni**.

**D. È possibile archiviare il progetto di Visual Studio in una condivisione di rete?**

R. No, Visual Studio non supporta il caricamento di progetti da una condivisione di rete.

## <a name="r-interpretersintegration"></a>Interpreti/integrazione di R

**D. Quali interpreti R funzionano con RTVS?**

R. [CRAN R](https://cran.r-project.org/), [Microsoft R Client e Microsoft Machine Learning Server](/machine-learning-server/)

**D. Dove è possibile scaricare questi interpreti?**

R. Vedere l'argomento [Installation](installing-r-tools-for-visual-studio.md) (Installazione).

D. **Che cos'è Microsoft R Server?**

R. R Server è il nome precedente di [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**D. RTVS funziona con le edizioni di R a 32 bit?**

R. No, RTVS supporta soltanto edizioni di R a 64 bit in esecuzione su edizioni di Windows a 64 bit.

**D. RTVS funziona con il sistema di controllo del codice sorgente?**

R. Sì, è possibile usare qualsiasi sistema di controllo del codice sorgente integrato in Visual Studio.

**D. Quali sono le impostazioni consigliate *. gitignore* per un progetto RTVS?**

R. GitHub gestisce un repository di file con *estensione gitignore* consigliati. È possibile visualizzarlo qui: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Servizi remoti

Q. **Cosa sono i servizi remoti in Visual Studio?**

R. I servizi R remoti per Visual Studio consentono di configurare un computer Windows o Linux e quindi di connettersi a tale computer da RTVS. Vedere [Impostare aree di lavoro remote](setting-up-remote-r-workspaces.md).

Q. **RTVS può connettersi a Microsoft Machine Learning Server?**

R. No, in quanto Microsoft ML Server è una tecnologia diversa e non offre lo stesso meccanismo di connettività richiesto da RTVS.

Q. **RTVS può connettersi a una macchina virtuale creata usando l'immagine di macchina virtuale data science in Azure?**

R. Sì. Nell'immagine [Data Science Virtual Machine - Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) sono preinstallati i servizi R remoti per Visual Studio.

D. **RTVS può connettersi a un computer remoto con R installato?**

Per eseguire codice R in un computer remoto deve esistere un servizio che si pone in ascolto delle richieste, riceve il codice e restituisce i risultati al computer client. Queste sono le funzionalità dei servizi R remoti per Visual Studio. Vedere [Impostare aree di lavoro remote](setting-up-remote-r-workspaces.md).

Q. **Che cos'è una sessione remota?**

R. Vedere l'articolo [Execute on remote server](/machine-learning-server/r/how-to-execute-code-remotely) (Eseguire in un server remoto) nella documentazione di Machine Learning Server.

## <a name="rtvs-development-and-features"></a>Sviluppo e funzionalità di RTVS

**D. manca la funzionalità X, ma RStudio**

R. RStudio è un IDE per R avanzato e maturo il cui sviluppo è in corso da diversi anni. RTVS tenta di offrire tutte le funzionalità critiche necessarie agli utenti. Consente di classificare in ordine di priorità il lavoro futuro mediante la presentazione di problemi in [GitHub](https://github.com/Microsoft/RTVS/issues/)

**D. Posso contribuire a RTVS?**

R. Assolutamente sì. Il codice sorgente è disponibile su [GitHub](https://github.com/microsoft/RTVS). Usare la funzionalità di gestione dei problemi per segnalare bug e commentare quelli già registrati.

È anche possibile contribuire a questa documentazione. è &mdash; sufficiente selezionare il comando **Edit (modifica** ) in alto a destra in qualsiasi pagina. Sono inoltre benvenuti i commenti sulla documentazione, da aggiungere nella parte inferiore della pagina.
