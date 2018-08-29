---
title: Creare un'installazione offline di Visual Studio
description: Informazioni dettagliate sull'installazione offline di Visual Studio.
ms.custom: ''
ms.date: 01/17/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d19eabe10234ca2a1670ae04f99a45a85a6cac14
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138877"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Creare un'installazione offline di Visual Studio 2017

Il programma di installazione di Visual Studio 2017 è stato progettato per funzionare correttamente in computer e reti diversi, in condizioni di qualsiasi tipo.

- Il nuovo modello basato sul carico di lavoro consente di scaricare un minor numero di componenti rispetto alle precedenti versioni di Visual Studio: l'installazione più piccola richiede solo 300 MB.
- Anziché un file "ISO" o un file zip generico ora vengono scaricati solo i pacchetti necessari per il computer. Ad esempio i file a 64 bit vengono scaricati solo se sono necessari.
- Durante il processo di installazione, vengono provate tre diverse tecnologie di download (WebClient, BITS e WinInet) per ridurre al minimo le interferenze con software proxy e anti-virus;
- I file necessari per l'installazione di Visual Studio vengono distribuiti in una rete di distribuzione globale e possono quindi essere recuperati da un server locale.

È consigliabile provare il nuovo [programma di installazione Web di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)&mdash;, che garantisce risultati molto soddisfacenti.

 > [!div class="button"]
 > [Scarica Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

Se si vuole eseguire l'installazione offline perché la connessione Internet non è disponibile o non è affidabile, vedere [Installare Visual Studio 2017 in ambienti di rete con larghezza di banda ridotta o non affidabili](../install/install-vs-inconsistent-quality-network.md). È possibile usare la riga di comando per creare una cache locale dei file necessari per completare l'installazione offline. Questo processo sostituisce i file ISO disponibili per le versioni precedenti.

> [!NOTE]
> Gli amministratori dell'organizzazione che vogliono distribuire Visual Studio 2017 in una rete di workstation client protette da Internet tramite firewall possono vedere le pagine [Creare un'installazione di rete di Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) e [Installare i certificati necessari per l'installazione offline di Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]
