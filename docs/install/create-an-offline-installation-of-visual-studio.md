---
title: Creare un'installazione offline di Visual Studio | Microsoft Docs
description: Informazioni dettagliate sull'installazione offline di Visual Studio.
ms.custom: 
ms.date: 08/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 8b0902c7e2d3c2b51ecd915647a3e8a03e49c641
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/11/2017
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Creare un'installazione offline di Visual Studio 2017

Il programma di installazione di Visual Studio 2017 è stato progettato per funzionare correttamente in computer e reti diversi, in condizioni di qualsiasi tipo.

- Il nuovo modello basato sul carico di lavoro consente di scaricare un minor numero di componenti rispetto alle precedenti versioni di Visual Studio: l'installazione più piccola richiede solo 300 MB.
- Anziché un file "ISO" o un file zip generico ora vengono scaricati solo i pacchetti necessari per il computer. Ad esempio i file a 64 bit vengono scaricati solo se sono necessari.
- Durante il processo di installazione, vengono provate tre diverse tecnologie di download (WebClient, BITS e WinInet) per ridurre al minimo le interferenze con software proxy e anti-virus;
- I file necessari per l'installazione di Visual Studio vengono distribuiti in una rete di distribuzione globale e possono quindi essere recuperati da un server locale.

È consigliabile provare il nuovo [programma di installazione Web di Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)&mdash;, che garantisce risultati molto soddisfacenti.

 > [!div class="button"]
 > [Scaricare Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)
<br/>

Se si vuole eseguire l'installazione offline perché la connessione Internet non è disponibile o non è affidabile, vedere [Installare Visual Studio 2017 in ambienti di rete con larghezza di banda ridotta o non affidabili](../install/install-vs-inconsistent-quality-network.md). È possibile usare la riga di comando per creare una cache locale dei file necessari per completare l'installazione offline. Questo processo sostituisce i file ISO disponibili per le versioni precedenti.

> [!NOTE]
> Gli amministratori dell'organizzazione che vogliono distribuire Visual Studio 2017 in una rete di workstation client protette da Internet tramite firewall possono vedere le pagine [Creare un'installazione di rete di Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) e [Considerazioni speciali per l'installazione di Visual Studio in un ambiente offline](../install/install-visual-studio-in-offline-environment.md).

## <a name="get-support"></a>Supporto
Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce,per suggerimenti per la risoluzione dei problemi vedere la pagina [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). È anche possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) nell'IDE di Visual Studio o condividere un suggerimento su [UserVoice](https://visualstudio.uservoice.com/forums/121579). È possibile visualizzare lo stato dei problemi del prodotto nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/), dove è possibile creare domande e trovare risposte. È anche possibile comunicare con Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio) (è necessario un account [GitHub](https://github.com/)).
